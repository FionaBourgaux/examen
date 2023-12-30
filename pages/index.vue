<script setup>
const query = gql`
query Pages {
  page(where: {slug: "accueil"}){
    id
    titre
    texte {
      html
    }
  }
  produits(orderBy: id_ASC, first: 3) {
    id
    nom
    
    slug
    photo {
      url
    }
  }
}

`;

const contenuAccueil = ref();
const { data } = await useAsyncQuery(query);
console.log(data.value);
contenuAccueil.value = data.value.page;

const produits = ref();

produits.value = data.value.produits;
</script>

<template>
  <div class="relative space-x-6 space-y-3">
  <NuxtImg
              class="h-[80vh] w-full object-cover"
        src="/images/vr.jpg"
        alt="banner"
      />
<h2 class="text-5xl text-white absolute top-12 pt-52
 font-titre"> 
    {{ contenuAccueil.titre }}
</h2>

<div class="absolute text-2xl text-white top-24 pt-52" v-html="contenuAccueil.texte.html"> </div>
</div>

<button
          class=" bottom-40 absolute bg-blue-500 hover:bg-blue-700 text-white font-bold py-3 px-12 rounded-full ml-16 text-xl"
        >
          Voir plus
        </button>

<TitresH1 class="text-black "> Découvrez l'Univers Captivant de Paws & Play VR</TitresH1>
<TextesParagraphe class="text-center m-10 text-xl"> 
Explorez notre collection soigneusement élaborée de casques, jouets connectés et accessoires qui ouvrent la porte à un tout nouveau monde d'interaction avec vos animaux de compagnie. Chaque produit est le fruit d'une passion partagée pour la technologie et l'amour inconditionnel envers nos amis à poils.
Plongez dans notre catalogue et découvrez comment Paws & Play VR transforme la façon dont vous interagissez avec vos animaux, offrant une dimension nouvelle et passionnante à chaque instant partagé.</TextesParagraphe>
<div v-if="produits" class=" grid sm:grid-cols-3 gap-8">
  <div v-for="produit in produits">
 <NuxtLink :to="`/produit/${produit.slug}`">
      <NuxtImg
        class=" hover:shadow-white hover:scale-125 shadow-xl shadow-black lg:w-2/3 mx-auto m-10 aspect-square "
        :src="produit.photo.url"
        :alt="produit.nom"
      />
 </NuxtLink>
    <div class="m-16 ">
      <h2 class="text-2xl text-center pb-10 font-sans text-black">{{ produit.nom }}</h2>
    </div>
  </div>
  </div>

  <div class="flex flex-row justify-center items-center">
 <button
          class=" bg-blue-500 hover:bg-blue-700 text-white font-bold py-3 px-8 rounded-full mb-10 text-xl"
        >
          Voir les produits
  </button>
  </div>
</template>
<script setup>
const query = gql`
query Pages {
  page(where: {slug: "accueil"}) {
    id
    titre
    texte {
      html
    }
  }
  produits {
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

<button
          class=" bottom-36 absolute bg-blue-500 hover:bg-blue-700 text-white font-bold py-4 px-6 rounded-full mt-6 "
        >
          Voir plus
        </button>
</div>

<TitresH1 class="text-black "> Découvrez l'Univers Captivant de Paws & Play VR</TitresH1>
<TextesParagraphe class="text-center m-10 text-2xl"> 
Explorez notre collection soigneusement élaborée de casques, jouets connectés et accessoires qui ouvrent la porte à un tout nouveau monde d'interaction avec vos animaux de compagnie. Chaque produit est le fruit d'une passion partagée pour la technologie et l'amour inconditionnel envers nos amis à poils.
Plongez dans notre catalogue et découvrez comment Paws & Play VR transforme la façon dont vous interagissez avec vos animaux, offrant une dimension nouvelle et passionnante à chaque instant partagé.</TextesParagraphe>
<div v-if="produits" class="p-10 grid sm:grid-cols-3 gap-8">
  <div v-for="produit in produits">
 <NuxtLink :to="`/produit/${produit.slug}`">
      <NuxtImg
        class="shadow-xl shadow-black lg:w-2/3 mx-auto m-10 aspect-square "
        :src="produit.photo.url"
        :alt="produit.nom"
      />
 </NuxtLink>
    <div class="m-10 ">
      <h2 class="text-3xl text-center pb-10 font-sans text-black">{{ produit.nom }}</h2>

      <div class="text-center items-center object-center text-black grid grid-cols-2">
      <div class="grid text-center p-5 items-center object-center ">
      
      </div>
      </div>
      
    </div>
    
  </div>
  </div>

   <button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-4 px-4 rounded-full mt-6"
        >
          Voir plus
        </button>
 
</template>
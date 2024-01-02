<script setup>
const query = gql`
  query produit($slug: String!) {
    produit(where: { slug: $slug }) {
      id
      nom
      slug
      description
      caracteristique {
        html
      }
      photo {
        url
      }
      prix
    }
  }
`;

const produit = ref();

const route = useRoute();
const { data } = await useAsyncQuery(query, {
  slug: route.params.slug,
});

console.log(data.value);
produit.value = data.value.produit;
</script>

<template>
<div v-if="produit" class="p-10 grid grid-cols-2">

  <div class="">
      <NuxtImg
        class="shadow-xl shadow-black lg:w-1/2 mx-auto m-10 aspect-square items-center"
        :src="produit.photo.url"
        :alt="produit.nom"
      />
    </div>

    <div class="m-10 text-black ">
      <h2 class="text-3xl font-sans">{{ produit.nom }}</h2>

      <div class="grid p-5 ">
      <h3 class="text-black text-2xl"><i class="ri-money-euro-circle-line"></i> {{ produit.prix }}</h3>
      </div>
      <TextesParagraphe class="m-2">{{ produit.description }}</TextesParagraphe>
      <TextesParagraphe class="" v-html="produit.caracteristique.html"> </TextesParagraphe>

      <div class="grid grid-cols-2 gap-16 mt-10">
  
      <div>
        <button
          class=" m-18 bg-blue-500 hover:bg-blue-700 text-white font-bold py-3 px-20 rounded-full mt-6"
        >
        Acheter
        </button>
      </div>

      <div>
        <a href="index">
          <button
          class=" m-18 bg-blue-500 hover:bg-blue-700 text-white font-bold py-3 px-20 rounded-full mt-6"
          >
        Retour
          </button>
        </a>
        </div>
        </div>
    </div>

  </div>
</template>

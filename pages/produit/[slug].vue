<script setup>
const query = gql`
  query produit($slug: String!) {
    produit(where: { slug: $slug }) {
      id
      nom
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

const produits = ref();

const route = useRoute();
const { data } = await useAsyncQuery(query, {
  slug: route.params.slug,
});

console.log(data.value);
produits.value = data.value.produit;
</script>

<template>
 <div v-if="produit" class="p-10 grid sm:grid-cols-2 gap-8">
  <div v-for="produit in produits">
 <div class="">
      <NuxtImg
        class="shadow-xl shadow-black lg:w-2/3 mx-auto m-10 aspect-square hover:scale-110 hover:transition"
        :src="produit.image.url"
        :alt="produit.nom"
      />
    </div>

    <div class="m-10 ">
      <h2 class="text-3xl text-center pb-10 font-sans">{{ produit.nom }}</h2>

      <div class="grid grid-cols-4 p-5 text-center items-center object-center ">
      <h3><i class="ri-heart-pulse-fill"></i> {{ produit.prix }}</h3>
      <img
        class="h-10 w-10 mt2"
        :src="produit.image.url"
        :alt="produit.nom"
      />
      </div>
      <p class="">{{ produit.description }}</p>
      <p class="">{{ produit.caracteristique}}</p>
    </div>
  </div>
  </div>
   
  <div v-else>
    <li>Loading...</li>
  </div>
</template>

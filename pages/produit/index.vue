<script setup>
const query = gql`
 query produit {
  produits {
    id
    nom
    prix
    slug
    photo {
      url
    }
  }
}
`
const produits = ref();

const route = useRoute();
const { data } = await useAsyncQuery(query);

console.log(data.value);
produits.value = data.value.produits;
</script>

<template>
 <div v-if="produits" class="p-10 grid sm:grid-cols-2 gap-8">
  <div v-for="produit in produits">
 <div class="">
      <NuxtImg
        class="shadow-xl shadow-black lg:w-2/3 mx-auto m-10 aspect-square hover:scale-110 hover:transition"
        :src="produit.photo.url"
        :alt="produit.nom"
      />
    </div>

    <div class="m-10 ">
      <h2 class="text-3xl text-center pb-10 font-sans">{{ produit.nom }}</h2>

      <div class="grid grid-cols-4 p-5 text-center items-center object-center ">
      <h3><i class="ri-money-euro-circle-line"></i> {{ produit.prix }}</h3>
      
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

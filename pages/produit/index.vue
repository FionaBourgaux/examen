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
 <NuxtLink :to="`/produit/${produit.slug}`">
      <NuxtImg
        class="shadow-xl shadow-black lg:w-1/3 mx-auto m-10 aspect-square hover:scale-110 hover:transition"
        :src="produit.photo.url"
        :alt="produit.nom"
      />
    </NuxtLink>

    <div class="m-10 ">
      <h2 class="text-3xl text-center pb-10 font-sans text-black">{{ produit.nom }}</h2>

      <div class="text-center items-center object-center text-black ">
      <h3 class="text-center text-xl"><i class="ri-money-euro-circle-line"></i> {{ produit.prix }}</h3>
      
      </div>
      <p class="text-black">{{ produit.description }}</p>
      <p class="text-black">{{ produit.caracteristique}}</p>
    </div>
  </div>
  </div>
   
  <div v-else>
    <li>Loading...</li>
  </div>
</template>

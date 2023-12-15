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
        class="shadow-xl shadow-black lg:w-1/2 mx-auto m-10 aspect-square hover:scale-110 hover:transition items-center"
        :src="produit.photo.url"
        :alt="produit.nom"
      />
    </div>

    <div class="m-10 items-center ">
      <h2 class="text-3xl text-center  font-sans">{{ produit.nom }}</h2>

      <div class="grid text-center p-5 items-center object-center ">
      <h3 class="text-black text-3xl"><i class="ri-money-euro-circle-line"></i> {{ produit.prix }}</h3>
      </div>
      <TextesParagraphe class="">{{ produit.description }}</TextesParagraphe>
      <TextesParagraphe class="" v-html="produit.caracteristique.html"> </TextesParagraphe>
    </div>
  </div>
  
   
  <div v-else>
    <li>Loading...</li>
  </div>
</template>

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
}

`;

const contenuAccueil = ref();
const { data } = await useAsyncQuery(query);
console.log(data.value);
contenuAccueil.value = data.value.page;
</script>

<template>
<h2> 
    {{ contenuAccueil.titre }}
</h2>

<div v-html="contenuAccueil.texte.html"> </div>

<ul
    v-if="produit"
    class="grid gap-8 grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 2xl:grid-cols-6 p-12"
  >
    <li v-for="produit in produits" :key="produit.id">
      <NuxtLink :to="`/produit/${produit.slug}`">
        <NuxtImg 
        class="shadow-2xl shadow-[#2D033B] hover:animate-bounce"
        :src="produit.image.url"
         :alt="produit.nom" />
        <h2 class="text-3xl text-center p-5 hover:scale-125">{{ produit.nom }}</h2>
      </NuxtLink>
    </li>
  </ul>
  <ul v-else>
    <li>Loading...</li>
  </ul>
</template>
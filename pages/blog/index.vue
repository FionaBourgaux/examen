<script setup>
const query = gql`
  query blogs {
    blogs {
      id
      titreBlog
      date
      resume
      imageBlog {
        url
      }
      slug
    }
  }
`;

const articles = ref();
const { data } = await useAsyncQuery(query);
console.log(data.value);
articles.value = data.value.blogs;
</script>

<template>
  <TitresH1> Bienvenue sur le Blog Paws & Play VR !</TitresH1>
  <TextesParagraphe class="text-center pl-10 pr-10 pb-10">
    Plongez dans l'univers fascinant de la réalité virtuelle pour animaux de
    compagnie avec notre blog. Ici, nous partageons des articles captivants, des
    astuces innovantes et des actualités passionnantes pour vous tenir informé
    des dernières tendances en matière de technologie et d'expériences
    interactives pour vos compagnons à quatre pattes.</TextesParagraphe
  >
  <div v-if="articles" class="p-10">
    <div v-for="article in articles">
      <NuxtLink
        :to="`/blog/${article.slug}`"
        class="flex items-top rounded overflow-hidden shadow-lg p-10"
      >
        <NuxtImg
          class="w-1/5 aspect-square"
          :src="article.imageBlog.url"
          :alt="article.nom"
        />

        <div class="p-10">
          <TitresH2 class="text-4xl pb-3">
            {{ article.titreBlog }}
          </TitresH2>

          <p class="text-black text-2xl">{{ article.date }}</p>

          <p class="text-black pt-2 text-xl font-light">{{ article.resume }}</p>

          <button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full mt-6 "
        >
          Voir l'article
        </button>
        </div>

        
      </NuxtLink>
      
      
    </div>
    
  </div>
</template>

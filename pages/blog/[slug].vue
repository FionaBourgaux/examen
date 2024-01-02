<script setup>
const query = gql`
  query blog($slug: String!) {
    blog(where: { slug: $slug }) {
      contenuBlog {
        html
      }
      id
      date
      titreBlog
      imageBlog {
        url
      }
    }
  }
`;

const article = ref();

const route = useRoute();
const { data } = await useAsyncQuery(query, {
  slug: route.params.slug,
});

console.log(data.value);
article.value = data.value.blog;
</script>

<template>
 <Head v-if="article">
    <Title>{{ article.titreBlog }} - Détails de l'article</Title>
    <Meta
      name="description"
      :content="`Découvrez des détails sur ${article.titreBlog}: ${article.contenuBlog}: ${article.date} `"
    />
    <Meta
      property="og:title"
      :content="`${article.titreBlog} - Détails du Pokémon`"
    />
    <Meta
      property="og:description"
      :content="`Découvrez des détails sur ${article.titreBlog}: ${article.contenuBlog}: ${article.date}`"
    />
    <Meta property="og:image" :content="article.imageBlog.url" />
    <Meta property="og:type" content="website" />
    <Meta property="og:locale" content="fr_FR" />
  </Head>
  <div v-if="article" class="p-10">
    <div class="">
      <NuxtImg
        class="aspect-square h-[50vh] w-full object-cover"
        :src="article.imageBlog.url"
        :alt="article.nom"
      />
    </div>

    <div class="m-10 items-center text-black">
      <h2 class="text-3xl text-center font-sans font-bold">
        {{ article.titreBlog }}
      </h2>

      <p class="text-black text-2xl text-center">{{ article.date }}</p>

      <div class="grid text-center p-5 items-center object-center"></div>
      <p
        class="text-black text-xl text-justify"
        v-html="article.contenuBlog.html"
      ></p>
    </div>
    
  </div>


</template>

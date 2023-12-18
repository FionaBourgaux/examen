<script setup>
const query = gql`
  query blog($slug: String!) {
    blog(where: { slug: $slug }) {
      contenuBlog {
        html
      }
      id
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
  <div v-if="article" class="p-10">
    <div class="">
      <NuxtImg
        class="aspect-square h-[50vh] w-full object-cover"
        :src="article.imageBlog.url"
        :alt="article.nom"
      />
    </div>

    <div class="m-10 items-center">
      <h2 class="text-3xl text-center font-sans">{{ article.TitreBlog }}</h2>

      <div class="grid text-center p-5 items-center object-center"></div>
      <p class="text-black" v-html="article.contenuBlog.html">
      </p>
    </div>
  </div>

  <div v-else>
    <li>Loading...</li>
  </div>
</template>

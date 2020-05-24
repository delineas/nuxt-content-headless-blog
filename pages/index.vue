<template>
  <div>
    <h1 class="text-3xl py-6">{{ index.title }}</h1>
    <p class="text-xl py-3">{{ index.description }}</p>
    <nuxt-content :document="index" class="leading-loose" />
    <ul class="list-disc list-inside mb-4">
      <li v-for="(post, index) in posts" :key="index">
        <nuxt-link :to="post.path" class="underline">{{ post.title }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    const index = await $content("index")
      .fetch()
      .catch(err => {
        error({ statusCode: 404, message: "index not found" });
      });

    const posts = await $content("posts")
      .only(["title", "path"])
      .limit(5)
      .sortBy('title')
      .where({
        published: true
      })
      .fetch()
      .catch(err => {
        error({ statusCode: 404, message: "Página no encontrada" });
      });

    return {
      index,
      posts
    };
  }
};
</script>

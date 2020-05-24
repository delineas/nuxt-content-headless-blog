<template>
  <div>
    <h1 class="text-3xl py-6">{{ page.title }}</h1>
    <p class="text-xl py-3">{{ page.description }}</p>
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
    const page = await $content("index")
      .fetch()
      .catch(err => {
        error({ statusCode: 404, message: "Page not found" });
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
      page,
      posts
    };
  }
};
</script>

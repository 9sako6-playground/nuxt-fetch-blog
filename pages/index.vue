<template>
  <div>
    <!-- <div class="container">{{ JSON.stringify(posts) }}</div> -->
    <h1>Blog posts</h1>
    <template v-if="$fetchState.pending">
      <content-placeholders>
        <content-placeholders-text :lines="20" />
      </content-placeholders>
    </template>
    <template v-else-if="$fetchState.error">
      <p>Error while fetching posts: {{ error }}</p>
    </template>
    <template v-else>
      <ul>
        <li v-for="post of posts" :key="post.id">
          <n-link :to="`/posts/${post.fields.slug}`">{{post.fields.title}}</n-link>
        </li>
      </ul>
    </template>
  </div>
</template>

<script>
export default {
  async fetch() {
    this.posts = await this.$http
      .$get(
        `https://cdn.contentful.com/spaces/${process.env.SPACE_ID}/environments/${process.env.ENVIRONMENT_ID}/entries?access_token=${process.env.ACCESS_TOKEN}&content_type=${process.env.CONTENT_TYPE}`
      )
      .then(res => res.items);
  },
  data() {
    return {
      posts: null
    };
  }
};
</script>

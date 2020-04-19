<template>
  <div>
    <h1>{{ slug }}</h1>
    <n-link to="/">back</n-link>
  </div>
</template>
<script>
export default {
  async asyncData({ params }) {
    return {
      slug: params.slug
    };
  }
};
</script>
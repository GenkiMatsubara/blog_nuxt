<template>
  <article>
    <h1>{{tech.title}}</h1>
    <dl>
      <dt>date</dt>
      <dd>{{tech.date}}</dd>
    </dl>
    <div><img :src="tech.image" /></div>
    <div v-for="tag in tech.tags" :key="tag">{{tag}}</div>
    
    <nuxt-content :document="tech" />
  </article>
</template>

<script lang="ts">
export default {
  async asyncData ({ $content, params }) {
    const tech = await $content('tech', params.slug || 'index').fetch()
    return { tech }
  }
}
</script>
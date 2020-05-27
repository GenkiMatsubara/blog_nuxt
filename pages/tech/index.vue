<template>
  <div>
    <div v-for="n in tech" :key="n.slug">
      <nuxt-link :to="'/tech/'+ n.slug">
        <div>{{n.date}} : {{n.title}}</div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>

export default {
  async asyncData ({ $content, params }) {
    const query = await $content('tech' || 'index').limit(15)
    const tech = await query.fetch()
    return { tech }
  }
}
</script>
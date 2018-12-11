<template>
  <section class="container">
    <div v-for="(v, index) in post.data" :key="index">
      <nuxt-link :to="v.link">
        <div class="eyecatch">
          <img :src="v.jetpack_featured_media_url" alt>
        </div>
        <div>{{ v.id }}</div>
        <div>{{ v.date }}</div>
        <div>{{ v.title.rendered }}</div>
      </nuxt-link>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import axios from 'axios'
export default {
  components: {
    Logo
  },

  data() {
    return {
      post: ''
    }
  },

  async mounted() {
    console.log(this)
    this.post = await axios.get(
      'http://nayucolony.xsrv.jp/wp-json/wp/v2/posts?_embed',
      {
        // headers: {
        //   'Access-Control-Arrow-Origin': '*'
        // }
      }
    )
  }
}
</script>

<style lang="scss" scoped>
.eyecatch {
  width: 100%;
  img {
    width: 100%;
    height: auto;
  }
}

.container {
  max-width: 700px;
  /* display: flex; */
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

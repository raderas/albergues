<template>
  <div class="container">
    <div>
      <logo />
      <h1 class="title">
        Albergues Manager
      </h1>
      <h2 class="subtitle">
        Albergues Manager
      </h2>
      <div class="links">
        <nuxt-link v-if="!token" to="/login" class="button-link">
          Login
        </nuxt-link>
        <nuxt-link v-if="token" to="/personas" class="button-link">
          Personas
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
import _ from 'lodash'
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  },
  data() {
    return {
      token: null
    }
  },
  mounted() {
    this.token = _.get(
      this.$axios,
      'defaults.headers.common.Authorization',
      null
    )
  }
}
</script>

<style lang="scss" scoped>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}

.button-link {
  @apply border p-4 bg-blue-500;
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

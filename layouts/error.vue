<template>
  <v-app dark>
    <h1>{{ errorDesc() }}</h1>
    <NuxtLink to="/"> Back to Home Page </NuxtLink>
  </v-app>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';

interface Error {
  statusCode: Number;
  description: String;
}

@Component
export default class ErrorLayout extends Vue {
  pageNotFound = 'Page Not Found :(';

  @Prop({
    type: Object,
    default: {
      statusCode: null,
      description: 'An Error Occured',
    },
    required: true,
  })
  readonly error!: Error;

  errorDesc() {
    return this.error.statusCode === 404
      ? this.pageNotFound
      : this.error.description;
  }
}
</script>

<style scoped>
h1 {
  font-size: 20px;
}
</style>

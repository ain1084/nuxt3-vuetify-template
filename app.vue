<template>
  <v-app>
    <div>
      <v-btn variant="outlined" prepend-icon="mdi-vuetify" @click="click"
        >Click</v-btn
      >
    </div>
    <TransitionGroup tag="div">
      <div v-for="(msg, i) in messages" :key="i">
        <v-icon icon="mdi-alert-circle" />
        {{ msg }}
      </div>
    </TransitionGroup>
  </v-app>
</template>
<script lang="ts" setup>
const versions = Object.entries(useNuxtApp().versions)
  .map((entity) => `${entity[0]}:${entity[1]}`)
  .join("/");
const messages = ref<string[]>([]);
const click = () => {
  messages.value.push(`This is Nuxt3(${versions}) + Vuetify application`);
};
</script>
<style lang="scss" scoped>
.v-enter-active {
  transition: all 1s ease-in-out;
}
.v-enter-from {
  opacity: 0;
  transform: translateX(100px);
}
</style>

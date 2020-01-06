<template>
  <v-app>
    <Chat />
  </v-app>
</template>

<script>
import Chat from './components/Chat.vue';

export default {
  name: 'app',
  components: {
    Chat
  }
}
</script>
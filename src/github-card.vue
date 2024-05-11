<template>
  <div v-if="user" class="m-5 card card-side bg-base-100 shadow-xl">
    <figure>
      <img src="https://avatars.githubusercontent.com/u/158302526?v=4" alt="Avatar" />
    </figure>
    <div class="card-body">
      <h2 class="card-title">{{ username }}</h2>
      <p>
        <strong>Seguidores:</strong> {{ user.followers }} <strong>Siguiendo:</strong>
        {{ user.following }}
      </p>
      <div class="card-actions justify-end">
        <a href="https://github.com/ErikMT24" class="btn btn-primary">Ver perfil</a>
      </div>
    </div>
  </div>
  <!-- <h1 class="text-3xl font-bold underline">Hola mundo</h1> -->
</template>
<script setup>
import { ref } from 'vue'
const user = ref(null)
const props = defineProps({
  username: {
    type: String,
    required: true
  }
})
// fetching data
fetch(`https://api.github.com/users/ErikMT24/${props.username}`)
  .then(async (res) => {
    user.value = await res.json()
  })
  .catch((err) => {
    console.log(err)
  })
</script>
<style scoped></style>

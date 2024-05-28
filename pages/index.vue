<script setup>
const state = reactive({
  imageUrl: null
});

const getImage = async () => {
  try {
    const res = await $fetch('/api/image', {
      method: 'POST',
      body: {
        content: 'Hello, World!',
      },
    });
    const imageUrl = URL.createObjectURL(res)
    state.imageUrl = imageUrl;
  } catch (error) {
    console.error(error)
  }
};
</script>

<template>
  <div>
    <button @click="getImage">Get Image</button>
    <div>
      <img v-if="state.imageUrl" :src="state.imageUrl" alt="image" />
    </div>
  </div>
</template>

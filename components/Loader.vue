<template>
    <transition name="fade">
      <div v-if="loading" class="loader">
        <div class="spinner"></div>
      </div>
    </transition>
  </template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue';
  
  const loading = ref(true);
  
  onMounted(() => {
    setTimeout(() => {
      loading.value = false;
    }, 5000);
  });
  
  onUnmounted(() => {
    loading.value = true;
  });
  </script>
  
  <style scoped>
  .loader {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: rgba(134, 134, 134, 0.8);
    transition: background-color 1s ease;
  }
  
  .spinner {
    width: fit-content;
    font-weight: bold;
    font-family: monospace;
    text-shadow:
      0 0 0 rgb(255 0 0),
      0 0 0 rgb(0 255 0),
      0 0 0 rgb(0 0 255);
    font-size: 700%;
    animation: l32 1s infinite cubic-bezier(0.5, -2000, 0.5, 2000);
  }
  
  .spinner:before {
    content: "YaelCoder";
  }
  
  @keyframes l32 {
    25%, 100% {
      text-shadow:
        0.03px -0.01px 0.01px rgb(255 0 0),
        0.02px 0.02px 0 rgb(0 255 0),
        -0.02px 0.02px 0 rgb(0 0 255);
    }
  }
  
  @keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }
  
  .fade-enter-active, .fade-leave-active {
    transition: opacity 1s ease;
  }
  
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
  </style>  
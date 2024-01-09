<template>
    <button class="btn btn-primary"  @click="status = !status">
        Toggle status
    </button>

    <transition 
        mode="out-in"
        name="custom"
        enter-active-class="dog"
        leave-active-class="cat"
    >
        <div class="p-3 mb-2 bg-danger text-white"
            v-if="!status"
            key="status_off"    
        >
            OFF
        </div>
        <div class="p-3 mb-2 bg-success text-white"
            v-else="status"
            key="status_on"    
        >
            ON
        </div>
    </transition>
   
</template>

<script setup>
   import { ref } from 'vue';
   const status = ref(false);
</script>


<style scoped>

    .custom-enter-from,
    .custom-leave-to {
        opacity: 0;
    }

    .dog,
    .cat {
        transition: 1s;
    }

    .custom-enter-to,
    .custom-leave-from {
        opacity: 1;
    }

</style>
<template>
 <div>
    <h1>
        {{ title }}
    </h1>
 </div>
</template>

<script>
import { ref, computed } from "vue";
export default {
data() {

  return {
        day: computed(() => today.getDate()),
        month: computed(() => today.getMonth() + 1), // JavaScript months are zero-based
        year: computed(() => today.getFullYear())
        };
}
}
</script>

<style>

</style>
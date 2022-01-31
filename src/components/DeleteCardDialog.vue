<template>
  <main class="delete-card">
            <div v-if="deletecard" class="delete-card-box">
                <p>Do you really want to delete this card?</p>
                <button @click="$emit('deleteThisCard')">Yes</button><button @click="$emit('keepCard')">No</button>
            </div>
        <button @click="$emit('remove-box')">Delete this card</button>
  </main>
</template>

<script>
export default {
    props: ['activecard', 'deletecard']
}
</script>

<style scoped>
    
</style>
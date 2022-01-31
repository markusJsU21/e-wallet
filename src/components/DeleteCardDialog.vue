<template>
  <main class="delete-card">
            <div v-if="deletecard" class="delete-card-box">
                <p>Do you really want to delete this card belonging to '{{activecard.cardHolderName}}'?</p> 
            
                <p class="warning">Destroying other people's bankcards is a criminal offense... <br>
                    ...wait why do you even have this?</p>
                <div class="yes-or-no-box">
                <button @click="$emit('deleteThisCard')">Yes</button><button @click="$emit('keepCard')">No</button>
                </div>
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
    .delete-card-box{
        background-color: rgb(241, 241, 241);
        border-radius: 10px;
        z-index: 3;
        padding:1rem;
        
    }
    button{
        width: 45%;
    }
    p{
        font-weight: bold;
        /* font-family: 'Source Sans Pro', sans-serif; */
    }
    .yes-or-no-box{
        display:flex;
        justify-content: space-evenly;
    }
    .warning{
        font-size: .6rem;
        font-family: 'PT Mono', sans-serif;
        font-style: italic;
        margin: 1rem auto 1rem auto;
        line-height: 1rem;
        font-weight: normal;
        
    }
</style>
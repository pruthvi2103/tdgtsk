<template>
    <div>
        <v-card 
        v-if="loading">
        <v-skeleton-loader
            
            height="94"
            type="list-item-avatar-three-line"
          >
          </v-skeleton-loader>
          </v-card>

      
    </div>
</template>

<script>
    export default {
         data: () => ({
        loading: true,
         })
    }
</script>

<style lang="scss" scoped>

</style>
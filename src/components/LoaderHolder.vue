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

             <v-card
            v-else
          >
            <v-card-title>Title</v-card-title>
            <v-card-text>Card Text</v-card-text>
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
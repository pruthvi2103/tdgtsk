<template>
  <div class="text-xs-center" style="padding-top:5px">
        
        <v-card>
            <v-card-text>
              <v-pagination
                
                :length="10"
                @input="next"
              >
              </v-pagination>
            </v-card-text>
          </v-card>
     
      
    
  </div>
</template>

<script>
  export default {
      props: ['pages'],
    data () {
      return {
        page: 1
      }
    },
    methods:{
        next (event) {
            console.log(event);
            this.$emit('newpage',event);
    }
  }
  }
</script>
<style lang="scss" scoped>

</style>
<template>
  <div>
      <v-row>
      <v-col
          v-for="(post, i) in posts.slice(this.start,this.limit+this.start)"
          :key="i"
          cols="12"
          >
    <v-lazy>
        <v-card
            
          >
                 <v-avatar color="indigo" size="36">
      <span class="white--text headline">{{ post.userId }}</span>
    </v-avatar>
            <div class="d-flex flex-no-wrap justify-space-between">
              <div>
                  
                  
                <v-card-title
                  class="headline"
                  v-text="post.title"
                >

         
                
                </v-card-title>

                <v-card-subtitle v-text="post.body"></v-card-subtitle>
              </div>
            </div>
          </v-card>
          </v-lazy>

        
      </v-col>
      <v-col
      rows= "12"
      v-if="this.limit+this.start<this.page*10">
      <LoaderHolder
      v-intersect= "appendPosts"></LoaderHolder>
      
      </v-col>
      
        </v-row>
        <Paginator 
        :pages="pages" 
        @newpage="onNewPage" ></Paginator>
        
  </div>
</template>

<script>
import LoaderHolder from './LoaderHolder';
import Paginator from './Paginator';
    export default {
        name: 'PostBody',
        props: ['posts'],
        components:{ LoaderHolder, Paginator },
        data: () => ({
            isActive: false,
            postdisp: [],
            start:0,
            limit:5,
            page:1,
            pages:10
      
    }),
    methods:{
        appendPosts(){
            this.limit = this.limit+5
            console.log(this.posts.length)
            //console.log(this.postdisp);
        },
        onNewPage(pg){
         setTimeout(() => {this.page=pg;this.start = (pg-1)*10;}, 1500);
            
            


        },


    },
    created(){
        this.isActive= true;
    },
    mounted(){
        this.isActive= true;
    }
        
    }
</script>

<style lang="scss" scoped>
body {
    font-family: 'Roboto', sans-serif;
}

.col{
  padding-bottom: 0;
  padding-top:5px ;
}
</style>
<template>
  <div>
      <v-row
      color="primary"
      style="border-left-style:solid;border-right-style:solid;border-left-color:#eee;
      border-right-color:#eee">
      <v-col
          v-for="(post, i) in posts.slice(this.start,this.limit+this.start)"
          :key="i"
          cols="12"
          style="padding-bottom:10px">
          
    <v-lazy>
      
        <v-card
          color="anchor"  
          >
          
                 <v-avatar color="indigo" size="36">
      <span class="white--text headline">{{ post.userId }}</span>
    </v-avatar>
            <div class="d-flex flex-no-wrap justify-space-between">
              <div>
                  
                  
                <v-card-title
                  class="title"
                  v-text="post.title"
                  style="padding-bottom:12px"
                >
              </v-card-title>

                <v-divider></v-divider>

                <v-card-subtitle v-text="post.body"></v-card-subtitle>
              <v-card-actions>
                <v-icon style="padding-left:2%">mdi-heart-outline</v-icon>
                <v-icon style="padding-left:4%">mdi-github-circle</v-icon>
                <v-spacer></v-spacer>
                <v-icon >mdi-share</v-icon>
                
              </v-card-actions>
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
            setTimeout(() => {console.log(this.limit);}, 1500);
            this.limit = this.limit+5;
            //console.log(this.posts.length)
            //console.log(this.postdisp);
        },
        onNewPage(pg){
         this.page=pg;
         this.start = (pg-1)*10;
            
            


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
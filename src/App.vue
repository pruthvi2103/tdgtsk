<template>
  <v-app id="sandbox">
    <v-navigation-drawer
      v-model="primaryDrawer.model"
      :clipped="primaryDrawer.clipped"
      :floating="primaryDrawer.floating"
      :mini-variant="primaryDrawer.mini"
      :permanent="primaryDrawer.type === 'permanent'"
      :temporary="primaryDrawer.type === 'temporary'"
      app
      overflow
      expand-on-hover
      
    >
      <v-list-item class="px-2">
        <v-list-item-avatar>
          <v-icon
          >mdi-account-box</v-icon>
        </v-list-item-avatar>

        <v-list-item-title>John Doe</v-list-item-title>

        <v-btn
          icon
          @click.stop="primaryDrawer.model = !primaryDrawer.model"
        >
          <v-icon>mdi-chevron-left</v-icon>
        </v-btn>
      </v-list-item>
<v-divider></v-divider>
          <v-list-item
            link
          >
          <v-list-item-icon>
              <v-icon>
                mdi-home
              </v-icon>

                  
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>Home</v-list-item-title>
            </v-list-item-content>
          </v-list-item>

          <v-list-item
            link
          >
          <v-list-item-icon>
              <v-icon>
               mdi-weather-night
              </v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>Mode</v-list-item-title>
            </v-list-item-content>
            <v-switch
                      v-model="$vuetify.theme.dark"
                      primary
                      label="Dark"
                    />
          </v-list-item>

      
    </v-navigation-drawer>

    <v-app-bar
      :clipped-left="primaryDrawer.clipped"
      app
    >
      <v-app-bar-nav-icon
        v-if="primaryDrawer.type !== 'permanent'"
        @click.stop="primaryDrawer.model = !primaryDrawer.model"
      />
      <v-toolbar-title>TDG-Partner</v-toolbar-title>
      <v-divider
      class="mx-12 hidden-sm-and-down"
      style="padding-left:30px"
      vertical
    ></v-divider>
    <span class="hidden-sm-and-down">
      Home</span>
       <v-spacer></v-spacer>
  <v-toolbar-items class="hidden-sm-and-down">
    <v-divider vertical></v-divider>
      <v-btn text>
        Sign-In
      </v-btn>

      <v-divider vertical></v-divider>

      <v-btn text>
        Sign-Up
      </v-btn>

      

</v-toolbar-items>
    </v-app-bar>

    <v-content>
      <v-container fluid>
        <v-row
          align="center"
          justify="center"
        >
          <v-col md="8"
          sm="10">
          <v-divider vertical></v-divider>
            <PostBody :posts="posts"></PostBody>
          </v-col>
        </v-row>
      </v-container>
    </v-content>

    <v-footer
      :inset="footer.inset"
      absolute
      app
    >
      <span class="px-4">Pruthvi Shetty</span>
    </v-footer>
  </v-app>
</template>

<script>
import PostBody from './components/PostBody';
import axios from 'axios'
  export default {
    data: () => ({
      drawers: ['Default (no property)', 'Permanent', 'Temporary'],
      primaryDrawer: {
        model: null,
        type: 'default (no property)',
        clipped: true,
        floating: true,
        mini: false,
      },
      footer: {
        inset: false,
      },
      posts:[]
    }),
    components:{
      PostBody
    },
    created(){
      axios.get('https://jsonplaceholder.typicode.com/posts').then(response=>{
        this.posts = response.data
      })
      .catch(e =>{
        this.errors.push(e)
      })
    }
  }
</script>

<style lang="scss">


</style>
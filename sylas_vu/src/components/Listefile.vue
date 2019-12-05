<template>
<v-container>
    <div>
        <button class="favorite styled"
            type="button" @click = "liste" > 
            Ma Liste
        </button>
        <br>
        <br>
        <v-card
            max-width="600"
            class="mx-auto"
        >
            <v-toolbar
            color="light-blue"
            dark
            >
            
            </v-toolbar>

            <v-list two-line subheader align="center">
            <v-subheader inset>Folders</v-subheader>

            <v-list-item
                v-for="(Objects,i) in listObjects"
                :key="i"
                click=""
            >
            
            <div class="my-2">
                <v-btn text small  @click="deletePost(Objects.Key)" >Delete</v-btn>
            </div>
            <div class="my-2">
                <v-btn text small  @click="downPost(Objects.Key)" >Down</v-btn>
            </div>
            <button type="button" >
            {{Objects.Key}}</button>

                <v-list-item-content>
                <v-list-item-title v-text="listObjects.Key"></v-list-item-title>
                <!--<v-list-item-subtitle v-text="item.subtitle"></v-list-item-subtitle>-->
            </v-list-item-content>

                <v-list-item-action>
                <v-btn icon>
                    <v-icon color="grey lighten-1">mdi-information</v-icon>
                </v-btn>
                </v-list-item-action>
            </v-list-item>


                <v-list-item-action>
                <v-btn icon>
                    <v-icon color="grey lighten-1">mdi-information</v-icon>
                </v-btn>
                </v-list-item-action>
            <!-- </v-list-item>-->
            </v-list>
        </v-card>

    </div>
    </v-container>
</template>

<script>
        export default {
            data () {
                return {
                    listObjects: null,
                    downObjects: null
                }
            },
            methods:{
            liste(){ 
                  fetch(' https://91qeit0dj9.execute-api.eu-central-1.amazonaws.com/beta/liste')
                    .then(res => res.json())
                    .then(json => {
                       // console.log(json);
                        console.log(json.Contents)
                        this.listObjects = json.Contents
                    })  
                    
                },

                deletePost(key){
                    console.log(key);
                    fetch('https://91qeit0dj9.execute-api.eu-central-1.amazonaws.com/beta/delete?Bucket=sylas&Key='+key) 
                        // { method: 'GET', 
                         //body: JSON.stringify({
                        //     "bucket":"sylas",
                        //     "Key": key
                        //     //"content" : evt.target.result
                        //     }) }) // expecting a json response
                            .then(json => console.log(json));
                 },

                downPost(key){
                    console.log(key);
                    fetch('https://91qeit0dj9.execute-api.eu-central-1.amazonaws.com/beta/down?bucket=sylas&key='+key) 
                        .then(res => res.json())
                    .then(json => {
                       // console.log(json);
                        console.log(json.Contents)
                        this.downObjects = json.Contents
                        
                    })
                 }
            
        }
            
        
  }

</script>

<style scoped>
#tout {
  font-size: 2em;
  text-align: center;
}
</style> 
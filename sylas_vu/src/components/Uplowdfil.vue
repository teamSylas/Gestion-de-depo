<template>
    <div>
        <input type ="file" @change = "change" >
    
    </div>
</template>

<script>
export default {
  data(){
      return {
          file : null
      }
  },

  methods:{
      change(e){
          console.log(e.target.files.item(0));
          var filename = e.target.files.item(0).name;
          var file = e.target.files.item(0);
          console.log(filename);
            if (file) {
                var reader = new FileReader();
                reader.readAsDataURL(file);
                reader.onload = function (evt) {

                   console.log(evt.target.result);
                    fetch(' https://91qeit0dj9.execute-api.eu-central-1.amazonaws.com/beta/sylas', 
                        { method: 'POST', 
                        body: JSON.stringify({
                            "bucket":"sylas",
                            "fileName": "/tmp/"+filename,
                            "content" : evt.target.result
                            }) }) // expecting a json response
                            .then(json => console.log(json));
                }
                reader.onerror = function (evt) {
                    document.getElementById("fileContents").innerHTML = "error reading file"+ evt;
                }
            } 
      },

  }
  }
</script>
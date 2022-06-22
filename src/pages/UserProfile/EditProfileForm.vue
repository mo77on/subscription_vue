<template>
  <form>
    <md-card>
      <md-card-header :data-background-color="dataBackgroundColor">
        <h4 class="title">Add Post</h4>
        <p class="category"></p>
      </md-card-header>
      <md-card-content>
       <form method="post" @submit.prevent="addNewPost()">
        <div class="md-layout">
          <div class="md-layout-item md-small-size-100 md-size-100">
            <md-field>
              <label>Title</label>
              <md-input v-model="title" name="title" type="text"></md-input>
            </md-field>
          </div>
          <div class="md-layout-item md-size-100">
            <md-field maxlength="5">
              <label>Description</label>
              <md-textarea v-model="description" name="description"></md-textarea>
            </md-field>
          </div>
          <div class="md-layout-item md-size-100 text-right">
            <md-button class="md-raised md-success" value="Submit" type="submit" >Add Post</md-button>
          </div>
        </div>
        </form>
      </md-card-content>
    </md-card>
  </form>
</template>

<script>
import axios from 'axios'
    export default {
        
        data(){
            return {
              title: '',
              description: ''
            }
        },
        methods: {
            addNewPost(){
            
                axios.post('http://localhost:8000/api/post',{title:this.title, description:this.description})
                .then((response)=>{
                alert('Successfully Added Post!')
                this.$router.push('/dashboard');
                })
            }
        }
    }
</script>
<style></style>

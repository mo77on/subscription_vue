<template>
  <div class="content">
    <div class="md-layout">
      <div class="md-layout-item">
        <md-card>
          <md-card-header data-background-color="green">
            <h4 class="title">Subscription</h4>
            <p class="category"></p>
          </md-card-header>
          <md-card-content>
            <div id="typography">
              <div class="title">
                <h2>Subscribe</h2>
              </div>
              <form method="post" @submit.prevent="addNewSubscription()">
              <div class="md-layout">
                <div class="md-layout-item md-small-size-100 md-size-100">
                  <md-field>
                    <label>Email</label>
                    <md-input v-model="email" name="email" type="email"></md-input>
                  </md-field>
                </div>
                <div class="md-layout-item md-size-100 text-right">
                  <md-button class="md-raised md-success" value="Submit" type="submit" >Subscribe</md-button>
                </div>
              </div>
              </form>
            </div>
          </md-card-content>
        </md-card>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  props: {
    dataBackgroundColor: {
      type: String,
      default: "",
    },
  },

      data(){
            return {
              email: ''
            }
        },
        methods: {
            addNewSubscription(){
                axios.post('http://localhost:8000/api/subscribe',{email:this.email})
                .then((response)=>{
                alert('Successfully Subscribed!')
                this.$router.push('/dashboard');
                })
            }
        }
};

</script>

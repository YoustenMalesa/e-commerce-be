<template>
  <div class="text-center">
    <div class="spinner-border" role="status">
      <span class="sr-only">Loading...</span>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "SuccessView",
  props:["baseUrl"],
  data() {
    return {
      token: null,
      sessionId:null
    }
  },
  methods:{
    saveOrder() {
      window.location.href = '/order';
      axios.post(`${this.baseUrl}/order/add?token=${this.token}&sessionId=${this.sessionId}`)
          .then(()=>{
            window.location.href = '/order';
          }).catch((error)=>{
        console.log(error);
      })
    }
  },
  mounted(){
    this.token = localStorage.getItem("token");
    this.sessionId = localStorage.getItem("sessionId");
    this.saveOrder()
  }
}
</script>

<style scoped>

</style>
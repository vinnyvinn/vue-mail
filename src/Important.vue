<template>
<div class="inbox-body">
  <app-messages :messages="importantMessages"></app-messages>
</div>
</template>

<script>
    import Messages from "./Messages";

    export default {
  props:{
      data:{
          type:Object,
          required:true
      }
  },
        computed:{
            importantMessages(){
                return  this.data.messages.filter(message =>{
                    return (message.type == 'incoming' && message.isImportant === true && !message.isDeleted);
                })
            },
        },
        components:{
      'app-messages':Messages
        }
    }
</script>

<style scoped>

</style>

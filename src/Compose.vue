<template>
    <div>
      <a href="#composeModal" data-toggle="modal" class="btn btn-compose">Compose</a>
      <div aria-hidden="true" role="dialog" tabindex="-1" id="composeModal" class="modal fade" style="display: none">
<div class="modal-dialog">
  <div class="modal-content">
<div class="modal-header">
<button aria-hidden="true" data-dismiss="modal" class="close" type="button">&times;</button>
  <h4 class="modal-title">New Message</h4>
</div>

    <div class="modal-body">
      <form role="form" class="form-horizontal" @submit.prevent="sendMessage">
   <div class="form-group">
     <label for="subject">Subject</label>
     <input type="text" class="form-control" id="subject" v-model="message.subject">
   </div>
        <div class="form-group">
          <label for="message">Message</label>
          <textarea name="message" id="message" cols="30" rows="10" class="form-control" v-model="message.content"></textarea>
        </div>
<div class="form-group">
<button type="submit" class="btn btn-send">Send</button>
</div>
      </form>
    </div>
  </div>
</div>
      </div>
    </div>
</template>

<script>
  import { eventBus} from "./main";
  import moment from 'moment';

  export default {
        data(){
        return{
            message:{
                subject:'',
                content:''
            }
        }
        },
      methods:{
sendMessage(){
    eventBus.$emit('sentMessage',{
        message:{
         subject:this.message.subject,
          content: this.message.content,
isDeleted: false,
type:'outgoing',
date: moment(),
from:{
name:'Vinnie Vinn',
    email:'Vinn@test.com'
},
attachments:[]
        }
    })
}
      }
    }
</script>

<style scoped>

</style>

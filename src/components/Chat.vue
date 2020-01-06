<template>
    <v-card :style="heightObj" width="60%" class="mt-5 mx-auto">
      <v-toolbar color="indigo" dark v-if="nameReceived"> 
        <v-toolbar-title v-model="usrName">{{usrName}}</v-toolbar-title>
      </v-toolbar>
      <v-card-title v-if="!nameReceived">
        <span class="my-6 mx-auto headline font-weight-bold"> Добро пожаловать в уютный чат! А как Вас звать? </span>
      </v-card-title>
      <v-card-subtitle v-if="!nameReceived">
        <v-text-field outlined placeholder="Ник: например, kus" v-model="usrName" @keyup.enter="logIn"/>
      </v-card-subtitle>
      <v-card-text> 
        <v-list v-if="nameReceived" three-line style="height:70vh; overflow-y:auto;" v-chat-scroll>
          <template v-for="flooder in flood">
            <v-list-item :key="flooder.created.substr(20,8)">
              <v-list-item-content>
                <v-list-item-title><b>{{flooder.name ? flooder.created.substr(11,8) : flooder.text}}</b> <span class="text--primary">{{flooder.name ? "от " + flooder.name + " :" : ""}}</span></v-list-item-title>
                <v-list-item-subtitle>{{flooder.name ? flooder.text : ""}}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </template>
        </v-list>
      </v-card-text>
      <v-footer absolute v-if="nameReceived">
        <v-form @submit.prevent="sendMessage" class="grow">
          <v-text-field placeholder="Сообщение писать сюды :)" v-model="message"/>
        </v-form>
      </v-footer>
    </v-card>
</template>

<script>
import Vue from 'vue'
import VueNativeSock from 'vue-native-websocket'
import VueChatScroll from 'vue-chat-scroll'

Vue.use(VueChatScroll)
Vue.use(VueNativeSock, 'ws://pm.tada.team/ws?name=USERNAME', {
    connectManually: true
});

export default {
  name: 'chat',
  data(){
    return{
      nameReceived:false,
      usrName:"",
      message:"",
      flood:[]
    }
  },
  methods:{
    logIn(){
      this.$connect('ws://pm.tada.team/ws?name=' + this.usrName, { format: 'json' });
      this.nameReceived = !this.nameReceived;
    },
    sendMessage() {
      this.$socket.sendObj({"text":this.message});
      this.message = "";
    }
  },
  created(){
    this.$options.sockets.onmessage = (data) => this.flood.push(JSON.parse(data.data));
  },
  computed:{
    heightObj(){
      return{
        height: this.nameReceived ? "94vh" : ""
      }
    }
  }
}
</script>
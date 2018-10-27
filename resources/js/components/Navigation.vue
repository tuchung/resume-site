<template>
  <div>
    <sui-menu class="content-menu" pointing>

        <router-link
        is="sui-menu-item"
        v-for="item in routeItems"
        :active="isActive(item.name)"
        :key="item.name"
        :content="item.name"
        v-on:click.native="select(item.name)"
        :to="item.href"
        ></router-link>

        <a is="sui-menu-item"
        :key="contact.name"
        :content="contact.name"
        @click="toggle"
        />
    </sui-menu>


    <!-- modal -->
    <sui-modal class='contact-modal' size="mini" v-model="open">
        <sui-message
        v-show="success"
        header="Success"
        content="{{successMessage}}"
        />
        <sui-message
        v-show="error"
        header="Fail"
        content="{{successMessage}}"
        />
      <sui-modal-header class="contact-header">
          Contact Via
        <v-icon class="close-icon" v-on:click.native="toggle()" name="times-circle" scale="2"/>
      </sui-modal-header>
      <sui-modal-content>
        <sui-modal-description>
          <sui-header>By Phone:</sui-header>
          <div>
              <v-icon name="mobile-alt"/>&nbsp;&nbsp;(770) 402-6324
          </div>
          <sui-header>By Email:</sui-header>
          <div>
              <v-icon name="envelope"/>&nbsp;&nbsp;tuthienchung@gmail.com
          </div>
          <sui-header>Or Send Me A Message Directly Here:</sui-header>
          <div>
              <div class="ui form">
                <div class="field">
                    <sui-label>
                        Subject
                    </sui-label>
                    <sui-input v-model="subject" placeholder="Default: No Subject" />
                </div>
                <div class="field">
                    <sui-label>
                        Body
                    </sui-label>
                    <textarea v-model="content"></textarea>
                </div>
              </div>
          </div>

        </sui-modal-description>
      </sui-modal-content>
      <sui-modal-actions>
        <sui-button positive @click.native="sendEmail()">
          Send
        </sui-button>
      </sui-modal-actions>
    </sui-modal>

  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Navigation',
  data() {
    return {
      active: 'Resume',
      open: false,
      content: '',
      subject: '',
      success: false,
      error: false,
      successMessage: '',
      errorMessage: '',
      routeItems:
          [
              {
                name: "Resume",
                href: "/"
              },
              {
                name: "About",
                href: "/about"
              }
          ]
      ,
      contact:{
          name: "Contact Me"
      },
    };
  },
  methods: {
    isActive(name) {
      return this.active === name;
    },
    toggle() {
      this.open = !this.open;
    },
    select(name) {
        this.active = name;
    },
    setRoute(){
        var i;
        for(i=0;i < this.routeItems.length;i++){
            if(this.routeItems[i].href === this.$route.path){
                this.active = this.routeItems[i].name;
                return;
            }
        }
    },
    sendEmail(){
        axios.post('/mail/send',
         {
             subject: this.subject,
             content: this.content
         }
        )
        .then(function(response) {
            console.log(response);
        }).catch(function (error) {
            console.log(error);
        });

    }
  },
  mounted(){
     this.setRoute();
  },
  watch: {
    '$route': function(from, to) {
      this.setRoute();
    }
  }
};

</script>

<style>
    .content-menu.ui.menu{
        margin: 10px;
    }

    .contact-modal .ui.modal{
        top: 5%;
        left: 30%;
        width: 40%;
        height: 90%;
        overflow: auto;
    }

    .contact-modal .header.contact-header{
        background-color: #3cade0;
    }

    .close-icon{
        float: right;
        cursor: pointer;
    }


</style>


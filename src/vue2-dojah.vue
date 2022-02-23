<template>
    <div @click="initDojah">
      <slot></slot>
    </div>
</template>

<script>
export default {
  
 props:{
   AppId:String,
   PKey: String,
   type: String
 },
 methods:{
    initDojah() {
      console.log('Console works')
      window.connect.setup();
      window.connect.open();
    },
   
 },
 created() {
    window.newConsole = Object.assign({}, window.console);
    window.console = Object.assign({}, window.newConsole);
  },
  mounted() {
     window.newConsole = Object.assign({}, window.console);
    let externalScript = document.createElement("script");
    externalScript.setAttribute("src", "https://widget.dojah.io/widget.js");
    document.body.appendChild(externalScript);
    externalScript.onload = () => {
      const options = {
        app_id: this.AppId,
        p_key: this.PKey,
        type: this.type, // 'payment', 'identification', 'verification', 'liveness'
        onSuccess: (response) => {
          this.$emit('onSuccess',response)
        },
       onError: (err) => {
          this.$emit("onError", err);
        },
        onClose: () => {
          this.$emit("onClose");
        },
      };
      window.connect = new window.Connect(options);
      window.console = Object.assign({}, window.newConsole);
    };
  },
};
</script>
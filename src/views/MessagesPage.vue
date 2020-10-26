<template>
  <v-container class="mx-auto mt-5">
    <h1>Mert</h1>
    <input type="submit" value="Submit" @click="selectUser('adminmert')">
    <h1>Eren</h1><input type="button" value="Submit" @click="newMessage({message: 'Dune', sentBy: 'cagdasay'}) ">
  </v-container>
</template>

<script>
export default {
  data: () => {
    return {
      username: 'cagdasay',
      users: ['cagdasay'],
      message: "",
      messages: []
    }
  },
  sockets: {
    oldMessages(data) {
      this.messages = data;
      console.log(this.messages);
    }
  },
  methods: {
    selectUser (name) {
      this.username = name;
      console.log(this.username);
      this.users.push(this.username);
      console.log(this.users);

      this.$socket.emit('initialize', this.users);
    },
    newMessage (data) {
      this.message = data.message;
      this.sentBy = data.sentBy;
      this.messages.push(this.messages);
      this.$socket.emit('new message', data);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

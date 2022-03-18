<template>
  <div class="hello">
    <div class="jumbotron">
      <div class="d-flex justify-content-center">
       <form @submit.prevent>
        <div class="form-group">
          <label for="text">Text</label>
          <input type="text" class="form-control" id="text" v-model="text">
        </div>
        <div class="form-group">
          <label for="exampleInputPassword1">Password</label>
          <input type="password" class="form-control" id="exampleInputPassword1" v-model="password">
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Text field</label>
          <textarea class="form-control" id="exampleFormControlTextarea1" rows="3"  v-model="textarea"></textarea>
        </div>
        <button type="submit" class="btn btn-secondary" @click="submit">Submit</button>

        <div class="alert alert-success mt-4" role="alert" v-if="success">
          Success!
        </div>

        <div class="alert alert-danger mt-4" role="alert" v-if="error">
          Error!
        </div>

      </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      text: '',
      password: '',
      textarea: '',
      error: false,
      success: true
    }
  },
  props: {
    msg: String
  },
  methods: {
    submit() {
      this.axios.post('https://testoweee.free.beeceptor.com', {
          text: this.text,
          password: this.password,
          textarea: this.textarea,
        })
        .then(function (response) {
          this.success = true;
          console.log(response);
        })
        .catch(function (error) {
          this.error = true;
          console.log(error);
        });
    }
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

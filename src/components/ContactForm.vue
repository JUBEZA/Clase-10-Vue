<template>
  <div>

    <div v-if="sent">
      Gracias Loco
    </div>
    <form @submit.prevent="formSubmitHandler" v-else>
      <div>
        <label for="name">Nombre</label>
        <input type="text" id="name" v-model="form.name" name="name">
      </div>
      <div>
        <label for="email">Email</label>
        <input type="email" id="email" v-model="form.email" email="email">
      </div>
      <div>
        <label for="message">Mensaje</label>
        <textarea id="message" cols="30" rows="10" v-model="form.message" name="message"></textarea>
      </div>
      <button>Enviar</button>
    </form>
  </div>
</template>

<script>
  export default{
    name: 'ContactForm',
    data() {
      return {
        sent: false,
        form: {
          email: "",
          name: "",
          message: "",
        },
      };
    },
    methods: {
      formSubmitHandler() {
        fetch("https://649df2bc9bac4a8e669e7987.mockapi.io/contact-form/", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify(this.form),
        })
          .then((res) => res.json())
          .then(() => {
            this.sent = true
          });
      },
    },

  };

</script>

<template>
    <form @submit.prevent="formSubmitHandler">
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
      <button>Editar</button>
    </form>
</template>

<script>
export default {

  name: "EditContactForm",
  data() {
    return {
      form: {
        name: "",
        email: "",
        message: ""
      }
    }
  },
  props: {
    id: {
      type: Number,
      required: true
    }
  },
  created(){
    this.getContactForm();
  },
  updated() {
    this.getContactForm();
  },
  method: {
    getContactForm() {
      fetch(`https://649df2bc9bac4a8e669e7987.mockapi.io/contact-form/${this.id}`
      )
      .then((res) => res.json())
      .then((form) => this.form = form);

    },
    formSubmitHandler() {
      fetch(
        `https://649df2bc9bac4a8e669e7987.mockapi.io/contact-form/${this.id}`,
        {
          method: "PUT",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify(this.form)
        }
      ).then(() => alert("editado!"));

    },
  },
};
</script>

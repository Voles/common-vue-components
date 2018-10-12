<template>
  <form>
    <label for="postal">Postcode</label>
    <input type="text" placeholder="1000 AB" id="postal" v-model="postal" v-on:input="validateInput" />

    <label for="number">Huisnummer</label>
    <input type="number" placeholder="1" id="number" v-model="number" v-on:input="validateInput" />

    <label for="suffix">Toevoeging</label>
    <input type="text" placeholder="Bis" id="suffix" v-model="suffix" v-on:input="validateInput" />
  </form>
</template>

<script>
  export default {
    name: "AddressValidation",
    data () {
      return {
        postal: '',
        number: '',
        suffix: '',
      }
    },
    methods: {
      validateInput: function () {
        if (!this.postal || !this.number) {
          this.$emit('input-invalidated');
        } else {
          this.$emit('input-validated', {
            postal: this.postal,
            number: this.number,
            suffix: this.suffix,
          });
        }
      }
    }
  }
</script>

<style scoped>

  form {
    overflow: hidden;
  }

  label {
    float: left;
    width: 200px;
    clear: both;
  }

  input {
    float: left;
    width: 200px;
  }

</style>

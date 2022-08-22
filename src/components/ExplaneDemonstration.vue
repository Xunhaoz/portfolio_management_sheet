<template>
    <v-container>
        
    </v-container>
</template>

<script>
  export default {
    data: () => ({
      show: false,
      valid: false,
      firstname: '',
      lastname: '',
      nameRules: [
        v => !!v || 'required',
        v => v.length <= 2 || 'Name must be less than 2 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'required',
        v => /.+@.+/.test(v) || 'E-mail must be valid',
      ],
    }),
    methods: {
      validate () {
        this.$refs.form.validate()
        this.show = false
      },
    },
  }
</script>
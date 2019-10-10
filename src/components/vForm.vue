<template>

  <div class="container">
    
    <form @submit.prevent="submit">
        <div class="form-group">
            <input 
                v-model="d_email"
                :class="{'is-invalid': $v.d_email.$error}"
                @blur="$v.d_email.$touch"
                type="email" 
                class="form-control"
                placeholder="Enter email"
            >
            <small class="form-text text-muted">
              <div v-if="!$v.d_email.required">Enter you email</div>
              <div v-if="!$v.d_email.email">Now email is invalid</div>
            </small>

        </div>
        <div class="form-group">
            <input 
                v-model="d_password"
                :class="{'is-invalid': $v.d_password.$error}"
                @blur="$v.d_password.$touch"
                type="password" 
                class="form-control" 
                id="exampleInputPassword1" 
                placeholder="Password"
            >
            <small class="form-text text-muted">
              <div v-if="!$v.d_password.required">Enter you password</div>
              <div v-if="!$v.d_password.minLength">Min length password is 6, now only {{ d_password.length }}</div>
            </small>
        </div>

        <button type="submit" class="btn btn-primary">Submit</button>

        <p class="typo__p" v-if="submitStatus === 'OK'">Thanks for your submission!</p>
        <p class="typo__p" v-if="submitStatus === 'ERROR'">Please fill the form correctly.</p>
        <p class="typo__p" v-if="submitStatus === 'PENDING'">Sending...</p>

        <pre>{{ $v }}</pre>
    </form>

  </div>

</template>

<script>

import { required, email, minLength } from 'vuelidate/lib/validators'

export default {
  name: 'vForm',
  data() {
    return {
        d_email: '',
        d_password: '',
        submitStatus: null
    }
  },
  validations: {
    d_email: {
      required,
      email
    },
    d_password: {
      required,
      minLength: minLength(6)
    }
  },
  methods: {
    submit() {
      console.log('submit!')
      this.$v.$touch()
      if (this.$v.$invalid) {
        this.submitStatus = 'ERROR'
      } else {
        // do your submit logic here
        this.submitStatus = 'PENDING'
        setTimeout(() => {
          this.submitStatus = 'OK'
        }, 500)
      }
    }
  }
}

</script>

<style scoped>
  .is-invalid { box-shadow: 0 0 3px red; }
  .cl-red { color: red; }
  pre {
    text-align: left;
  }
</style>
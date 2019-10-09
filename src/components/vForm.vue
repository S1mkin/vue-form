<template>

  <div class="container">
    
    <form>
        <div class="form-group">
            <label>Email address</label>
            <input 
                v-model="d_email"
                type="email" 
                class="form-control"
                placeholder="Enter email"
            >
            <small class="form-text text-muted">We'll never share your email with anyone else {{d_email}}.</small>
        </div>
        <div class="form-group">
            <label for="exampleInputPassword1">Password</label>
            <input 
                v-model="d_password"
                type="password" 
                class="form-control" 
                id="exampleInputPassword1" 
                placeholder="Password"
            >
        </div>
        <div class="form-check">
            <input type="checkbox" class="form-check-input" id="exampleCheck1">
            <label class="form-check-label" for="exampleCheck1">Check me out</label>
        </div>
        <button type="submit" class="btn btn-primary">Submit</button>
    </form>

  </div>

</template>

<script>
export default {
  name: 'vForm',
  data() {
    return {
        d_email: '',
        d_password: ''
    }
  }
}
</script>
<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-8">
        <div class="card">
          <div class="card-header">Login</div>

        <div class="card-body">
                    <div class="form-group row">
                            <label for="email" class="col-md-4 col-form-label text-md-right">E-Mail Address</label>

                            <div class="col-md-6">
                                <input id="email" type="email"  v-model="form.email" class="form-control " name="email" value="" required autocomplete="email" autofocus>

                            </div>
                        </div>

                        <div class="form-group row">
                            <label for="password" class="col-md-4 col-form-label text-md-right">Password</label>

                            <div class="col-md-6">
                                <input id="password" v-model="form.password" type="password" class="form-control " name="password" required autocomplete="current-password">

                              
                            </div>
                        </div>

                        <div class="form-group row">
                            <div class="col-md-6 offset-md-4">
                                <div class="form-check">
                                    <input class="form-check-input" type="checkbox" name="remember" id="remember" >

                                    <label class="form-check-label" for="remember">
                                        Remember Me
                                    </label>
                                </div>
                            </div>
                        </div>

                        <div class="form-group row mb-0">
                            <div class="col-md-8 offset-md-4">
                                <button type="submit" @click.prevent="loginUser" class="btn btn-primary">
                                   Login
                                </button>

                                <a class="btn btn-link" href="/forget-password">
                                    Forgot Your Password?
                                </a>
                            </div>
                        </div>
                    
                </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
    data(){
        return{
            form:{
                email: '',
                password: ''
            },
            errors: []
        }
    },
    methods:{
         loginUser(){
             axios.post('/api/login', this.form).then(() =>{
                 this.$router.push({ name: "dashboard"}); 
             }).catch((error) =>{
         this.errors = error.response.data.errors;
            })
         }
    }
}
</script>
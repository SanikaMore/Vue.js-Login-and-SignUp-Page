<template>
  <v-container>
    <v-row align="center" justify="center">
       <v-col cols="12" sm="10">
        <v-card class="elevation-6 mt-10">
          <v-window v-model="step">
            <v-window-item :value="1" >
              <v-row>
                <v-col cols="12" sm="6">
                  <v-card-text class="mt-12">
                    <h4 class="text-center">Login in to Your Account</h4>
                    <h6 class="text-center grey--text">Login to your Account so that you can continue building
                      <br>and editing your onboard flows
                    </h6>
                    <v-row align="center" justify="center">
                      <v-col cols="12" sm="8">
                        <v-text-field v-model="email" label="Email" outlined dense color="green" autocomplete="false" class="mt-16"></v-text-field>
                        <v-text-field v-model="password" label="Password" outlined dense color="green" autocomplete="false" type="password"></v-text-field>
                        <v-row>   
                          <v-col cols="12" sm="7">
                            <v-checkbox label="Remember Me" class="mt-n1" color="green"></v-checkbox> 
                          </v-col>
                          <v-col cols="12" sm="5">
                            <span class="caption green--text">Forgot Password</span>
                          </v-col>
                        </v-row>
                        <v-btn color="#89c540" dark block tile @click="login">Login In</v-btn>
                        <h5 class="text-center grey--text mt-4 mb-3">Or Log In using</h5>
                        <div class="d-flex justify-space-between align-center mx-10 mb-16">
                          <v-btn depressed outlined color="grey">
                            <v-icon color="red">fab fa-google</v-icon>
                          </v-btn>
                          <v-btn depressed outlined color="grey">
                            <v-icon color="blue">fab fa-facebook-f</v-icon>
                          </v-btn>
                          <v-btn depressed outlined color="grey">
                            <v-icon color="light-blue lighten-3">fab fa-twitter</v-icon>
                          </v-btn>
                        </div>
                      </v-col>
                    </v-row>
                  </v-card-text>
                </v-col>
                <v-col cols="12" sm="6" class="rounded-bl-xl" style="background-color: #89c540;">

                  <div style="text-align:center; padding:180px 0;">
                    <v-card-text class="white--text">
                      <h3 class="text-center">Dont have an Account yet?</h3>
                      <h6 class="text-center">
                        Lets get you all setup so you can start creating your first<br>
                        onboarding experience
                      </h6>
                    </v-card-text>
                    <div class="text-center">
                      <v-btn tile outlined dark @click="step++">SIGN UP</v-btn>
                    </div>
                  </div>
                </v-col>
              </v-row>
            </v-window-item>
          <v-window-item :value="2">
            <v-row>
              <v-col cols="12" sm="6" class="rounded-br-xl" style="background-color: #89c540;">

                <div style="text-align: center; padding: 180px 0;">
                 <v-card-text class="white--text">
                  <h3 class="text-center">Already Signed Up?</h3>
                  <h6 class="text-center">Log into you account to continue the process</h6>
                 </v-card-text>
                 <div class="text-center">
                  <v-btn tile outlined dark @click="step--">Log In</v-btn>
                 </div>
                </div>
               </v-col>
               <v-col cols="12" sm="6">
                <v-card-text class="mt-12">
                  <h4 class="text-center">Sign Up for An Account</h4>
                  <h6 class="text-center grey--text">
                    Let's get you all set so that you can start
                  </h6>
                  <v-row align="center" justify="center">
                    <v-col cols="12" sm="8">
                      <v-row>
                        <v-col cols='12' sm="6">
                          <v-text-field v-model="firstName" label="First Name" outlined dense color="green" autocomplete="false" class="mt-4"></v-text-field>
                        </v-col>
                        <v-col cols='12' sm="6">
                          <v-text-field v-model="lastName" label="Last Name" outlined dense color="green" autocomplete="false" class="mt-4"></v-text-field>
                        </v-col>
                      </v-row>
                      <v-text-field v-model="email2" label="Email" outlined dense color="green" autocomplete="false"></v-text-field>
                      <v-text-field v-model="password2" label="Password" outlined dense color="green" type="password"></v-text-field>
                      <v-row>
                        <v-col cols="12" sm="7">
                          <span class="caption green--text ml-n4">Terms & Conditions</span>
                        </v-col>
                      </v-row>
                      <v-btn color="#89c540" dark block tile @click="signup">Sign In</v-btn>
                      <h5 class="text-center grey--text mt-4 mb-3">Or SignUp using</h5>
                      <div class="d-flex justify-space-between align-center mx-10 mb-16">
                          <v-btn depressed outlined color="grey">
                            <v-icon color="red">fab fa-google</v-icon>
                          </v-btn>
                          <v-btn depressed outlined color="grey">
                            <v-icon color="blue">fab fa-facebook-f</v-icon>
                          </v-btn>
                          <v-btn depressed outlined color="grey">
                            <v-icon color="light-green lighten-3">fab fa-twitter</v-icon>
                          </v-btn>
                        </div>
                    </v-col>
                  </v-row>
                </v-card-text>
               </v-col>
              </v-row>
          </v-window-item>
          
          </v-window>
        </v-card>
       </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    step: 1,
    email: '',
    password: '',
    email2: '',
    password2: '',
    firstName:'',
    lastName:''
  }),

  props: {
    source: String
  },

  methods: {
    login() {
      
      console.log('Email:', this.email);
      console.log('Password:', this.password); //....Show login in console

    
      const storedLogins = localStorage.getItem('logins'); //....Insside stored login 

      let logins = [];

      
      if (storedLogins) {
        logins = JSON.parse(storedLogins);
      }

      
      logins.push({ email: this.email, password: this.password }); //....Add current login to list

      // Update the login credentials in local storage
      localStorage.setItem('logins', JSON.stringify(logins)); //....Update list as well

    
      alert('Logged in successfully!');
    },
    signup() {
      console.log('First Name:', this.firstName);
      console.log('Last Name:', this.lastName);
      console.log('Email:', this.email2);
      console.log('Password:', this.password2);

      const storedSignups = localStorage.getItem('signups');

      let signups = [];

      if (storedSignups) {
        signups = JSON.parse(storedSignups);
      }

      signups.push({ firstName: this.firstName, lastName: this.lastName, email: this.email2, password: this.password2 });

      localStorage.setItem('signups', JSON.stringify(signups));

      alert('Signed up successfully!');
    },
  }
}
</script>



<style scoped>
.v-application .rounded-bl-xl {
  border-bottom-left-radius: 300px !important;
}
.v-application .rounded-br-xl {
  border-bottom-right-radius: 300px !important;
}

</style>

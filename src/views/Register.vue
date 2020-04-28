<template>

<v-container>
    <h1>REGISTRATION</h1>
  <form>
    <v-text-field
      v-model="name"
      :error-messages="nameErrors"
      :counter="10"
      label="Name"
      required
      @input="$v.name.$touch()"
      @blur="$v.name.$touch()"
    ></v-text-field>
    <v-text-field
      v-model="email"
      :error-messages="emailErrors"
      label="E-mail"
      required
      @input="$v.email.$touch()"
      @blur="$v.email.$touch()"
    ></v-text-field>

    <v-text-field
    v-model ="password"
    :error-messages="passwordErrors"
    label="Password"
    type= "password"
    required
    @input="$v.password.$touch()"
    @blur="$v.password.$touch()"

>
    </v-text-field>

    <v-select
      v-model="select"
      :items="items"
      :error-messages="selectErrors"
      label="Role"
      required
     
      @blur="$v.select.$touch()"
    ></v-select>

    <v-text-field 
type="number"
v-model="age"
:error-messages="ageErrors"
required
label="Age"
@input="$v.age.$touch()"
@blur="$v.age.$touch()">


</v-text-field>
<v-textarea
v-model="address"
label="Address"


:error-messages="addressErrors"
required
@input="$v.address.$touch()"
@blur="$v.address.$touch()">
  
</v-textarea>
    <v-checkbox
      v-model="checkbox"
      :error-messages="checkboxErrors"
      label="Do you agree?"
      required
      @change="$v.checkbox.$touch()"
      @blur="$v.checkbox.$touch()"
    ></v-checkbox>

    <v-btn class="mr-4" @click="submit">submit</v-btn>
    <v-btn @click="clear">clear</v-btn>
  </form>
</v-container>
</template>

<script>
  import { validationMixin } from 'vuelidate'
  import { required, maxLength, email,minLength,minValue} from 'vuelidate/lib/validators'

  export default {
    mixins: [validationMixin],

    validations: {
      name: { required, maxLength: maxLength(10) },
      email: { required, email },
      password:{ required,minLength:minLength(6)},
      select: { required },
      age:{required, minValue:minValue(18)},
      address:{required},
      checkbox: {
        checked (val) {
          return val
        },
      },
    },

    data: () => ({
      name: '',
      email: '',
      password:'',
      select: null,
      items: [
        'Java developer',
        'Vue developer',
        'Node developer',
        'React developer',
      ],
      age:'',
      address:'',
      checkbox: false,
    }),

    computed: {
      checkboxErrors () {
        const errors = []
        if (!this.$v.checkbox.$dirty) return errors
        !this.$v.checkbox.checked && errors.push('You must agree to continue!')
        return errors
      },
      selectErrors () {
        const errors = []
        if (!this.$v.select.$dirty) return errors
        !this.$v.select.required && errors.push('Role is required')
        return errors
      },
      nameErrors () {
        const errors = []
        if (!this.$v.name.$dirty) return errors
        !this.$v.name.maxLength && errors.push('Name must be at most 10 characters long')
        !this.$v.name.required && errors.push('Name is required.')
        return errors
      },
      emailErrors () {
        const errors = []
        if (!this.$v.email.$dirty) return errors
        !this.$v.email.email && errors.push('Must be valid e-mail')
        !this.$v.email.required && errors.push('E-mail is required')
        return errors
      },
      passwordErrors(){
        const errors =[]
        if(!this.$v.password.$dirty) return errors
        !this.$v.password.minLength && errors.push('minimum 6 letters required')
        !this.$v.password.required && errors.push('Password is required')
        return errors
      },
      ageErrors(){
        const errors =[]
        if(!this.$v.age.$dirty) return errors
        !this.$v.age.minValue && errors.push('minimum age should be 18  years')
        !this.$v.age.required && errors.push('age is required')
        return errors
      },
      addressErrors(){
        const errors =[]    
        if(!this.$v.address.$dirty) return errors
        !this.$v.address.required && errors.push('Address is required')
        return errors
      }
    },

    methods: {
      submit () {
        this.$v.$touch()
        this.$router.push({name:'login'})
      },
      clear () {
        this.$v.$reset()
        this.name = ''
        this.email = ''
        this.password=''
        this.age=''
        this.address=''
        this.select = null
        this.checkbox = false
      },
    },
  }
</script>
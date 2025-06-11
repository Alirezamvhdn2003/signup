<template>
  <form>
    <label>firs name: <span>☀</span> </label>
    <input type="text" v-model="firstName" required>

    <label>last name: <span>☀</span> </label>
    <input type="text" v-model="lastName" required>

    <label>user name: <span>☀</span> </label>
    <input type="text" v-model="userName" required>

    <div class="password">
        <label>password: <span>☀</span> </label>
        <input :type="pass" v-model="password" class="pass" required>
    </div>
    <button @click.prevent="toggleShow" class="btn">{{ value }}</button>
    <p class="error" v-if="passwordEror">{{ passwordEror }}</p>

    <label>email: <span>☀</span> </label>
    <input type="email" v-model="email" required>

    <label>role:</label>
    <select v-model="role">
        <option value="teacher">teacher</option>
        <option value="student">student</option>
        <option value="developer">web developer</option>
        <option value="designer">web designer</option>
    </select>
    
    <div class="skill">
        <label>skils:</label>
        <span>please press enter after each skill , click on skill to remove</span>
        <input type="text" v-model="tepmSkill" @keyup="addSkill">
    </div>

    <div class="pillWrap">
        <div v-for="skill in skills" :key="skill" class="pill" @click="removeSkill(skill)">
            {{ skill }}
        </div>
    </div>
   
    <div class="terms">
        <input type="checkbox" id="box" v-model="terms" required>
        <label for="box"><a href="#">accept terms and policy</a></label>
    </div>

    <button class="submit" @click.prevent="submit">create account</button>

  </form>
</template>

<script>
export default {
    data() {
        return {
            firstName:'',
            lastName: '',
            userName: '',
            password: '',
            passwordEror: '',
            email: '',
            role: ' ',
            skills: [],
            terms: false ,
            pass: "password",
            value: 'show',
            tepmSkill: '',
        }
    },
    methods:{
        toggleShow() {
            if (this.pass == "password"){
                this.value = 'hide'
                this.pass = "text"
            }else{
                this.value = 'show'
                this.pass = "password"
            }
        },
        addSkill(event) {
            if (event.key === 'Enter' && this.tepmSkill){
                if (!this.skills.includes(this.tepmSkill)){
                    this.skills.push(this.tepmSkill)
                }
                this.tepmSkill = ''
            }
        },
        removeSkill(skill){
            this.skills = this.skills.filter((item) =>{
                return skill !== item
            })
        },
        submit(){
            this.passwordEror = this.password.length > 5 ? this.passwordEror = '' : this.passwordEror = 'password must be atleast 6 characters !'
            if (!this.passwordEror){
                console.log('firs name' , this.firstName)
                console.log('last name' , this.lastName)
                console.log('user name' , this.userName)
                console.log('password' , this.password)
                console.log('email' , this.email)
                console.log('role' , this.role)
                console.log('skills' , this.skills)
            }
        }
    }

}
</script>

<style>



</style>
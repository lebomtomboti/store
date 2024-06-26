<template>
    <div id="parent">
     <form @submit.prevent="formSubmit">
        <h1>sign Up Form hehe</h1>
        <!--using v-model to save data in properties-->
        <label>Email:</label>
        <input type="email" required v-model ="email">
        <label>Password:</label>
        <input type="password" required v-model ="password">
        <label>Role:</label>
        <!--select box-->
        <select v-model="role">
            <!--default option-->
            <option value="developer">Web Developer</option>
            <option value="desinger">Web Designer</option>
            <option value="">Select a role:</option>
        </select>
        <label>Languages</label>
        <input type="text" v-model="currentLanguage" @keydown="keyfinder" @keyup.enter. alt="addLanguage">
        <button type="submit">submit</button>
        <div v-for="lang,index in languages" :key="index+1">
            <p id="para" @click='deleting(lang)'>
                {{ index+1 }}:{{ lang }}
            </p>
        </div>
        <div class="terms">
           <input type="checkbox" required v-model="terms">
           <label>Accept  Terms and conditions</label>
        </div>
        <h4>People wanted in your team:</h4>
        <div>
            <input type="checkbox" value="mario" v-model="names">
            <label>Mario</label>
        </div>
        <div>
            <input type="checkbox" value='Dean' v-model="names">
            <label>Dean</label>
        </div>
        <div>
            <input type="checkbox" value="Luigi" v-model="names">
            <label>Luigi</label>
        </div>
     </form>
     <!--showing stored information in data function-->
     <div>
        <p>email:{{ email }}</p>
        <p>password:{{ names }}</p>
        <p>role:{{ names }}</p>
        <p>terms:{{terms }}</p>
        <p>currentLanguage:{{currentLanguage}}</p>
        <p>languages:{{ languages }}</p>
     </div>
    </div>
</template>
<script>
export default {
    name:'signUpForm',
    props:{
        msg:string   
    },
    data(){
        return{
    email:'',
    password:'',
    role:'',
    //if you want default value to be checked then change boolean to true
    terms:false,
    names:[],
    currentLanguage:'',
     languages:['something','nothing']
 } 
},
methods: {
    keyfinder(){
        console.log(event)
    },
    deleteLang(lang){
        this.languages = this.languages.filter(item=> item != lang)
    },
    formSubmit(){
        console.log('The page has refreshed');
        this.email = '',
        this.password = '',
        this.role = '',
        this.currentLanguage = '',
        this.terms = false
    
    },
    addLanguage(){
        if(!this.languages.includes(this.currentLanguage)){
            this.languages.push(this.currentLanguage)
        }
    },
},
computed:{

}

}
</script>
<style scoped>
    #parent{
        display: flex;
    }
    form{
        width: 20cap;
        padding: 5cap;
        text-align: center;
        margin-left: 25%;
        background-color: #092C4E;
        margin-left: auto;
        margin-right: auto;
    }
    input, select{
        background-color: #0B4580;
        border: 1px whitesmoke solid;
        border-radius: 5px;
        width: 250px;
        padding-bottom: 5px;
    }
    label{
       padding-top:5px ;
        width: 250px;
        text-align: left;
        font-size: small;
    }
    .terms{
       display: flex;
       width: 400px;
    }
    input[type='checkbox']{
        height: 16px;
        width: 16px;
        position: relative;
        top: 2px;
    }
    #para{
        width: 200px;
        height: 10px;
        box-sizing: content-box;
        border: white dashed 5px;
        margin: 0px;
        padding: 10px 10px 15px 5px;
        cursor: pointer;
    }
    #para:hover{
        background-color: aliceblue;
    }
    
</style>
<template>

    <tr :id="person.login.uuid">
        <td> <img :src="person.picture.medium" /></td>
        <td>{{person.name.first}}</td>
        <td> {{person.name.last}}</td>
        <td>{{person.email}}</td>
        <td>{{person.gender}}</td>
        <td v-if="page == 'home'"><button @click="saveUser()"> Save User</button></td>
        <td v-if="page == 'saved'"><button @click="deleteUser()"> Delete User</button></td>
    </tr>
</template>
<script>


export default {
    name:'EachPeople',
    props:{
        person:Object,
        id:String,
        page:String,
    },
    methods:{
        async saveUser(){
            try{
                let data = window.localStorage.getItem("people")
                data =  data?JSON.parse(data):[]
                var {name,email,picture,gender,login} =this.person
                let newUser =  {name,email,picture,gender,login} 
                let newData = [...data,newUser]
                newData = JSON.stringify(newData)
                window.localStorage.setItem("people",newData)
                alert(`${name.first} saved to storage successfully`)
            }
            catch(e){
                alert("failed to save user")
                console.log(e);
            }
        },
        async deleteUser(){
            try{
                let data = window.localStorage.getItem("people")
                data =  data?JSON.parse(data):[]
                let delID = this.person.login.uuid
                let newData = data.filter(user => {
                    if(user.login.uuid != delID){
                        return user
                    }
                })
                newData = JSON.stringify(newData)
                window.localStorage.setItem("people",newData)
                let tr = document.getElementById(delID)
                tr.remove();
                alert(`${this.person.name.first} removed from storage successfully`)
            }
            catch(e){
                alert("failed to delete user")
                console.log(e);
            }
        }
    }
}
</script>
<style scoped>

    button{
        cursor: pointer;
        display: inline-block;
        background: #333;
        color: #fff;
        font-size: 15px;
        border: 0;
        padding: 0.5rem 0.7rem;
    }

    button:focus{
        outline: none;
    }

    button:hover{
        transform: scale(0.98)
    }
</style>

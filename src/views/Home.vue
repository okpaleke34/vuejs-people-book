<template>
  <div class="home">
      <table>
        <thead>
          <tr>
            <th></th>
            <th>First Name</th>
            <th> Last Name</th>
            <th>Email</th>
            <th>Gender</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <EachPeople v-for="person in people" :key="person.email" :id="person.email" :person="person" page="home" />
        </tbody>
      </table>
  </div>
</template>

<script>
import EachPeople from '@/components/EachPeople.vue'

export default {
  name: 'Home',
  components: {
    EachPeople
  },
    data(){
        return{
            people:[]
        }
    },
    async created(){
        const config = {
            headers:{
                'Accept':'application/json'
            }
        }

        try {
            const res = await fetch('https://randomuser.me/api/?page=3&results=10')
            const { results } = await res.json()
            this.people = results
        } 
        catch (error) {
            console.log(error);
        }
    }
}
</script>

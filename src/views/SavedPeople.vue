<template>
  <div class="home">
    <h1>List of saved people</h1>
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
          <EachPeople v-for="person in people" :key="person.email" :id="person.email" :person="person" page="saved" />
        </tbody>
      </table>
  </div>
</template>

<script>
import EachPeople from '@/components/EachPeople.vue'

export default {
  name: 'SavedPeople',
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
      
      let data = window.localStorage.getItem("people")
      data =  data?JSON.parse(data):[]
      this.people = data
      console.log(this.people);
    } 
    catch (error) {
      console.log(error);
    }
  }
}
</script>
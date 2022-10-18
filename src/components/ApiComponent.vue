<template>
    <div>
        <!-- <select @click="getusers" class="my-5">
           <option v-for="user in users" :key="user.id">
            <h3>{{user.name}}</h3>
        </option>
       </select> -->
   </div>
</template>
<script>
import axios from 'axios'
export default {
    name: 'ApiComponent',
    data() {
        return {
            users: []
        }
    },
    methods: {
        getusers() {
            axios.get('https://jsonplaceholder.typicode.com/users')
                .then((response) => {
                    console.log(response.data)
                    this.users = response.data
                })
        }
    }
}
</script>
<style scoped>

</style>
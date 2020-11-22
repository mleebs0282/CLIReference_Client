<template>
  <div class="commands">
    <h1>{{ title }}</h1>
    <table>
        <thead class="thead-dark">
            <tr>
                <th>Description</th>
                <th>Usage</th>
                <th>Platform</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="command in commands" :key="command.Id">
                <td>{{command.description}}</td>
                <td>{{command.usage}}</td>
                <td>{{command.platform}}</td>
            </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
    import axios from 'axios';
    export default {
        name: 'Commands',
        data() {
            return {
                commands: []
            }
        },
        mounted () {
            axios
                .get('https://localhost:5001/api/Command')
                .then(response => (this.commands = response.data.commands))
        },
        props: {
            title: String
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

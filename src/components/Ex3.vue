<script>
import axios from 'axios';

    export default { 

       // add code here
        data(){
            return{
                moods: ["Happy", "Sad", "Angry"],
                subject: "",
                entry: "",
                selMood: "",
                outputMsg: ""
            }
        }

       computed: {

       },
       methods: {
        addPost(){
            //issue get request to addPost backend service
            axios.get(`${this.baseUrl}/addPost`)
            .then(response =>{
                this.outputMsg = response.data.message
            })
            .catch(error =>{
                this.posts = [{entry: "There was an error: " + error.message}]
            })

        }
       }

    }
</script>

<template>
    <div class="table m-2">
        <h3>Add a New Blog Post</h3>

        Subject: <input type='text' size='30' v-model='subject' required>
        <br>

        Entry: <br>
        <textarea name='entry' cols='80' rows='5' v-model='entry' required></textarea>
        <br>

        Mood:
        <!-- TODO: Build a dropdown list here for selecting the mood -->
            <select v-model="selMood">
                <option v-for="mood in moods"> {{ mood }}</option> <!-- should be mood, not posts -->
            </select>
        <br>

        <br>
        <button @click="addPost">Submit New Post</button>
        <br></br>
        {{ outputMsg }}
        <hr> Click  <a><router-link to="/ViewPosts/">here</router-link></a>  to return to Main Page
       
    </div>
</template>


<template>
    <div>
        <h1>Participant Forms</h1>
        <p>Please enter each participant's name, email, and a short description of them below</p>
        <v-text-field
            v-model="name"
            :rules="[rules.checknameSize]"
            label= "Name"
            counter
            maxlength="256"
        ></v-text-field>
        <v-text-field
            v-model="email"
            :rules="[rules.checkEmail]"
            label= "Email"
        ></v-text-field>
        <v-text-field
            v-model="aboutParticipant"
            :rules="[rules.checkAbout]"
            label= "About"
            counter
            maxlength="3000"
        ></v-text-field>
    </div>
    

</template>

<script>

export default({
    data() {
        return {
            name: 'John', //no NULL 256 Max
            email: '', //Input rule needed
            aboutParticipant: '', // so No check 3000 Max
            rules: {
                checknameSize: value => (value.length <= 256 && value.length > 0) || 'Name too long or too short',//Works
                checkEmail: value => /.+@.+/.test(value) || 'Invalid Email',//Works
                checkAbout: value => value.length <= 3000 || 'Too many words sum it up', //Works
             //Gonna need 3 input rules
            },
                    
        }
    },
})
</script>

<style>
</style>



<template>
<p>Create one form component that takes in the name, email, and text input for info on the participant</p>
</template>

<script>

export default({
    data() {
        return {
            name: '',
            email: '',
            aboutParticipant: '',
            inputRule: 'you will probs need a rule per item, except maybe about, up to you/Kate, look into reg exp or input rules on vue'
        }
    },
    methods:{
        validate(){
            //perhaps validate on here, use rules on the v-input, you can bind it and it will show as the user inputs
        }
    }
})
</script>



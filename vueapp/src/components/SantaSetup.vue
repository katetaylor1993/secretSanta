<template>
    <v-container>
        <p>Generating... P.S. I will make this look better don't worry :P</p>
        <div v-if="generated">
        <EmailModal :value="emailObject" @failure="fix"/>
        </div>
    </v-container>  
</template>
<script>
import EmailModal from './EmailModal.vue';

export default ({
    prop: value,
    components: {
        EmailModal
    },
    data() {
        return {
            //i will generate list of each email and generate them randomly in the methods, set up generated to true if 
            //randomize is complete with checks to make sure everyone has someone
            generated: false,
            emailObject: [{}]
        }
        
    },
    methods: {
        randomize(){
            //i will mess around with this and make it work
            //will make email object either loop hrough each email modal in a v-for for each in the data object
            //do a full objec twith everytwo and from, going through one will be easier to debug probably
        },
        fix(object){
            //this is when email modal failed, it will return the error message to here as well so i can fix it
            //when it is fixed, will need to recall email modal to try again
            this.generated = !this.generated;
        }
    }
})
</script>

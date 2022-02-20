<template>
    <v-container>
        <p>This will take in a prop, and show it as the error, will be set up later! as of now, this is the error :p </p>
        {{ value }}
    </v-container>
</template>

<script>
export default ({
    props: ['value'],
    methods: {
        generateError(){
            //this is where i will take in the value and display it properly
        }
    }
})
</script>

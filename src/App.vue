<script setup>
import CookieModal from './components/Cookies/CookieModal.vue';

const cookieContext = {
    rejectButtonActive: true,
    cookieHeader: "header",
    cookieDescription: "Description Here",
    cookiePolicy: "Policy Here",
    cookieSettings: "Settings Here",
    acceptButton:{
        text:"Kabul Et",
        textColor: "white",
        bgColor: "orange",
        bgHover: "" 

    },
    declineButton:{
        text:"Reddet",
        textColor: "white",
        bgColor: "coral",
        bgHover: ""
    }
}


</script>

<template>
   
	<CookieModal v-bind="{...cookieContext}"></CookieModal>
    
</template>

<style scoped>

</style>

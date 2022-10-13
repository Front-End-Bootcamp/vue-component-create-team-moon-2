<script setup>
import CookieModal from './components/Cookies/CookieModal.vue';

const cookieContext = {
    rejectButtonActive: true,
    cookieHeader: "header",
    cookieDescription: "Description Here",
    cookiePolicy: "Policy Here",
    cookieSettings: "Settings Here",
    // acceptButton:{
    //     //text:"Kabul Et",
    //     //textColor: "white",
    //    // bgColor: "green",
    //     //bgHover: "" 
    // },
		acceptButtonText: "Accept",
		acceptButtonColor: "white",
		acceptButtonBGC: "green",
		acceptButtonHover: "",
		declineButtonText: "Decline",
		declineButtonColor: "white",
		declineButtonBGC: "green",
		acceptButtonHover: "",
    // declineButton:{
    //     text:"Reddet",
    //     textColor: "white",
    //     bgColor: "coral",
    //     bgHover: ""
    // }
}


</script>

<template>
   
	<CookieModal v-bind="{...cookieContext}"></CookieModal>
    
</template>

<style scoped>
a{
	background-color: rgb(255, 128, 0);
}
</style>

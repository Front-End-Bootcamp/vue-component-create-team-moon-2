<script setup>
import CookieModal from './components/Cookies/CookieModal.vue';

const cookieContext = {
    rejectButtonActive: true,
		//cookieModalBGC:"black",
    cookieHeader: "header",
		cookieHeaderColor: "white",
    cookieDescription: "Description Here",
		cookieDescriptionColor: "white",
    cookiePolicy: "Policy Here",
		cookiePolicyColor: "green",
    cookieSettings: "Settings Here",
    // acceptButton:{
    //    //text:"Kabul Et",
    //    //textColor: "white",
    //    // bgColor: "green",
    //     
    // },
		acceptButtonText: "Accept",
		acceptButtonColor: "white",
		acceptButtonBGC: "green",
		declineButtonText: "Decline",
		declineButtonColor: "white",
		declineButtonBGC: "green",
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

</style>

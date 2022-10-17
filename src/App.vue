<script setup>
import CookieModal from './components/Cookies/CookieModal.vue';

const cookieContext = {
	rejectButtonActive: true,
	cookieModalBGC: "black",
	cookieHeader: "Header Text Here",
	cookieHeaderColor: "white",
	cookieDescription: "Description Here",
	cookieDescriptionColor: "white",
	cookiePolicy: "Policy Here",
	cookiePolicyColor: "green",
	cookieSettings: "SettingsText",
	acceptButtonText: "AcceptText",
	acceptButtonColor: "white",
	acceptButtonBGC: "green",
	declineButtonText: "DeclineText",
	declineButtonColor: "white",
	declineButtonBGC: "green",
}

	// acceptButton:{
	//    //text:"Kabul Et",
	//    //textColor: "white",
	//    //bgColor: "green",
	// },
	// declineButton:{
	//     text:"Reddet",
	//     textColor: "white",
	//     bgColor: "coral",
	//     bgHover: ""
	// }



</script>

<template>

	<CookieModal v-bind="{...cookieContext}"></CookieModal>

</template>

<style scoped>

</style>

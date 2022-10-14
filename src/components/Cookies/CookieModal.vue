<script setup>
import { onMounted, ref } from 'vue';

const props = defineProps({
	rejectButtonActive: {
		type: Boolean,
		default: true,
	},
	cookieModalBGC: {
		type: String,
		default: "rgb(38, 38, 38)"
	},
	cookieHeader: {
		type: String,
		default: "Daha iyi bir deneyim için izninizi istiyoruz.",
	},
	cookieDescription: {
		type: String,
		default: `Tanımlama bilgilerini; sitemizin doğru şekilde çalışmasını sağlamak, içerikleri ve reklamları kişiselleştirmek, sosyal medya özellikleri sunmak ve site
                    trafiğimizi analiz etmek için kullanıyoruz. Aynı zamanda site kullanımınızla ilgili bilgileri; sosyal medya, reklamcılık ve analiz ortaklarımızla paylaşıyoruz.`,
	},
	cookiePolicy: {
		type: String,
		default: "Çerez Politikası",
	},
	cookiePolicyColor: {
		type: String,
		default: "orange"
	},
	cookieSettings: {
		type: String,
		default: "Çerez Ayarları",
	},
	// acceptButton: {
	// 	type: Object,
	// 	default: () => {
	// 		return {
	// 			text: "Kabul Et",
	// 			bgColor: "orange"
	// 		}
	// 	}
	// },
	acceptButtonText: {
		type: String,
		default: "Kabul Et"
	},
	acceptButtonColor: {
		type: String,
		default: "white"
	},
	acceptButtonBGC: {
		type: String,
		default: "rgb(255, 128, 0)"
	},
	declineButtonText: {
		type: String,
		default: "Reddet"
	},
	declineButtonColor: {
		type: String,
		default: "white"
	},
	declineButtonBGC: {
		type: String,
		default: "rgb(255, 128, 0)"
	},
	// declineButton: {
	// 	text: {
	// 		type: String,
	// 		default: "Reddet",
	// 	},
	// 	bgColor: {
	// 		type: String,
	// 		default: "rgb(255 96 0 / var(--tw-bg-opacity))"
	// 	}
	// }

});

// console.log(props.acceptButton);
// const acceptBGC = props.acceptButton.bgColor;
// const declineBGC = props.declineButton.bgColor;


const showCookie = ref(JSON.parse(localStorage.getItem("cookieCheck")));


onMounted(() => {
	checkCookie(showCookie);
})

function checkCookie(localCheck) {
	if (localCheck.value != true) {
		localStorage.setItem("cookieCheck", false);
	}
	return;
}

function acceptCookie() {
	localStorage.setItem("cookieCheck", true);
	showCookie.value = localStorage.getItem("cookieCheck");
	return;
}

function declineCookie() {
	localStorage.setItem("cookieCheck", "refused");
}

</script>

<template>

	<template v-if="!showCookie">
		<div class="cookie" :style="{backgroundColor: props.cookieModalBGC}">
			<div class="cookie__description">
				<div class="cookie__header">
					<p>{{props.cookieHeader}}</p>
				</div>
				<div class="cookie__text">
					<p>{{props.cookieDescription}}
						<a class="policy" :style="{color: props.cookiePolicyColor}" href="#">{{props.cookiePolicy}}</a>
					</p>
				</div>
			</div>
			<div class="cookie__buttons">
				<button @click="acceptCookie" class="accept-cookie"
					:style="{backgroundColor: props.acceptButtonBGC, color: props.acceptButtonColor}">{{props.acceptButtonText}}</button>
				<template v-if="props.rejectButtonActive">
					<button @click="declineCookie" class="decline-cookie"
						:style="{backgroundColor: props.declineButtonBGC, color: props.declineButtonColor}">{{props.declineButtonText}}</button>
				</template>
				<a class="cookie-settings" href="#">{{props.cookieSettings}}</a>
			</div>
		</div>
	</template>

</template>

<style lang="scss" scoped>
.cookie {
	@apply  absolute bottom-0 flex w-full text-gray-50 ;
	box-shadow: rgba(0, 0, 0, 0.56) 0px 22px 70px 4px;
	&__description {

		@apply w-full flex justify-center flex-col p-3;

		.cookie__header {
			@apply text-[18px] mb-3;
		}

		.cookie__text {
			@apply text-[14px];
		}

		.policy {
			@apply underline text-primary;
		}

		.policy:hover {
			@apply text-orange-700 brightness-90;
		}
	}

	&__buttons {
		@apply flex justify-center items-center gap-6;

		.accept-cookie {
			@apply p-3 rounded-[3px] w-32;
			// background-color: v-bind(acceptBGC);
		}

		.accept-cookie:hover {
			@apply text-gray-300 brightness-90;

		}

		.decline-cookie {
			@apply p-3 rounded-[3px] w-32;
			// background-color: v-bind(declineBGC);
		}

		.decline-cookie:hover {
			@apply text-gray-300 brightness-90;

		}

		.cookie-settings:hover {
			@apply brightness-75;
		}
	}

}
</style>

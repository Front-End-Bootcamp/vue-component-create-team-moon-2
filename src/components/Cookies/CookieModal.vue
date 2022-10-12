<script setup>
import { onMounted, ref } from 'vue';

const props = defineProps({
    rejectButtonActive: {
        type: Boolean,
        default: true,
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
    cookieSettings: {
        type: String,
        default: "Çerez Ayarları",
    },
    acceptButton: {
        text: {
            type: String,
            default: "Kabul Et"
        },
        bgColor: {
            type: String,
            default: "rgb(255 96 0 / var(--tw-bg-opacity))"
        }
    },
    declineButton: {
        text: {
            type: String,
            default: "Reddet",
        },
        bgColor: {
            type: String,
            default: "rgb(255 96 0 / var(--tw-bg-opacity))"
        }
    }

});

console.log(props.acceptButton);
const acceptBGC = props.acceptButton.bgColor;
const declineBGC = props.declineButton.bgColor;


const showCookie = ref(JSON.parse(localStorage.getItem("cookieCheck")));


onMounted(() => {
    checkCookie(showCookie);
})

function checkCookie(check) {
    if (check.value != true) {
        localStorage.setItem("cookieCheck", false);
    }
    return;
}

function acceptCookie() {
    localStorage.setItem("cookieCheck", true);
    showCookie.value = localStorage.getItem("cookieCheck");
    return;
}

</script>

<template>

    <template v-if="!showCookie">
        <div class="cookie">
            <div class="cookie__description">
                <div class="cookie__header">
                    <p>{{props.cookieHeader}}</p>
                </div>
                <div class="cookie__text">
                    <p>{{props.cookieDescription}}
                        <a class="policy" href="#">{{props.cookiePolicy}}</a>
                    </p>
                </div>
            </div>
            <div class="cookie__buttons">
                <button @click="acceptCookie" class="acceptCookie">{{props.acceptButton.text}}</button>
                <template v-if="props.rejectButtonActive">
                    <button @click="rejectCookie" class="declineCookie">{{props.declineButton.text}}</button>
                </template>
                <a href="#">{{props.cookieSettings}}</a>
            </div>
        </div>
    </template>

</template>

<style lang="scss" scoped>
.cookie {
    @apply w-full bg-neutral-800 absolute bottom-0 flex text-gray-50;

    &__description {

        @apply w-2/3 flex justify-center flex-col p-3;

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
            @apply text-orange-700;
        }
    }

    &__buttons {
        @apply w-1/3 flex justify-center items-center gap-6;

        .acceptCookie {
            @apply bg-primary p-3 rounded-[3px] w-32;
            background-color: v-bind(acceptBGC);
        }

        .acceptCookie:hover {
            @apply bg-orange-600 text-gray-300;
        }

        .declineCookie{
            @apply bg-primary p-3 rounded-[3px] w-32;
            background-color: v-bind(declineBGC);
        }
        .declineCookie:hover {
            @apply bg-primary text-gray-300;
            
        }
    }

}
</style>

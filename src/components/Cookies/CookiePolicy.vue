<script setup>
import { ref } from "vue";
const props = defineProps(["isPolicyOpen", "PolicyTitle", "PolicyText"]);
const emits = defineEmits(["closeModalPolicy"]);
const isModalOpen = ref(false);

const closeModalPolicy = () => {
	emits("closeModalPolicy", isModalOpen);
};
</script>

<template>
	<div class="policy">
		<button class="close-modal" @click="closeModalPolicy">&times;</button>
		<h1 class="policy--title">{{ props.PolicyTitle }}</h1>
		<p class="policy--text">{{ props.PolicyText }}</p>
	</div>
</template>

<style lang="scss" scoped>
.policy {
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	width: 35%;
	background-color: white;
	padding: 2rem;
	border-radius: 7px;
	box-shadow: 0 3rem 5rem rgba(0, 0, 0, 0.3);
	z-index: 10;

	&--title {
		text-align: center;
		font-size: 2rem;
		margin-bottom: 2rem;
	}
	&--text {
		font-size: 1rem;
	}
}

// .modal--title {
// 	text-align: center;
// }

.close-modal {
	@apply flex items-center justify-center absolute top-0 right-0 text-[36px] bg-slate-200 rounded-tr-lg rounded-bl-lg w-8;
	@apply hover:bg-slate-400;
}

// h1 {
// 	font-size: 2.5rem;
// 	margin-bottom: 2rem;
// }

// p {
// 	font-size: 1.8rem;
// }
</style>

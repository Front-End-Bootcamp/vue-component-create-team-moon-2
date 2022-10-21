<script setup>
import { ref } from "vue";
const props = defineProps(['isOpen']);
const emits = defineEmits(["closeModal"]);

const isModalOpen = ref(false);

const closeModal = () =>{
	emits("closeModal", isModalOpen)
};


</script>

<template>
	<div class="modal">
		<button class="close-modal" @click="closeModal">&times;</button>
		<h1 class="modal--title">Çerez Ayarları</h1>

		<table class="cookie--table">
			<tr>
				<td>
                    <p>Zorunlu çerezler</p>
                </td>
				<td>
					<label class="switch">
						<input type="checkbox" checked />
						<span class="slider round"></span>
					</label>
				</td>
			</tr>
			<tr>
				<td>
                    <p>Performans Çerezleri</p>
                </td>
				<td>
					<label class="switch">
						<input type="checkbox" />
						<span class="slider round"></span>
					</label>
				</td>
			</tr>
			<tr>
				<td>
                    <p>Hedefleme Çerezleri</p>
                </td>
				<td>
					<label class="switch">
						<input type="checkbox" />
						<span class="slider round"></span>
					</label>
				</td>
			</tr>
			<tr>
				<td>
                    <p>İşlevsellik Çerezleri</p>
                </td>
				<td>
					<label class="switch">
						<input type="checkbox" />
						<span class="slider round"></span>
					</label>
				</td>
			</tr>
		</table>
	</div>
</template>

<style scoped>
.modal {
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
}
.modal--title{
    text-align: center;
}

.close-modal {
	position: absolute;
	top: -1.8rem;
	right: 1rem;
	font-size: 4rem;
	color: #333;
	cursor: pointer;
	border: none;
	background: none;
}

h1 {
	font-size: 2.5rem;
	margin-bottom: 2rem;
}

p {
	font-size: 1.8rem;
}

.cookie--table{
    width :100%;
}

.switch {
	position: relative;
	display: inline-block;
	width: 60px;
	height: 34px;
}

.switch input {
	opacity: 0;
	width: 0;
	height: 0;
}

.slider {
	position: absolute;
	cursor: pointer;
	top: 0;
	left: 0;
	right: 0;
	bottom: 0;
	background-color: #ccc;
	-webkit-transition: 0.4s;
	transition: 0.4s;
}

.slider:before {
	position: absolute;
	content: "";
	height: 26px;
	width: 26px;
	left: 4px;
	bottom: 4px;
	background-color: white;
	-webkit-transition: 0.4s;
	transition: 0.4s;
}

input:checked + .slider {
	background-color: green;
}

input:focus + .slider {
	box-shadow: 0 0 1px green;
}

input:checked + .slider:before {
	-webkit-transform: translateX(26px);
	-ms-transform: translateX(26px);
	transform: translateX(26px);
}

/* Rounded sliders */
.slider.round {
	border-radius: 34px;
}

.slider.round:before {
	border-radius: 50%;
}
</style>

<script setup>
import { ref, computed } from "vue";

const searchInput = ref();
const filteredData = ref();

const data = [
	"Hasan",
	"Hüseyin",
	"Ali",
	"Veli",
	"Fatih",
	"Alihan",
	"Ankara",
	"Rize",
	"Adıyaman",
	"Trabzon",
];

const searchData = computed(() => {
	filteredData.value = data.filter((dataItem) => {
		dataItem = dataItem.toLowerCase();
		return dataItem.startsWith(searchInput.value.toLowerCase());
	});
});

const searchComplete = (dataItem) => {
	searchInput.value = dataItem;
};

</script>

<template>
	<div class="search">
		<input class="form__input" type="text" v-model="searchInput" @input="searchData" />
	</div>
	<div class="filter__data">
		<ul v-if="searchInput">
			<li class="search__data" v-for="dataItem in filteredData" @click="searchComplete(dataItem)">
				{{ dataItem }}
			</li>
		</ul>
	</div>
</template>

<style scoped>
.search {
	display: flex;
	justify-content: center;
}

.filter__data {
	display: flex;
	justify-content: center;
}

.form__input {
	color: #333;
	font-size: 1.2rem;
	padding: 10px;
	border-radius: 0.2rem;
	background-color: rgb(255, 255, 255);
	border: none;

	display: block;
	border: 1px solid black;
	transition: all 0.3s;
}

.search__data {
	list-style: none;
	margin: 10px;
	padding: 10px;
	background-color: #fff;
	border: 1px solid black;
	border-radius: 5px;
	box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
}
</style>

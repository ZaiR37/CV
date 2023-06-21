<template>
	<div class="header">
		<div class="header-wrapper">
			<img src="../assets/Leaves_object.svg" alt="leaves">
			<ul>
				<li v-for="item in navList" :key="item">
					<a v-bind:href="`#${item}`"> {{ item }}</a>
				</li>
			</ul>
		</div>
	</div>
</template>

<script setup>
const navList = ['About', 'Projects', 'Contact'];
</script>

<style scoped>
.header {
	padding: 5px 10px 5px 10px;
	background-color: hsla(0, 100%, 100%, 0.04);
	box-shadow:
		0px 1px 1px 0px hsla(0, 0%, 0%, 0.14),
		0px 2px 1px -1px hsla(0, 0%, 0%, 0.12),
		0px 1px 3px 0px hsla(0, 0%, 0%, 0.2);
	font-weight: 500;
	font-size: 1.1rem;
}

.header-wrapper{
	width: 90%;
	margin: auto;
	display: flex;
	justify-content: space-between;
}

img {
	filter: sepia(30%);
	padding: 2px;
	height: 4rem;
	width: auto;
}

ul {
	display: flex;
	justify-content: end;
	list-style-type: none;
}

li {
	padding: 0 10px 0 10px;
	display: inline-block;
}


a {
	color: rgb(133, 152, 177);
	text-decoration: none;
}

a:hover {
	color: rgb(155, 164, 175);
}

a:active {
	color: rgb(177, 179, 180);
}
</style>
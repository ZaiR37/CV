<template>
	<div class="header">
		<div class="header-wrapper">
			<img src="../assets/Leaves_object.png" alt="leavesImage">
			<ul>
				<li v-for="item in navList" :key="item">
					<a v-bind:href="`#${item}`"> {{ item }}</a>
				</li>
			</ul>
		</div>
		<div class="curve-bottom">
			<svg data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none">
				<path
					d="M0,0V46.29c47.79,22.2,103.59,32.17,158,28,70.36-5.37,136.33-33.31,206.8-37.5C438.64,32.43,512.34,53.67,583,72.05c69.27,18,138.3,24.88,209.4,13.08,36.15-6,69.85-17.84,104.45-29.34C989.49,25,1113-14.29,1200,52.47V0Z"
					opacity=".25" fill="#b2c1c2"></path>
				<path
					d="M0,0V15.81C13,36.92,27.64,56.86,47.69,72.05,99.41,111.27,165,111,224.58,91.58c31.15-10.15,60.09-26.07,89.67-39.8,40.92-19,84.73-46,130.83-49.67,36.26-2.85,70.9,9.42,98.6,31.56,31.77,25.39,62.32,62,103.63,73,40.44,10.79,81.35-6.69,119.13-24.28s75.16-39,116.92-43.05c59.73-5.85,113.28,22.88,168.9,38.84,30.2,8.66,59,6.17,87.09-7.5,22.43-10.89,48-26.93,60.65-49.24V0Z"
					opacity=".5" fill="#b2c1c2"></path>
				<path
					d="M0,0V5.63C149.93,59,314.09,71.32,475.83,42.57c43-7.64,84.23-20.12,127.61-26.46,59-8.63,112.48,12.24,165.56,35.4C827.93,77.22,886,95.24,951.2,90c86.53-7,172.46-45.71,248.8-84.81V0Z"
					fill="#b2c1c2"></path>
			</svg>
		</div>
	</div>
</template>

<script setup>
const navList = ['About', 'Projects', 'Contact'];

const color = {
	background: "#FFF2F2",
	font: "#8699b1",
	font_hover: "#9ba4af",
	font_active: "#b1b3b4",
};
</script>

<style scoped>
.header {
	height: 80px;
	padding: 5px 10px 5px 10px;
	background-color: v-bind('color.background');
	font-weight: 500;
	font-size: 1.1rem;
}

.header-wrapper {
	width: 90%;
	margin: auto;
	display: flex;
	justify-content: space-between;
}

img {
	position: relative;
	top: -5px;
	filter: sepia(30%);
	padding: 2px;
	padding-left: 3vw;
	height: 5rem;
	width: auto;
	z-index: 2;
}

ul {
	padding: 0;
	display: flex;
	justify-content: end;
	list-style-type: none;
}

li {
	position: relative;
	top: 8px;
	padding: min(5%, 8px);
	margin: auto;
	display: inline-block;

	-khtml-user-select: none;
	-o-user-select: none;
	-moz-user-select: none;
	-webkit-user-select: none;
	user-select: none;
}

a {
	color: v-bind('color.font');
	text-decoration: none;

	background:
		linear-gradient(to left, rgba(100, 200, 200, 0.253), rgba(100, 200, 200, 0.61));
	background-size: 0 0.1em, 100% 0.1em;
	background-position: 100% 100%, 0 100%;
	background-repeat: no-repeat;
	transition: background-size 400ms;
}

a:hover,
a:focus {
	color: v-bind('color.font_hover');
	background-size: 100% 0.1em, 0 0.1em;
}

a:active {
	color: v-bind('color.font_active');
}

/*---- CURVE BOTTOM ----*/
.curve-bottom {
	position: absolute;
	top: 70px;
	left: 0;
	width: 100dvw;
	overflow: hidden;
	line-height: 0;
	transform: rotate(180deg);
}

.curve-bottom svg {
	position: relative;
	display: block;
	width: calc(100dvw + 1.3px);
	height: 27px;
}

@media (max-width: 350px) {
	img {
		padding-left: 0;
		left: -12px
	}

	li {
		left: 16px;
	}
}
</style>
<template>
	<div class="cover">
		<div class="cover-wrapper">
			<div class="content">
				<span id="greet">Hi i'm</span>
				<span id="name">Lorem Ipsum</span>
				<div id="desc">
					<span>Lorem ipsum dolor sit amet consectetur adipisicing elit. Error eum consequuntur maiores. Nihil
						deleniti ut natus illo.
					</span>
				</div>
				<img id="handIcon" src="../assets/handIcon.svg" alt="handIcon">
			</div>
			<div class="img-wrapper">
				<img src="../assets/coverImage.svg" alt="ComputerImage">
			</div>
		</div>
		<div class="curve-bottom">
			<svg data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none">
				<path
					d="M321.39,56.44c58-10.79,114.16-30.13,172-41.86,82.39-16.72,168.19-17.73,250.45-.39C823.78,31,906.67,72,985.66,92.83c70.05,18.48,146.53,26.09,214.34,3V0H0V27.35A600.21,600.21,0,0,0,321.39,56.44Z"
					class="shape-fill">
				</path>
			</svg>
		</div>
	</div>
</template>

<script setup>
const color = {
	background: "#b2c1c2",
	background_next: "#f1f6f6",
	background_desc: "#929e9fbe",
	font_greet: "#647080",
	font_name: "#647080",
	font_desc: "#ddeaf8ea",
};
</script>

<style scoped>
.cover {
	background-color: v-bind('color.background') ;
	padding-top: 10px;
	padding-bottom: 10px;
	min-height: 460px;
	height: 85dvh;
	position: relative;
}

.cover-wrapper {
	display: flex;
	align-items: center;
	justify-content: center;
	text-align: center;
	margin: auto;
	width: 90%;
	height: 100%;
}

.content {
	position: relative;
	padding-right: 10px;
	z-index: 3;
}

#greet {
	z-index: 1;
	color: v-bind('color.font_greet');
	font-size: 1.2rem;
	padding-right: 5px;
	user-select: none;
}

#name {
	display: inline-block;

	color: v-bind('color.font_name');
	font-weight: 600;
	font-size: 3rem;
	text-transform: uppercase;
	-webkit-text-stroke-width: 1px;
	-webkit-text-stroke-color: rgba(0, 0, 0, 0.085);
	background-image:
		linear-gradient(-225deg,
			#ffffff64 0%,
			#8ce2dd91 29%,
			#6ea6c991 67%,
			#fff0f091 100%);
	background-size: auto auto;
	background-clip: border-box;
	background-size: 200% auto;
	background-clip: text;
	animation: textclip 4s linear infinite;

	z-index: 1;
	user-select: none;
	-webkit-background-clip: text;
	-webkit-text-fill-color: transparent;
}

@keyframes textclip {
	to {
		background-position: 200% center;
	}
}

#desc {
	z-index: 1;
	color: v-bind('color.font_desc');
	position: relative;
	width: min(90%, 400px);
	margin: auto;
	padding: 6px;
	background-color: v-bind('color.background_desc');
	border-radius: 20px 0 20px 20px;
	box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
}

#desc::after {
	content: "";
	position: absolute;
	width: 0;
	height: 0;
	left: auto;
	right: 0;
	bottom: 0;
	top: -20px;
	border: 10px solid;
	border-color: v-bind('color.background');
	border-radius: 0 0px 80% 0;

}

#desc::before {
	content: "";
	position: absolute;
	width: 0;
	height: 0;
	left: auto;
	right: 0;
	bottom: 0;
	top: -20px;
	border: 10px solid;
	border-color: v-bind('color.background_desc');
}

#handIcon {
	position: absolute;
	bottom: 0;
	left: 0;
	height: auto;
	width: 260px;
	opacity: 20%;
	rotate: -20deg;
	transition: rotate 100ms;
}

#handIcon:hover{
	rotate: -35deg;
}

.img-wrapper img {
	max-height: 200px;
	height: 37vw;
	width: auto;

	position: relative;
	left: -60px;
	z-index: 1;
	opacity: 80%;
}

/*---- CURVE BOTTOM ----*/
.curve-bottom {
	position: absolute;
	bottom: 0;
	left: 0;
	width: 100%;
	overflow: hidden;
	line-height: 0;
	transform: rotate(180deg);
}

.curve-bottom svg {
	position: relative;
	display: block;
	width: calc(153% + 1.3px);
	height: 76px;
}

.curve-bottom .shape-fill {
	fill: v-bind('color.background_next');
}


@media (max-width: 1024px) {
	.cover-wrapper {
		flex-direction: column;
		gap: 30px;
	}

	.img-wrapper img {
		position: static;
		min-height: 120px;
	}
}


@media (max-width: 493px),
(max-height: 600px) {
	#name {
		display: block;
		letter-spacing: -1px;
	}

	#desc {
		font-size: 0.95rem;
	}
}

/*----  ----*/
</style>
<template>
	<div id="About" class="about-section">
		<div class="my-profile">
			<div class="title-container">
				<span id="title">ABOUT ME</span>
			</div>
			<div class="detail-container">
				<span>Ever since I was a child, I've always been fascinated by how computer works. It's truly a dream come
					true to now pursue a career in programming, where I can channel my passion. When I'm not coding, I enjoy
					playing instruments like guitar and piano in my free time, and though I don't game as much as I did
					in high school, I still have fun playing with friends every now and then.
				</span>
			</div>
		</div>
		<div class="mySkill-container">
			<div class="skillTitle-container">
				<span class="skillTitle">MY SKILL</span>
			</div>
			<div class="mySkill-wrapper">
				<ul v-for="(skills, category) in mySkill" :key="category" class="category-container">
					<li id="category-title">{{ category }}</li>
					<ul>
						<li v-for="skill in skills" :key="skill">{{ skill }}</li>
					</ul>
				</ul>
			</div>
		</div>
		<div class="myLanguage-container">
			<div class="myLanguage-wrapper">
				<span>I'm fluent in both Indonesian and Sundanese, and I can also comfortably converse in English and Japanese.</span>
			</div>
		</div>
	</div>
</template>

<script setup>
const mySkill = {
	frontend: ['Vue', 'Laravel', 'Vanilla Css','Bootstrap' ],
	backend: ['Javascript', 'NodeJs', 'Express', 'Lumen', 'NGINX', 'MySQL', 'MongoDB'],
	tools: ['VSCode','Git', 'Docker', 'Figma'],
}

const color = {
	background: "#FFF2F2",
	background_title: "#cbd5d6",
	background_desc: "#d8e0e0",
	font_title: "#8699b1",
	font_desc: "#748395",
	font_skill: "#868686",
};
</script>

<style scoped>
/* 
	display: grid;
	place-items: center;
*/
.about-section {
	width: min(80%, 900px);
	margin: auto;
	padding-top: 15dvh;
	padding-bottom: 20dvh;
}

/*=========== My-profile ===========*/
.title-container,
.skillTitle-container {
	user-select: none;
	color: v-bind('color.font_title');
	box-shadow: 0px 10px v-bind('color.background_title') ;
	background-color: v-bind('color.background_title');
	font-size: 2rem;
	font-weight: 600;
	text-align: center;
	width: min(70%, 200px);
	height: 30px;
}

#title {
	position: relative;
	top: -20px;
}

.detail-container {
	color: v-bind('color.font_desc');
	background: v-bind('color.background_desc');
	border-radius: 0px 100px 0px 100px;
	border: 3px double #ffffff;
	padding: 20px;
	padding-left: 50px;
	margin: auto;
}

/*=========== My-Skill ===========*/
.mySkill-container {
	position: relative;
	width: 100%;
	display: flex;
	justify-content: flex-end;
}

.mySkill-wrapper {
	display: flex;
	width: min(70dvw, 800px);
}

.skillTitle-container {
	position: absolute;
	font-size: 1.5rem;
	width: min(70%, 110px);
	height: 10px;
	left: 2%;
	top: 30%;
}

.skillTitle {
	position: relative;
	top: -20px;
}

ul {
	margin: 0;
	flex-grow: 1;
	padding: 0;
	padding-top: 10px;
	padding-bottom: 10px;
	list-style-type: none;
}

.category-container:nth-child(odd) {
	border-left: 3px double #ffffff;
	border-right: 3px double #ffffff;
	background-color: v-bind('color.background_desc');
}


#category-title {
	color: v-bind('color.font_skill');
	text-decoration: underline;
}

li {
	text-align: center;
}

#category-title {
	text-transform: uppercase;
	font-weight: 600;
}

/*=========== My-Language ===========*/
.myLanguage-container{
	color: v-bind('color.font_desc');
	background: v-bind('color.background_desc');
	border-radius: 100px 0px  100px 0px;
	border: 3px double #ffffff;
	padding: 20px;
	padding-left: 50px;
	margin: auto;
	text-align: center;
}

.myLanguage-wrapper{
	margin: auto;
	width: min(100%, 600px);
}

@media (max-width:767px) {
	.mySkill-wrapper {
		display: block;
		width: 60dvw;
	}

	.category-container:nth-child(2) {
		border: 3px double #ffffff;
	}
}
</style>
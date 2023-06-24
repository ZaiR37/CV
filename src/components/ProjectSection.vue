<template>
	<div id="Projects" class="projects-section">
		<div class="title">
			<span>MY PROJECT</span>
		</div>
		<div class="projects-container">
			<div v-for="(project, index) in projects" :key="project.title" class="project-container">
				<h2 class="projectTitle">{{ project.title }}</h2>
				<div class="project-wrapper">
					<div class="desc-container">
						<p :class="{ 'descHidden': showProject != index + 1 }">{{ project.desc }}</p>
					</div>
					<transition>
						<div class="projectDetails-container" v-if="showProject == index + 1">
							<div class="tools-container">
								<strong>Tools: </strong>
								<span v-for="(tool, index) in project.tools" :key="tool">
									{{ tool }}<span v-if="index !== project.tools.length - 1">, </span>
								</span>
							</div>
							<div class="carousel" v-if="project.photos.length > 0">
								<div style="text-align: center; text-decoration:underline"><strong>Project Sample</strong>
								</div>
								<swiper :navigation="true" :spaceBetween="30" :modules="modules" :grab-cursor="true"
									:loop="true" class="mySwiper" :lazy-preload-prev-next="lazyPreload">
									<SwiperSlide v-for="photo in project.photos" :key="photo" lazy>
										<img :src="`src/assets/photos/${photo}`" :alt="`imageof${photo}`" loading="lazy">
									</SwiperSlide>
								</Swiper>
							</div>
							<div class="collabolator-container">
								<div id="collaboratorTitle"> Collaborator</div>
								<ul>
									<li v-for="contributor in project.contributor" :key="contributor.name">
										<div class="detail"><strong>{{ contributor.name }}</strong> <br> {{ contributor.role
										}}
										</div>
										<a :href="contributor.githubLink" target="_blank" id="github">
											<img src="../assets/github.svg" alt="githubIcon">
										</a>
									</li>
								</ul>
							</div>
							<div class="source-container">
								<a :href="project.source" target="_blank">Source</a>
							</div><br>
						</div>
						<div v-else>
						</div>
					</transition>
				</div>
				<transition>
					<button class="showMore" v-if="showProject != index + 1" @click="ShowMore(index)">SHOW MORE</button>
					<button class="showMore" v-else @click="HideMore()">HIDE</button>
				</transition>
			</div>
		</div>
	</div>
</template>

<script setup>
import { ref } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation } from 'swiper';
import "swiper/css";
import 'swiper/css/navigation';

let showProject = ref(0);

const modules = [Navigation];
const lazyPreload = 0;

const projects = [
	{
		title: 'Digital Library',
		desc: 'This project was developed as part of my final assignment for the Distributed Database course. It is a web application designed to simplify the book borrowing process for users and provide real-time availability information. It also includes a staff interface to facilitate book management tasks such as adding, deleting, and updating book status in the database.',
		photos: [
			'projectSample1(1).webp',
			'projectSample1(2).webp',
			'projectSample1(3).webp',
			'projectSample1(4).webp',
			'projectSample1(5).webp',
		],
		contributor: [
			{
				name: 'Lorem Ipsum',
				role: 'Backend',
				githubLink: 'https://github.com/ZaiR37'
			},
			{
				name: 'Naufal Fadhilah Alwan',
				role: 'Frontend',
				githubLink: 'https://github.com/minxs33'
			}
		],
		tools: ['Laravel', 'Lumen', 'Docker', 'NGINX', 'MariaDB', 'Bootstrap'],
		source: 'https://gitlab.com/ZaiR37/dot'
	}, {
		title: 'Smart Digital Library',
		desc: 'This project was developed as part of my final assignment for the Internet of Things course. It shares similarities with my previous project, but with a focus solely on the staff functionality. One notable addition is the ability to scan card IDs using Arduino, which retrieves the corresponding book IDs and searches the database for its information.',
		photos: [
			'projectSample2(1).webp',
			'projectSample2(2).webp',
			'projectSample2(3).webp',
			'projectSample2(4).webp',
		],
		contributor: [
			{
				name: 'Lorem Ipsum',
				role: 'Backend',
				githubLink: 'https://github.com/ZaiR37/'
			},
			{
				name: 'Naufal Fadhilah Alwan',
				role: 'Frontend',
				githubLink: 'https://github.com/minxs33/'
			}
		],
		tools: ['NodeJs', 'Express', 'MariaDB', 'Bootstrap'],
		source: 'https://github.com/ZaiR37/Library-IOT'
	}, {
		title: 'Portofolio Website',
		desc: 'This project is the web that you are currently viewing, it serves as a demonstration of my skills in Vue.js frontend web programming. I developed it with the intention of showcasing my abilities to potential internship employers, providing them with a glimpse into my capabilities and previous projects.',
		photos: [],
		contributor: [
			{
				name: 'Lorem Ipsum',
				role: 'Frontend',
				githubLink: 'https://github.com/ZaiR37/'
			},
		],
		tools: ['NodeJs', 'NGINX', 'Vue', 'Vanilla CSS'],
		source: 'https://github.com/example/'
	},

]
const color = {
	projectContainer: '#d8e0e0',
	title_background: '#d8e0e0',
	project_wrapper: '#e5eeee',
	swiper_slide: '#fff'
}

function ShowMore(index) {
	this.showProject = index + 1;
}

function HideMore() {
	this.showProject = 0;
}

</script>

<style scoped>
.projects-section {
	width: min(90%, 900px);
	margin: auto;
	padding-top: 1dvh;
	padding-bottom: 10dvh;
}

.title {
	background: v-bind('color.title_background');
	font-size: 2rem;
	font-weight: 600;
	margin: auto;
	text-align: center;
	height: 10px;
	width: 230px;
	user-select: none;
}

.title span {
	position: relative;
	top: -30px;
}

.projects-container {
	width: min(100%, 800px);
	margin: auto;
	transition: height 100ms;
}

/*=========== Project-Container ===========*/
.project-container {
	position: relative;
	margin: 20px;
	padding: 20px;
	background: v-bind('color.projectContainer');
	border: 3px double #ffffff;
}

.project-container:nth-child(1) {
	position: relative;
	border-radius: 100px 100px 0px 100px;
}

.project-container:nth-child(1)::before,
.project-container:nth-child(2)::before {
	position: absolute;
	content: "";
	color: v-bind('color.projectContainer');
	right: 0;
	left: 80%;
	bottom: -23px;
	border: 10px solid;
}

.project-container:nth-child(2)::before {
	right: 80%;
	left: 0;
}

.project-container:nth-child(2) {
	position: relative;
	border-radius: 100px 0px 100px 0px;
}

.project-container:nth-child(3) {
	border-radius: 0 100px 100px 100px;
}

.project-container h2 {
	text-align: center;
	text-transform: capitalize;
	user-select: none;
}

.project-container p {
	text-indent: 50px;
}

.project-container ul {
	padding: 0;
	padding-top: 10px;
	display: flex;
	margin: auto;
	flex-wrap: wrap;
}

.project-container li,
.project-container li a {
	padding: 0;
	display: flex;
}

.project-container li {
	margin: auto;
	margin-bottom: 10px;
}

.project-wrapper{
	background: v-bind('color.project_wrapper');
	border-radius: 30px 30px 30px 30px;
	overflow: hidden;
}

/*=========== Project-Title ===========*/
.projectTitle {
	position: relative;
	width: fit-content;
	margin: auto;
	margin-top: 10px;
	margin-bottom: 10px;
}

.projectTitle::before {
	content: "";
	position: absolute;
	top: 85%;
	width: 100%;
	left: 0;
	height: 5px;
	border-radius: 10px;
	background:
		linear-gradient(to left, rgba(178, 255, 255, 0.253), rgba(71, 113, 113, 0.229));
}

/*=========== Description ===========*/
.desc-container {
	padding: 10px 20px 10px 20px;
}

.descHidden {
	overflow: hidden;
	text-overflow: ellipsis;
	display: -webkit-box;
	-webkit-line-clamp: 3;
	-webkit-box-orient: vertical;
}

/*=========== Tools ===========*/
.tools-container {
	position: relative;
	padding: 0 20px 0 20px;
	margin-bottom: 30px;
}


/*=========== Carousel ===========*/
.carousel {
	margin-bottom: 30px;

}

.swiper {
	width: min(100%, 400px);
	height: min(100%, 400px);
}

.swiper-slide {
	text-align: center;
	font-size: 18px;
	background: #fff;

	display: flex;
	justify-content: center;
	align-items: center;
}

.swiper-slide img {
	border: solid;
	display: block;
	width: 100%;
	height: 100%;
	margin: auto;
	object-fit: cover;
}

/*=========== Collabolator ===========*/

#collaboratorTitle {
	margin-top: 10px;
	text-align: center;
	font-weight: 600;
	text-decoration: underline;
}

#github img {
	padding-left: 10px;
	width: 30px;
	height: auto;
	opacity: 60%;
	transition: transform 100ms;
}

#github:hover img {
	opacity: 50%;
	transform: scale(1.2);
}

/*=========== Source LINK ===========*/
.project-container .source-container {
	margin: 10px;
	text-align: center;
}

a {
	color: #7e7e7e;
	font-weight: 600;
	font-size: 1.3rem;
	text-decoration: none;
}

a:hover {
	color: #999999;
}

a:active {
	color: #afafaf;
}

/*=========== Hide & Show Button ===========*/
.showMore {
	background: linear-gradient(to bottom, transparent, #b6b5b565);
	display: block;
	background-color: transparent;
	border: none;
	border-radius: 50%;
	color: #858585;
	font-size: 1.2rem;
	font-weight: 600;
	text-align: center;
	margin: auto;
	margin-top: 12px;
}

.showMore:hover {
	text-shadow: 0px 2px 2px #b5cbea;
	color: #a1a1a1;
}

/*=========== Transition ===========*/
.v-enter-active,
.v-leave-active {
	transition: opacity 0.2s ease;
}

.v-enter-from,
.v-leave-to {
	opacity: 0;
}
</style>
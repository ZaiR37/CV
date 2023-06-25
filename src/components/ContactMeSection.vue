<template>
	<div id="Contact" class="contact-container">
		<div class="curvedivider curveTop">
			<svg data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none">
				<path
					d="M321.39,56.44c58-10.79,114.16-30.13,172-41.86,82.39-16.72,168.19-17.73,250.45-.39C823.78,31,906.67,72,985.66,92.83c70.05,18.48,146.53,26.09,214.34,3V0H0V27.35A600.21,600.21,0,0,0,321.39,56.44Z"
					class="shape-fill"></path>
			</svg>
		</div>
		<div class="contact-wrapper">
			<div class="image-container">
				<img src="../assets/mail.svg" alt="mailImg">
			</div>
			<div class="form-container">
				<div class="mainTitle-container">
					<h2>CONTACT ME</h2>
				</div>
				<div class="container">
					<form @submit.prevent="submitForm">
						<label for="userName">Name:</label>
						<input type="text" id="userName" v-model="userName" placeholder="Your Name.." required>
						<label for="userEmail">Email:</label>
						<input type="email" id="userEmail" v-model="userEmail" placeholder="Your Email.." required>
						<label for="userMessage">Message:</label>
						<textarea v-model="userMessage" id="userMessage" name="userMessage" placeholder="Write something.."
							style="height:200px" required>
						</textarea>
						<div class="button-container">
							<button :disabled="formButton" :class="{
								'buttonSuccess': formStatus === 'Success',
								'buttonFailed': formStatus === 'Error'
							}">{{ formStatus }}
							</button>
						</div>
					</form>
				</div>
			</div>
		</div>
		<div class="curvedivider curveBottom">
			<svg data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none">
				<path
					d="M0,0V46.29c47.79,22.2,103.59,32.17,158,28,70.36-5.37,136.33-33.31,206.8-37.5C438.64,32.43,512.34,53.67,583,72.05c69.27,18,138.3,24.88,209.4,13.08,36.15-6,69.85-17.84,104.45-29.34C989.49,25,1113-14.29,1200,52.47V0Z"
					opacity=".25" class="shape-fill"></path>
				<path
					d="M0,0V15.81C13,36.92,27.64,56.86,47.69,72.05,99.41,111.27,165,111,224.58,91.58c31.15-10.15,60.09-26.07,89.67-39.8,40.92-19,84.73-46,130.83-49.67,36.26-2.85,70.9,9.42,98.6,31.56,31.77,25.39,62.32,62,103.63,73,40.44,10.79,81.35-6.69,119.13-24.28s75.16-39,116.92-43.05c59.73-5.85,113.28,22.88,168.9,38.84,30.2,8.66,59,6.17,87.09-7.5,22.43-10.89,48-26.93,60.65-49.24V0Z"
					opacity=".5" class="shape-fill"></path>
				<path
					d="M0,0V5.63C149.93,59,314.09,71.32,475.83,42.57c43-7.64,84.23-20.12,127.61-26.46,59-8.63,112.48,12.24,165.56,35.4C827.93,77.22,886,95.24,951.2,90c86.53-7,172.46-45.71,248.8-84.81V0Z"
					class="shape-fill"></path>
			</svg>
		</div>
	</div>
</template>

<script setup>
import { ref } from 'vue';
import axios from 'axios'

let userName = '';
let userEmail = '';
let userMessage = '';

const formStatus = ref('Send');
const formButton = ref(false);

function submitForm() {
	console.log("Submiting Form...");
	buttonSending();

	const formData = {
		name: userName,
		email: userEmail,
		msg: userMessage
	}

	axios.post("https://formspree.io/f/xgejwvnr", formData)
		.then(response => {
			if (response.data.ok) {
				console.log("Form Submitted!");
				buttonSuccess();
			}
			else {
				throw new Error("Request was not successful!");
			}
		}
		)
		.catch(error => {
			buttonFailed();
			console.error("There was an error!", error);
		});
}

function buttonSending() {
	formStatus.value = 'Sending..'
	formButton.value = true;
}

function buttonSuccess() {
	formStatus.value = 'Success';
}

function buttonFailed() {
	formStatus.value = 'Error';
}

</script>

<style scoped>
.contact-container {
	position: relative;
	background: #b2c1c2;
	padding-top: 100px;
	padding-bottom: 150px;
	overflow: hidden;
}

.contact-wrapper {
	display: flex;
	flex-wrap: wrap;
	width: min(80%, 1100px);
	margin: auto;
	margin-top: 5dvh;
}

.image-container {
	display: flex;
	flex-grow: 1;
	margin: auto;
	width: min(100%, 300px);
}

.image-container img {
	position: relative;
	margin: auto;
	height: auto;
	width: min(100%, 350px);
}

.form-container {
	flex-grow: 1;
	padding: 30px;
	padding-bottom: 40px;
	margin: auto;
	background: linear-gradient(to bottom, #eef1f9, #f1f6f6);
	border-radius: 20px;
}

.mainTitle-container {
	height: 13px;
	width: fit-content;
	margin: auto;
	background: #d8e0e0;
	text-align: center;
}

.mainTitle-container h2 {
	position: relative;
	top: -20px;
}

.form-container .container {
	display: flex;
	flex-direction: column;
}

.form-container form label {
	color: #626262;
	font-weight: 600;
}

.form-container form input,
textarea[name=userMessage] {
	display: block;
	font-family: "Poppins", sans-serif;
	font-size: 1.1rem;
	height: 35px;
	width: 100%;
	margin-bottom: 10px;
	border-radius: 10px;
	outline: none;
	border: #e8e8e8 solid;
}

.form-container form input:focus,
textarea[name=userMessage]:focus {
	border: solid #9c9c9c;
}

textarea[name=userMessage] {
	font-size: 1rem;
	resize: none;
}

.form-container form .button-container {
	display: flex;
}

.form-container form button {
	background: white;
	color: #626262;
	font-size: 1.2rem;
	font-weight: 600;
	margin: auto;
	margin-top: 10px;
	padding: 5px;
	width: 150px;
	border: solid rgb(212, 212, 212);
	border-radius: 10px;
}

.form-container form button:disabled {
	background: rgb(224, 224, 224);
	border: solid rgb(217, 216, 135);
}

.form-container form .buttonSuccess:disabled {
	background: rgb(204, 219, 241);
	border: solid rgb(119, 156, 207);
}

.form-container form .buttonFailed:disabled {
	background: rgb(241, 204, 204);
	border: solid rgb(207, 119, 119);
}

@media (max-width: 900px) {
	.image-container img {
		left: 50px;
	}

	.contact-wrapper {
		display: block;
		width: 90%;
	}

	.form-container {
		margin-top: 40px;
		width: 80%;
	}
}


/* CURVE DIVIDER */
.curvedivider {
	position: absolute;
	left: 0;
	width: 100%;
	overflow: hidden;
	line-height: 0;
}

.curvedivider svg {
	position: relative;
	display: block;
	width: calc(147% + 1.3px);
	height: 64px;
}

.curveTop {
	top: 0;
}

.curveBottom {
	bottom: 0;
	transform: rotate(180deg);
}

.curvedivider .shape-fill {
	fill: #f1f6f6;
}
</style>
<template>
	<div class="hello">
		<h1>{{ msg }}</h1>
		<ul>
			<li>
				<a href="#" @click.prevent="getStory">Next Story</a>
			</li>
		</ul>
		<div class="letter">
			<div v-if="!is_loading" style="line-height: 1.3; line-spacing: 2;" v-html="story"></div>
			<div v-else>
				<img
					src="https://i.pinimg.com/originals/f6/65/6a/f6656aa6fdb6b8f905dea0bcc2d71dd8.gif"
					alt="loading"
					width="125px"
					style="margin-top: 125px;"
				/>
			</div>
		</div>
	</div>
</template>

<script>
import axios from "axios";
export default {
	name: "Story",
	props: {
		msg: String,
	},
	data() {
		return {
			story: "",
			api_url: "http://api.fdci.se/cerpen",
			api_proxy: "https://cors-anywhere.herokuapp.com/",
			is_loading: false,
			is_error: false,
		};
	},
	mounted() {
		this.getStory();
	},
	methods: {
		async getStory() {
			this.is_loading = true;
			this.is_error = false;
			try {
				let response = await axios.post(
					`${this.api_proxy}${this.api_url}`
				);
				this.story = response.data
					.split('"')[1]
					.replace(new RegExp("\\\\n", "g"), "<br>");
				if (this.story == "viewport") {
					this.story =
						'<p style="margin-top: 150px;"><strong>Server Error, Coba Lagi</strong></p>';
				}
			} catch (e) {
				this.is_error = true;
				this.story =
					'<p style="margin-top: 150px;"><strong>Server Error, Coba Lagi</strong></p>';
			}

			this.is_loading = false;
		},
	},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url(https://fonts.googleapis.com/css?family=Indie+Flower);
h3 {
	margin: 40px 0 0;
}
ul {
	list-style-type: none;
	padding: 0;
}
li {
	display: inline-block;
	margin: 0 10px;
}
a {
	color: #42b983;
}
body {
	background: linear-gradient(#ccc, #fff);
	font: 14px sans-serif;
	padding: 20px;
}
.letter {
	background: #fff;
	box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
	margin: 26px auto 0;
	max-width: 550px;
	min-height: 300px;
	padding: 24px;
	position: relative;
	width: 80%;
}
.letter:before,
.letter:after {
	content: "";
	height: 98%;
	position: absolute;
	width: 100%;
	z-index: -1;
}
.letter:before {
	background: #fafafa;
	box-shadow: 0 0 8px rgba(0, 0, 0, 0.2);
	left: -5px;
	top: 4px;
	transform: rotate(-2.5deg);
}
.letter:after {
	background: #f6f6f6;
	box-shadow: 0 0 3px rgba(0, 0, 0, 0.2);
	right: -3px;
	top: 1px;
	transform: rotate(1.4deg);
}
</style>

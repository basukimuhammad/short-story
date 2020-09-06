<template>
	<div class="hello">
		<h1>{{ msg }}</h1>
		<ul>
			<li>
				<a href="#">Next Story</a>
			</li>
			<li>
				<a href="#">Share Story</a>
			</li>
		</ul>
		<div class="letter">
			<h3>Dear Friends,</h3>
			<div style="line-height: 1.3; line-spacing: 2;">
				Lorem ipsum, dolor sit amet consectetur adipisicing elit. Temporibus sunt quasi nisi, velit aperiam non laborum explicabo debitis et provident ea earum dolorum, officiis commodi tempora rerum reprehenderit! Quisquam, iure?
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "HelloWorld",
	props: {
		msg: String,
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

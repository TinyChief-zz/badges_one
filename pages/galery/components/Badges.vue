<template>
	<div class="section-content">
		<v-expansion-panel class="filter-wrapper">
			<v-expansion-panel-content>
				<div slot="header" class="filter-title">Отфильтруйте значки по форме, типу, году.</div>
				<div class="filter">
					<v-flex class="types">
						<h3 class="filter-title">Выберите тип:</h3>
						<v-checkbox class="choose-type" label="Cтуденческие отряды" v-model="types_in" value="ССО"></v-checkbox>
						<v-checkbox class="choose-type" label="Спортивные" v-model="types_in" value="спорт"></v-checkbox>
						<v-checkbox class="choose-type" label="Фестивали, форумы" v-model="types_in" value="фестивали"></v-checkbox>
						<v-checkbox class="choose-type" label="Прочие" v-model="types_in" value="прочие"></v-checkbox>
					</v-flex>
					<v-flex class="forms">
						<h3 class="filter-title">Выберите форму:</h3>
						<v-checkbox label="Круглые" v-model="forms_in" value="круглый"></v-checkbox>
						<v-checkbox label="Прямоугольные" v-model="forms_in" value="прямоугольный"></v-checkbox>
						<v-checkbox label="Разные" v-model="forms_in" value="разный"></v-checkbox>
					</v-flex>
					<v-flex class="years">
						<h3 class="filter-title">Выберите год:</h3>
						<v-text-field
						label="С"
						v-model="y1_in"
						required
						class="choose-year"
						></v-text-field>
						<v-text-field
						label="До"
						v-model="y2_in"
						required
						class="choose-year"
						></v-text-field>
					</v-flex>
					<v-flex class="buttons">
						<v-btn class="choose-all-btn" block light v-on:click="chooseAll">
							Выбрать все
						</v-btn>
						<v-btn class="filter-btn" block light v-on:click="filter">
							Фильтр
						</v-btn>
					</v-flex>
				</div>
			</v-expansion-panel-content>
		</v-expansion-panel>
		
		
		<div class="badges">
			<div class="badge" v-for="badge in badges" v-if="showBadge(badge)">
				<div class="badge-photo" :style="{backgroundImage: 'url(' + badge.url + ')'}">
				</div>
				<h3 class="badge-title">
					{{ badge.title }}
				</h3>
				<p class="badge-text">
					{{ badge.text }}
				</p>
			</div>
		</div>
	</div>
	
</template>

<script>
export default {
	data () {
		return {
			y1_in: 1940,
			y2_in: 2018,
			types_in: ["ССО","спорт","фестивали", "прочие"],
			forms_in: ["круглый", "прямоугольный", "разный"],
			y1_f: 1940,
			y2_f: 2018,
			types_f: ["ССО","спорт","фестивали", "прочие"],
			forms_f: ["круглый", "прямоугольный", "разный"],
			badges: [
			{
				title: "Значок ГТО",
				form: "круглый",
				year: 1980,
				type: "спорт",
				text: 'Выдается за сдачу экзамена "Готов к труду и обороне!"',
				url: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRr8RqBf9n-YP9-Xf0JW3rL6jRy8BCCJxq7IP8fa2M9DDIK9IQVmQ"
			},
			{
				title: "Знаменка 2017",
				form: "разный",
				year: 2017,
				type: "ССО",
				text: 'Ежегодный фестиваль отрядной песни.',
				url: "https://meshok.net/pics/cache/73992646.208x208.jpg"
			},
			{
				title: "Кирпич 2010",
				form: "прямоугольный",
				year: 2010,
				type: "ССО",
				text: 'Всероссийский студенческий отряд 2010.',
				url: "https://meshok.net/pics/35489943.jpg"
			},
			{
				title: "Кирпич 2011",
				form: "прямоугольный",
				year: 2011,
				type: "ССО",
				text: 'Имени 50-летия полета Ю.Гагарина.',
				url: "https://pp.userapi.com/c630729/v630729098/34aeb/ibOLZg782JM.jpg"
			},
			{
				title: "Значок ГТО",
				form: "круглый",
				year: 1980,
				type: "спорт",
				text: 'Выдается за сдачу экзамена "Готов к труду и обороне!"',
				url: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRr8RqBf9n-YP9-Xf0JW3rL6jRy8BCCJxq7IP8fa2M9DDIK9IQVmQ"
			},
			{
				title: "Знаменка 2017",
				form: "разный",
				year: 2017,
				type: "ССО",
				text: 'Ежегодный фестиваль отрядной песни.',
				url: "https://meshok.net/pics/cache/73992646.208x208.jpg"
			},
			{
				title: "Кирпич 2010",
				form: "прямоугольный",
				year: 2010,
				type: "ССО",
				text: 'Всероссийский студенческий отряд 2010.',
				url: "https://meshok.net/pics/35489943.jpg"
			},
			{
				title: "Кирпич 2011",
				form: "прямоугольный",
				year: 2011,
				type: "ССО",
				text: 'Имени 50-летия полета Ю.Гагарина.',
				url: "https://pp.userapi.com/c630729/v630729098/34aeb/ibOLZg782JM.jpg"
			}
			]
		}
	},
	methods: {
		showBadge: function (el) {
			if (this.forms_f.includes(el.form) && this.types_f.includes(el.type) && el.year >= this.y1_f && el.year <= this.y2_f) {
				return true
			} else {
				return false
			}
		},
		filter: function () {
			this.y1_f = this.y1_in;
			this.y2_f = this.y2_in;
			this.forms_f = this.forms_in;
			this.types_f = this.types_in
		},
		chooseAll: function () {
			this.y1_in = 1940;
			this.y2_in = 2018;
			this.types_in = ["ССО","спорт","фестивали", "прочие"];
			this.forms_in = ["круглый", "прямоугольный", "разный"];
		}
	},
	computed: {
		
	}
}
</script>

<style>
.badges{
	display: flex;
	flex-wrap: wrap;
	justify-content: space-around;
}
.badge {
	padding: 10px;
	margin: 0 0 20px 0;
	width: 240px;
	display: flex;
	justify-content: flex-start;
	flex-flow: column;
	/*align-items: flex-start;*/
	background: #F8FAFF;
	border: 1px solid transparent;
	border-radius: 15px;
	transition: 0.2s border ease-in-out;
}
.badge:hover {
	border: 1px solid #6a60a9;
}
.badge-photo {
	position: relative;
	height: 160px;
	background-position: center center;
	background-size: contain;
	background-repeat: no-repeat;
	box-shadow: inset 0px 0px 14px 0px rgba(0,0,0,0.5);
	margin-bottom: 10px;
	border-radius: 10px;
	overflow: hidden;
}
.badge-photo::after {
	content: "";
	position: absolute;
	width: 100%;
	height: 100%;
	background: rgba(0, 0, 0, 0.15);
	transition: 0.2s background ease-in;
}
.badge:hover .badge-photo::after{
	background: none;
}

.badge-title {
	text-align: center;
	margin-bottom: 10px;
}
.filter{
	width: 100%;
	background: #ccc;
	display: flex;
	flex-wrap: wrap;
	justify-content: space-between;
	align-items: flex-start;
	padding: 10px;
	padding-bottom: 0;
}
.types, .forms{
	display: flex;
	flex-wrap: wrap;
	flex-flow: column;
	margin-bottom: 10px;
	min-width: 200px;
}
.years {
	margin-bottom: 20px;
	max-width: 150px;
}
.choose-year::after {
	content: "";
	width: 100%;
	height: 1px;
	background-color: #000ccc;
}
.buttons {
	min-width: 100%;
	display: flex;
	margin-bottom: 10px;
}
.buttons button {
	margin: 0 10px;
}
.choose-all-btn {
	background-color: #a6172d;
	color: #fafafa;
	font-weight: bold;
}
.filter-btn {
	background-color: #08182b;
	color: #fafafa;
	font-weight: bold;
	flex-basis: 40%;
}
.filter-wrapper {
	background-color: #ccc;
	margin-bottom: 30px;
}
.filter-title {
	font-size: 20px;
	font-weight: bold;
}
</style>
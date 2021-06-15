<template>
	<div id="app">
		<div class="container pt-5">
			<h2>30 Common Irregular Verbs Application</h2>
		</div>
		<hr>
		<div class="container pt-5" id="app">
			<div class="row">
				<div class="row mb-3">
					<div>
						<div>
							<div class="verb-block">
								<p>
									<h4>{{rand1}}</h4>
								</p>
							</div>
							<div class="verb-block">
								<transition name="verb">
									<p v-if="verbVisibility">{{rand2}}</p> 
								</transition>
							</div>
							<div class="verb-block">
								<transition name="verb">
									 <p v-if="verbVisibility">{{rand3}}</p> 
								</transition>
							</div>
							<div class="verb-block">
							</div>
							<button class="btn btn-primary" @click="selectVerb()">Select a verb</button>
							<button class="btn btn-outline-success mr-3 button" v-on:click="verbVisibility = !verbVisibility">{{BtnText}}</button>
						
						</div>
					</div>
				</div>
				<div class="form-group">
					<label for="search">Write the past form</label>
					<input type="text" class="form-control" id="search" placeholder="verb.." v-model="search1">

					<p class="container pt-3">
						<button class="btn btn-primary" @click="checkVerb()">Check the past form</button>
					</p>
					<h2 class="container pt-3" :class="class1">{{PastCorrect}}</h2>

				</div>
				<div class="form-group">
					<label for="search">Write the participle</label>
					<input type="text" class="form-control" id="search" placeholder="verb.." v-model="search2">
					<p class="container pt-3">
						<button class="btn btn-primary" @click="checkParticiple()">Check the participle</button>
					</p>

					<h2 class="container pt-3" :class="class2">{{ParticipleCorrect }}</h2>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	const verb = (form1, form2, form3) =>
		({
			form1,
			form2,
			form3
		})


	const verbs = [

		verb('run', 'ran', 'run'),
		verb('do', 'did', 'done'),
		verb('buy', 'bought', 'bought'),
		verb('swim', 'swam', 'swum'),
		verb('read', 'read', 'read'),
		verb('think', 'thought', 'thought'),
		verb('feel', 'felt', 'felt'),
		verb('have', 'had', 'had'),
		verb('sleep', 'slept', 'slept'),
		verb('understand', 'understood', 'understood'),
		verb('begin', 'began', 'begun'),
		verb('give', 'gave', 'given'),
		verb('forgive', 'forgave', 'forgiven'),
		verb('sing', 'sang', 'sung'),
		verb('can', 'could', 'could'),
		verb('come', 'came', 'come'),
		verb('become', 'became', 'become'),
		verb('build', 'built', 'built'),
		verb('choose', 'chose', 'chosen'),
		verb('cost', 'cost', 'cost'),
		verb('make', 'made', 'made'),
		verb('say', 'said', 'said'),
		verb('leave', 'left', 'left'),
		verb('be', 'was/were', 'been'),
		verb('tell', 'told', 'told'),
		verb('find', 'found', 'found'),
		verb('break', 'broke', 'broken'),
		verb('bring', 'brought ', 'brought'),
		verb('stand', 'stood', 'stood'),
        verb('write', 'wrote', 'written')

	]

	export default {
		name: 'app',
		data() {
			return {
				verbs: verbs,
				verb: verbs[0],
				selectedVerbIndex: 0,
				verbVisibility: false,
				search1: '',
				search2: '',
				logs: [],
				rand1: '',
				class1: '',
				class2: '',
				PastCorrect: '',
				ParticipleCorrect: ''
			}
		},
		methods: {
			selectVerb() {
				this.rand = this.verbs[Math.floor(Math.random() * verbs.length)]
				this.rand1 = this.rand.form1
				this.rand2 = this.rand.form2
				this.rand3 = this.rand.form3
				this.PastCorrect = ''
				this.search1 = ''
				this.search2 = ''
				this.ParticipleCorrect = ''
			},
			checkVerb() {
				if (this.rand.form2 == this.search1) {
					this.PastCorrect = 'right !!!'
					this.class1 = 'right'
				} else {
					this.PastCorrect = 'try again !'
					this.class1 = 'wrong'
				}
			},

			checkParticiple() {
				if (this.rand.form3 == this.search2) {
					this.ParticipleCorrect = 'right !!!'
					this.class2 = 'right'
				} else {
					this.ParticipleCorrect = 'try again !'
					this.class2 = 'wrong'
				}
			},
		},
		computed: {
			BtnText() {
				return this.verbVisibility ? 'Hide forms' : 'Show forms'
			},
		}

	};
</script>

<style lang="scss">
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 20px;
		
		.right {
			color: aqua
		}

		.wrong {
			color: rgb(209, 32, 32)
		}
        .button{
			width: 120px
		}

		.verb-block {
			height: 36px;
		}


		.verb-enter-active,
		.verb-leave-active {
			transition: all .5s;
		}


		.verb-enter,
		.verb-leave-to {
			transform: translateX(50px);
			opacity: 0;
		}
	}
</style>
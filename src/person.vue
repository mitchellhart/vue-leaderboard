<template>
<ul class="wrapper">
	<li class="picture"><img class="profile" :src="profilePath" alt=""></li>
	<li class="name"> {{this.personName}}</li>
	<li class="sub" v-on:click="sub">-</li>
	<li class="add" v-on:click="add">+</li>
	<li class="completes">{{this.completes}}</li>
</ul>
</template>

<script type="text/javascript">

export default {
  name: 'person',
  data () {
    return {
    	completes: 0
    }
  },
  methods: {
  	add() {
  		this.completes ++
  		this.$emit('increment', this)
  	},
  	sub() {
  		this.completes --
  		this.$emit('deincrement')
  	}
  },
  props: ['personName', 'profile','id'],
  computed: {
  	profilePath(){
  		return require("./assets/" + this.profile )
  	}
  }
}

</script>

<style type="text/sass">

.wrapper {
	height: 150px;
	/*width: 90%;	*/
	overflow: hidden;
}

.rank {
	width: 10%;
	line-height: 150px;
}
.name {
	font-size: 40px;
	text-align: left;
	width: 20%;
	line-height: 150px;
	padding-right: 200px;
	padding-left: 50px;

}
.add, .sub {
	line-height: 150px;
	padding-left: 10px;
	cursor: pointer;
	user-select: none;
	font-size: 30px;
	width: 50px;
	
}
.completes {
	font-size: 40px;
	width: 20%;
	line-height: 150px;
	float: right;
}



li {
	display: inline;
	float: left;
}

.profile {
	height: 130px;
}
.picture {
	margin-top: 26px;
	border-radius: 50px;
	height: 100px;
	width: 100px;
	overflow: hidden;
}


</style>
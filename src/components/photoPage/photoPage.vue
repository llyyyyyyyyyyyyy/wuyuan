<template>
	<div id="photoPage">
		<photo-page :imgsArr="imgsArr"></photo-page>
	</div>
</template>
<script>
	import photoPage from "./photoWaterfall/vue-waterfall-easy.vue";
	import { mapGetters, mapActions } from 'vuex'
	export default{
		data(){
			return{
				imgsArr: [],
				fetchImgsArr: [],
				photoArr:[]
			}
		},
		computed: {
	        ...mapGetters(['photo'])
	    },
		components:{photoPage},
		methods: {
			back(){
				window.history.back();
			},

		    initImgsArr(n, m) { //num 图片数量
		      	var arr = []
		      	if (this.photo) {
		      		for (var i = 0; i < this.photo.length; i++) {
			        	arr.push({ src: this.photo[i].img +'-NewdeerFPs.ios'})
			      	}
		      	}
		      	console.log(arr)
		      	return arr
		    },
		  },
	  	created() {
	    	this.imgsArr = this.initImgsArr(0, 10)
	    	// this.fetchImgsArr = this.initImgsArr(10, 20) // 模拟每次请求的新的图片的数据数据
	  	},
	}
</script>
<style lang="css" src="./photoPage.css"></style>

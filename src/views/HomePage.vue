<template>
<div>

	<section>
		<div class="cardContainer">
			<div class="cardcharas">
				<img class="charaimg" alt="" srcset="../assets/home_girls.png"/>
			</div>
			<div class="btnContainer">
				<div class="cardbtn">
					<img class="btnimg" width="150" alt="" srcset="../assets/home_btn.png"/>
					<p class="cardcount">卡包内剩余10000张卡</p>
				</div>
			</div>
		</div>
    </section>

	<section>
      <div class="columns is-multiline is-mobile section2div">
        <div class="column is-4-desktop is-4-tablet is-12-mobile cardItem" v-for="item in itemIds" :key="item.id"
        @click="gotoCoinProfile(item.code)">
        	<img class="cardItemImg" alt="" :src="item.img"/>
        	<div :style="{ backgroundColor: item.color, height: '50px' }">
        		<span>
			        <a :style="{ lineHeight: '50px', color: item.textcolor, paddingLeft: '20px' }">{{ item.name }}{{ item.code }}</a>
			    </span>
			    <span class="priceSpan">
			        <a :style="{ lineHeight: '50px', color: item.textcolor }">= =USD</a>
			    </span>
        	</div>
        </div>
      </div>
    </section>

</div>
</template>

<script>
export default {
  name: 'HomePage',
  data: () => ({
    itemIds: []
  }),
  methods: {
    gotoCoinProfile(code) {
      this.$router.push({ path: `/coin/${code}` })
    }
  },
  mounted() {
    this.$http.get('static/girl_cards.json').then((response) => {
      this.itemIds = response.body;
    });
  }
};
</script>

<style scoped>
/*
  section 1
*/
.cardContainer {
	background-image: url("../assets/home_girls_bk.png");
	background-size: 100%;
	background-repeat: no-repeat;
	background-color: #fff;
	width: 100%;
	/*padding-top: 43.5%;*/
	padding-top: 50%;
	position: relative;
	text-align: center;
}
.cardcharas {
  position: absolute;
  top: 0;
  left: 0;
	width: 100%;
  /*@media (max-width: 800px) {
    text-align: center;
    padding-right: 0px;
  }*/
}
.charaimg{
  width: 80%;
    display: block;
    margin-left: auto;
    margin-right: auto;
}
.btnContainer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
	padding-top: 38%;
  /*background-color: #ccc;*/
}
.cardbtn {
    display: block;
    margin-left: auto;
    margin-right: auto;
}
.cardcount {
	color: #5495c6;
	font-size: 20px;
}

/*
  section 2
*/
.section2div {
	padding-right: 50px;
	padding-left: 50px;
	padding-top: 30px;
	padding-bottom: 50px;
}
.cardItemImg{
	vertical-align:bottom;
	cursor: pointer;
}
.priceSpan {
	float:right;
	padding-right: 20px;
}

@media (max-width: 800px) {
	.cardContainer {
		background-size: cover;
		padding-top: 60%;
	}
	.charaimg{
		width: 100%;
	}
	.btnContainer {
		padding-top: 50%;
	}

	.section2div {
		padding-top: 100px;
	}
	.cardItemImg{
		width: 100%;
	}
}
</style>


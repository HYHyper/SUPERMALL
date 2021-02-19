<template>
	<div class="goods-info" v-if="Object.keys(detailInfo).length !== 0">
		<div class="info-desc clear-fix">
			<div class="start"></div>
			<div class="desc">{{detailInfo.desc}}</div>
      <div class="end"></div>
		</div>
    <div class="info-key" v-for="(item,index) in detailInfo.detailImage" :key="index">
      <div class="desc">{{item.key}}</div>
      <div class="info-list">
        <img v-for="(item2, index) in item.list" :key="index" :src="item2" alt=""  @load="imgLoad">
      </div>
    </div>
  </div>

</template>

<script>

	export default {
		name: 'DetailGoodsInfo',
		props: {
			detailInfo: {
				type: Object,
				default() {
					return {}
				}
			}
		},
    methods:{
      imgLoad(){
        // console.log('ssss')
        this.$emit('detailImageLoad')
      }
    }
	}
</script>

<style scoped>
.info-desc{
  position: relative;
}
.start{
  width: 60px;
  height: 1px;
  background-color: #333;
  margin-left: 4px;
}
.start::before{
  position: absolute;
  left: 4px;
  top: -2.5px;
  display: block;
  content: '';
  width: 5px;
  height: 5px;
  background-color: #333;
}
.end{
  width: 60px;
  height: 1px;
  background-color: #333;
  position: absolute;
  right: 4px;
  bottom: 0;
}
.end::after{
  position: absolute;
  right: 0;
  top: -2.5px;
  display: block;
  content: '';
  width: 5px;
  height: 5px;
  background-color: #333;
}
.desc{
  font-size: 14px;
  padding-bottom: 6px;
  line-height: 20px;
  margin: 4px 0;
  text-indent: 10px;
}
.info-list img {
  width: 100%;
}
</style>

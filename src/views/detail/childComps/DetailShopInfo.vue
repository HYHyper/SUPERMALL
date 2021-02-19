<template>
  <div class="shop-info" v-if="Object.keys(shop).length !== 0">
    <div class="shop-top">
      <img :src="shop.logo" alt="">
      <span class="title">{{shop.name}}</span>
    </div>
    <div class="shop-middle">
      <div class="shop-middle-item shop-middle-left">
        <div class="info-sells">
          <div class="sells-count">
            {{shop.sells | sellCountFilter}}
          </div>
          <div class="sells-text">总销量</div>
        </div>
        <div class="info-goods">
          <div class="goods-count">
            {{shop.goodsCount}}
          </div>
          <div class="goods-text">全部宝贝</div>
        </div>
      </div>
      <div class="shop-middle-item shop-middle-right">
        <table>
          <tr v-for="(item,index) in shop.score" :key="index">
            <td>{{item.name}}</td>
            <td class="score"  :class="{active1:item.isBetter}">{{item.score}}</td>
            <td class="better" :class="{active2:item.isBetter}"><span>{{item.isBetter?  '高':'低' }}</span></td>
          </tr>
        </table>
      </div>
    </div>
    <div class="shop-bottom">
      <div class="enter-shop">进店逛逛</div>
    </div>
  </div>

</template>

<script>
export default {
  name: "DetailShopInfo",
  props:{
    shop:{
      type: Object,
      default(){
        return {}
      }
    }
  },
  filters:{
    sellCountFilter: function (value) {
      if(value < 10000) return value;
      return (value/10000).toFixed(1)+'万'
    }
  }
}
</script>

<style scoped>
.shop-info{
  padding: 25px 8px;
  border-bottom: 5px solid #f2f5f8;
}
.shop-top{
  line-height: 45px;
  display: flex;
  align-items: center;
  /*margin: 20px 10px;*/
}
.shop-top img{
  border-radius: 100%;
  width: 50px;
  height: 50px;
  margin-right: 10px;
  vertical-align: middle;
}
.shop-top .title{
  margin-left: 10px;
  vertical-align: center;
}
.shop-middle{
  margin-top: 15px;
  display: flex;
  align-items: center;
}
.shop-middle-item{
  flex: 1;
}
.shop-middle-left{
  display: flex;
  justify-content: space-evenly;
  color: #333;
  text-align: center;
  border-right: 1px solid #ececec;
}
.sells-count,.goods-count{
  font-size: 16px;
}
.sells-text,.goods-text{
  margin-top: 6px;
  padding: 2px 5px;
  font-size: 16px;
}
.shop-middle-right{
  font-size: 13px;
  color: #333;
}
.shop-middle-right table{
  width: 120px;
  margin-left: 30px;
}
.shop-middle-right table td{
  padding: 5px 0;
}
.shop-middle-right .score{
  color: #006666;
}
.shop-middle-right .active1{
  color: #880000;
}
.shop-middle-right .better span{
  background-color: #006666;
  color: #fff;
  text-align: center;
  padding: 1px 4px;
  font-size: 12px;
}
.shop-middle-right .active2 span{
  background-color: #880000;
}
.shop-bottom{
  text-align: center;
}
.enter-shop{
  display: inline-block;
  background-color: #f2f2f2;
  font-size: 12px;
  padding: 6px 30px;
  border-radius: 100px;
  margin: 10px;
}
</style>

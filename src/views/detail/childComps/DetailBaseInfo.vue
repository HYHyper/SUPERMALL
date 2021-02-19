<template>
  <div v-if="Object.keys(goods).length !== 0" class="base-info">
    <div class="info-title">{{goods.title}}</div>
    <div class="info-price">
      <div class="new-price">{{goods.newPrice}}</div>
      <div class="old-price">{{goods.oldPrice}}</div>
      <div class="discount" v-if="goods.discount">{{goods.discount}}</div>
    </div>
    <div class="info-other">
      <div>{{goods.columns[0]}}</div>
      <div>{{goods.columns[1]}}</div>
      <div>{{goods.services[goods.services.length-1].name}}</div>
    </div>
    <div class="info-serves">
      <div v-for="index in goods.services.length-1" :key="index">
        <img :src="goods.services[index-1].icon" alt="">
        {{goods.services[index-1].name}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailBaseInfo',
  props: {
    goods: {
      type: Object,
      default() {
        return {}
      }
    }
  }
}
</script>

<style scoped>
.base-info {
  margin: 10px 0;
  padding: 0 4px;
  font-size: 14px;
  line-height: 20px;
}
.info-price{
  display: flex;
  margin-top: 6px;
  padding: 0 4px 10px;
}
.info-price .new-price{
  font-size: 25px;
  color: var(--color-high-text);
}
.info-price .old-price{
  color: #999;
  font-size: 15px;
  margin: 0 4px;
  text-decoration: line-through;
}

.info-price .discount{
  color: #fff;
  font-size: 12px;
  border-radius: 100px;
  padding: 2px 6px;
  background-color: var(--color-high-text);
}

.info-other{
  display: flex;
  color: #999999;
  font-size: 12px;
  padding: 5px 4px;
  border-bottom: 1px solid #ededed;

}
.info-other div{
  flex: 1;
  margin-left: 25px;
}

.info-serves{
  display: flex;
  font-size: 12px;
  color: #333;
  padding: 10px 4px;
  justify-content: space-between;
  border-bottom: 4px solid #ededed;
}
.info-serves img{
  width: 12px;
  height: 12px;
  vertical-align: middle;
}

</style>

<template>
  <div>
    <swiper
      :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
    >
      <block v-for="img in imgUrls" :key="img">
        <swiper-item>
          <image :src="img" style="width:100%" />
        </swiper-item>
      </block>
    </swiper>
    <i-grid i-class="no-border">
    <i-grid-item @click="goType(grid)" v-for="grid in grids" :key="grid" i-class="no-border">
        <i-grid-icon>
            <image :src="grid.image" />
        </i-grid-icon>
        <i-grid-label>{{grid.title}}</i-grid-label>
    </i-grid-item>
  </i-grid>
  <i-panel :title="title_name">
    <view style="padding: 15px;">
      <i-card v-for="item in top" :key="item" i-class="split" :extra="item.name" :thumb="item.image">
          <view slot="content">{{item.remark}}</view>
          <view slot="footer">{{item.address}}</view>
      </i-card>
    </view>
  </i-panel>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title_name: "热门",
      grids: [
        {title:"中餐",image:"/static/images/1.png"},
        {title:"日韩料理",image:"/static/images/2.png"},
        {title:"西餐",image:"/static/images/3.png"},
        {title:"泰国菜",image:"/static/images/4.png"}
      ],
      top: [
        {name:"糖醋里脊",address:"口味：酸甜",image:"/static/images/z.jpg",remark:"主要食材：里脊肉，淀粉"},
        {name:"韩国炸鸡",address:"口味：甜辣",image:"/static/images/r.jpg",remark:"主要食材：鸡腿，甜辣酱"},
        {name:"意大利面",address:"口味：紧实而有弹性",image:"/static/images/x.jpg",remark:"主要食材：西红柿、洋葱、黄油、罗勒、黑胡椒、盐、意大利面、火腿、青椒"},
        {name:"冬阴功汤",address:"口味：酸酸辣辣香香甜甜，五味俱全",image:"/static/images/t.jpeg",remark:"主要食材：柠檬叶，香茅，辣椒，虾"}
      ],
      imgUrls: [
        '/static/images/c.jpg',
        '/static/images/b.jpg',
        '/static/images/a.jpg'
      ],
      indicatorDots: false,
      autoplay: false,
      interval: 5000,
      duration: 1000
    }
  },

  methods: {
    goType(type){
      console.log(type)
      let url = '../list/main?type=' + type.title
      mpvue.navigateTo({ url })
    }
  },

  created () {
  }
}
</script>

<style scoped>
div >>> .no-border{
  border-width: 0pt;
}
div >>> .split{
  margin-bottom: 10pt;
}
</style>

<template>
  <div>
    <!-- 轮播图 -->
    <swiper indicator-dots autoplay circular>
      <block v-for="item in swiperData" :key="item.id">
        <swiper-item>
          <!-- <image mode="aspectFill" :src="item.src"  @click="getdetail(item.id)"></image> -->
            <image mode="aspectFill" :src="item.src"  @click="getdetail(item.id)"></image>

        
        </swiper-item>
      </block>
    </swiper>
    <!-- 分类菜单 -->
    <div class="categories">
      <div class="category-item" v-for="item in catitems" :key="item.id">
        <img :src="item.src" alt="">
      </div>
    </div>
    <!-- 楼层数据 -->
    <div class="floor">
      <div class="floor-item" v-for="(item, index) in floordata" :key="index">
        <!-- 头部 -->
        <div class="floor_head">
          <img :src="item.src" alt="">
        </div>
        <div class="floor_body">
          <div class="floor_body_left">
            <img :src="item.src" alt="">
          </div>
          <div class="floor_body_right">
            <div v-for="(subitem, index1) in item.image" :key="index1">
              <img :src="subitem.src" alt="" class="floor_body_right_img">
            </div>
          </div>
        </div>
      </div>
    </div>
        <!-- 4.0 到底的提示 -->
        <div class="end-tips">
          <span class="iconfont icon-xiao"></span>
          <span class="bottomline">我是有底线的哦~</span>
        </div>
        <!-- 5.0 回到顶部 -->
        <div v-show="isShowToTop">
          <div @click="goToTop" class="to-top">
            <image src="/static/images/arrow_top@2x.png"/>
            <text>顶部</text>
          </div>
        </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        isShowToTop:false, // 是否显示回到顶部

        swiperData: [{
            src: 'https://gss0.baidu.com/-Po3dSag_xI4khGko9WTAnF6hhy/zhidao/pic/item/2e2eb9389b504fc2de49fce3e4dde71191ef6dc5.jpg',
            id: '1'
          },
          {
            src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924926038&di=5043cc6e794093cfad2fc63e654556e6&imgtype=0&src=http%3A%2F%2Fhbimg.b0.upaiyun.com%2Fef6043c0f407dac052c3b53b533274e30feb8b3e810f-dzocHu_fw658',
            id: '2'
          },
          {
            src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576925046466&di=e7681324b6e67945f1b3d63228993eb8&imgtype=0&src=http%3A%2F%2Fimage.hnol.net%2Fc%2F2016-06%2F07%2F09%2F201606070955255444-1988454.jpg',
            id: '3'
          },
          {
            src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924954350&di=cdbc3b5582b04b3d2dd2f7e0c6abba9d&imgtype=0&src=http%3A%2F%2Fpic1.win4000.com%2Fwallpaper%2Fb%2F588564e59d0b6.jpg',
            id: '4'
          },
          {
            src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576925046468&di=a9036eb70bbf80cb5d87f235f8ed7d5b&imgtype=0&src=http%3A%2F%2Fi0.hdslb.com%2Fbfs%2Farchive%2F839b48daee6bed189d49aa6eac912b353ce0db3d.jpg',
            id: '5'
          }
        ],
        catitems: [{ //分类菜单
            src: 'https://gss0.baidu.com/-Po3dSag_xI4khGko9WTAnF6hhy/zhidao/pic/item/2e2eb9389b504fc2de49fce3e4dde71191ef6dc5.jpg',
            id: '6'
          },
          {
            src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924926038&di=5043cc6e794093cfad2fc63e654556e6&imgtype=0&src=http%3A%2F%2Fhbimg.b0.upaiyun.com%2Fef6043c0f407dac052c3b53b533274e30feb8b3e810f-dzocHu_fw658',
            id: '7'
          },
          {
            src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576925046466&di=e7681324b6e67945f1b3d63228993eb8&imgtype=0&src=http%3A%2F%2Fimage.hnol.net%2Fc%2F2016-06%2F07%2F09%2F201606070955255444-1988454.jpg',
            id: '8'
          },
          {
            src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924954350&di=cdbc3b5582b04b3d2dd2f7e0c6abba9d&imgtype=0&src=http%3A%2F%2Fpic1.win4000.com%2Fwallpaper%2Fb%2F588564e59d0b6.jpg',
            id: '9'
          },
          {
            src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576925046468&di=a9036eb70bbf80cb5d87f235f8ed7d5b&imgtype=0&src=http%3A%2F%2Fi0.hdslb.com%2Fbfs%2Farchive%2F839b48daee6bed189d49aa6eac912b353ce0db3d.jpg',
            id: '10'
          }
        ],
        floordata: [{ //分类菜单
            src: 'https://gss0.baidu.com/-Po3dSag_xI4khGko9WTAnF6hhy/zhidao/pic/item/2e2eb9389b504fc2de49fce3e4dde71191ef6dc5.jpg',
            id: '11',
            image: [{ //分类菜单
                src: 'https://gss0.baidu.com/-Po3dSag_xI4khGko9WTAnF6hhy/zhidao/pic/item/2e2eb9389b504fc2de49fce3e4dde71191ef6dc5.jpg',
                id: '6'
              },
              {
                src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924926038&di=5043cc6e794093cfad2fc63e654556e6&imgtype=0&src=http%3A%2F%2Fhbimg.b0.upaiyun.com%2Fef6043c0f407dac052c3b53b533274e30feb8b3e810f-dzocHu_fw658',
                id: '7'
              },
              {
                src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576925046466&di=e7681324b6e67945f1b3d63228993eb8&imgtype=0&src=http%3A%2F%2Fimage.hnol.net%2Fc%2F2016-06%2F07%2F09%2F201606070955255444-1988454.jpg',
                id: '8'
              },
              {
                src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924954350&di=cdbc3b5582b04b3d2dd2f7e0c6abba9d&imgtype=0&src=http%3A%2F%2Fpic1.win4000.com%2Fwallpaper%2Fb%2F588564e59d0b6.jpg',
                id: '9'
              },

            ],
          },
          {
            src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924926038&di=5043cc6e794093cfad2fc63e654556e6&imgtype=0&src=http%3A%2F%2Fhbimg.b0.upaiyun.com%2Fef6043c0f407dac052c3b53b533274e30feb8b3e810f-dzocHu_fw658',
            id: '12',
            image: [{ //分类菜单
                src: 'https://gss0.baidu.com/-Po3dSag_xI4khGko9WTAnF6hhy/zhidao/pic/item/2e2eb9389b504fc2de49fce3e4dde71191ef6dc5.jpg',
                id: '6'
              },
              {
                src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924926038&di=5043cc6e794093cfad2fc63e654556e6&imgtype=0&src=http%3A%2F%2Fhbimg.b0.upaiyun.com%2Fef6043c0f407dac052c3b53b533274e30feb8b3e810f-dzocHu_fw658',
                id: '7'
              },
              {
                src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576925046466&di=e7681324b6e67945f1b3d63228993eb8&imgtype=0&src=http%3A%2F%2Fimage.hnol.net%2Fc%2F2016-06%2F07%2F09%2F201606070955255444-1988454.jpg',
                id: '8'
              },
              {
                src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924954350&di=cdbc3b5582b04b3d2dd2f7e0c6abba9d&imgtype=0&src=http%3A%2F%2Fpic1.win4000.com%2Fwallpaper%2Fb%2F588564e59d0b6.jpg',
                id: '9'
              },

            ],
          },
          {
            src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576925046466&di=e7681324b6e67945f1b3d63228993eb8&imgtype=0&src=http%3A%2F%2Fimage.hnol.net%2Fc%2F2016-06%2F07%2F09%2F201606070955255444-1988454.jpg',
            id: '13',
            image: [{ //分类菜单
                src: 'https://gss0.baidu.com/-Po3dSag_xI4khGko9WTAnF6hhy/zhidao/pic/item/2e2eb9389b504fc2de49fce3e4dde71191ef6dc5.jpg',
                id: '6'
              },
              {
                src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924926038&di=5043cc6e794093cfad2fc63e654556e6&imgtype=0&src=http%3A%2F%2Fhbimg.b0.upaiyun.com%2Fef6043c0f407dac052c3b53b533274e30feb8b3e810f-dzocHu_fw658',
                id: '7'
              },
              {
                src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576925046466&di=e7681324b6e67945f1b3d63228993eb8&imgtype=0&src=http%3A%2F%2Fimage.hnol.net%2Fc%2F2016-06%2F07%2F09%2F201606070955255444-1988454.jpg',
                id: '8'
              },
              {
                src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924954350&di=cdbc3b5582b04b3d2dd2f7e0c6abba9d&imgtype=0&src=http%3A%2F%2Fpic1.win4000.com%2Fwallpaper%2Fb%2F588564e59d0b6.jpg',
                id: '9'
              },

            ],
          },
          {
            src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924954350&di=cdbc3b5582b04b3d2dd2f7e0c6abba9d&imgtype=0&src=http%3A%2F%2Fpic1.win4000.com%2Fwallpaper%2Fb%2F588564e59d0b6.jpg',
            id: '14',
            image: [{ //分类菜单
                src: 'https://gss0.baidu.com/-Po3dSag_xI4khGko9WTAnF6hhy/zhidao/pic/item/2e2eb9389b504fc2de49fce3e4dde71191ef6dc5.jpg',
                id: '6'
              },
              {
                src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924926038&di=5043cc6e794093cfad2fc63e654556e6&imgtype=0&src=http%3A%2F%2Fhbimg.b0.upaiyun.com%2Fef6043c0f407dac052c3b53b533274e30feb8b3e810f-dzocHu_fw658',
                id: '7'
              },
              {
                src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576925046466&di=e7681324b6e67945f1b3d63228993eb8&imgtype=0&src=http%3A%2F%2Fimage.hnol.net%2Fc%2F2016-06%2F07%2F09%2F201606070955255444-1988454.jpg',
                id: '8'
              },
              {
                src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576924954350&di=cdbc3b5582b04b3d2dd2f7e0c6abba9d&imgtype=0&src=http%3A%2F%2Fpic1.win4000.com%2Fwallpaper%2Fb%2F588564e59d0b6.jpg',
                id: '9'
              },

            ],
          },

        ], //楼层数据

      }
    },
    onLoad() {
      console.log(11111111111111);
      this.getSwiper()
    },
    onPageScroll({scrollTop}){
    if (scrollTop > 80){
      if (this.isShowToTop) return
      this.isShowToTop = true
    } else {
      if (!this.isShowToTop) return
      this.isShowToTop = false
    }
  },
    methods: {
      // async getSwiper() {
      //   console.log(2222222);

      //   // const res = await this.$axios.get('........')
      // }
      getSwiper(){

      },
         // 回到顶部
    goToTop(){
      wx.pageScrollTo({
        scrollTop: 0,
        duration: 300
      })
    },
      getdetail(id){
        console.log(id);
        
const url=`../index/main?id=${id}`
wx.navigateTo({ url: url });
      },
    }
  }

</script>
<style lang="less" scoped>
  swiper {
    width: 750rpx;
    height: 400rpx;


  }

  swiper image {
    width: 100%;
    height: 100%;
  }

  .categories {
    display: flex;
    margin-top: 20rpx;
    margin-bottom: 20rpx;


  }

  .category-item {
    flex: 1;
    /* width:20%; */
    height: 100rpx;
    margin-right: 20rpx;


  }

  .category-item img {
    width: 100%;
    height: 100%;
    box-sizing: border-box;
    border-radius: 30rpx;
  }

  .floor-item {
    margin-top: 20rpx;
  }

  .floor_head {
    width: 100%;
    height: 100rpx;

  }

  img {
    width: 100%;
    height: 100%;
  }

  .floor_body {
    display: flex;


  }
  .floor_body_right {
      flex: 1;
      display: flex;
      flex-wrap: wrap;

    }
  .floor_body_right>div {
    width: 50%;
    height: 50%;

  }

  .floor_body_left {
    width: 300rpx;
    height: 400rpx;

  }
  .end-tips {
  display: flex;
  height: 100rpx;
  align-items: center;
  justify-content: center;
  font-size: 24rpx;
  color: #888;
  .bottomline {
    margin-left: 5rpx;
  }
}
.to-top {
  width: 90rpx;
  height: 90rpx;
  background: rgba(255, 255, 255, 0.8);
  border-radius: 50%;
  position: fixed;
  right: 40rpx;
  bottom: 50rpx;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  image {
    width: 24rpx;
    height: 14rpx;
  }
  text {
    margin-top: 20rpx;
    color: #999;
    font-size: small;
  }
}
</style>

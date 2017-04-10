<template>
  <div ref="home" class="home">
    <app-toTop class="toTop"></app-toTop>
    <app-header class="appHead"></app-header>
    <div class="content">
      <div class="homeBg">
        <a class="homeBgLink" href="http://swsy.duoyi.com/newcont/shenbing/"></a>
        <div class="downloadLinkBox">
          <a href="https://swappdl.duoyi.com/android/SwMobile2044_10199.apk?f=www">
            <img class="downloadAndroid" src="../assets/app_download_android.png" >
          </a>
          <a href="https://swsy.duoyi.com/i/">
            <img class="downloadMac" src="../assets/app_download_mac.png" >
          </a>
        </div>
      </div>
      <div class="news">
        <div class="slidePictureBox">
          <div class="slidePicture">
            <transition-group :name="animationName" mode="out-in">
              <v-touch
                class="pictures"
                v-for="picItem in Pictures"
                :key="picItem"
                v-show="picItem.show"
                @swipeleft="leftTip"
                @swiperight="rightTip"
              >
                <a :href="picItem.link">
                  <img class="picture" :src="picItem.imageUrl">
                </a>
              </v-touch>
            </transition-group>
            <div class="pointGroup">
              <v-touch
                class="point"
                v-for="pointItem in Pictures"
                key="pointItem"
                :style="{backgroundColor:pointItem.pointBgColor}"
                @tap="pointClick(pointItem)"
              ></v-touch>
            </div>
          </div>
        </div>
        <div class="slideNewsBox">
          <div class="slideNews">
            <div class="newsHeadBox">
              <div class="newTitleBox">
                <div class="newTitle" v-for="newTitleItem in News" :style="{backgroundColor:newTitleItem.bgColor}" @click="newsTitleClick(newTitleItem)" >
                  <p class="titleText" v-text="newTitleItem.name"></p>
                </div>
              </div>
              <a class="newsMore" :href="newsMore">more</a>
            </div>
            <div class="newsContentBox">
              <div class="newsPage" v-for="newContentItem in News"  v-show="newContentItem.contentShow">
                <a class="newBox" :href="contentItem.link" v-for="contentItem in newContentItem.content">
                  <p class="newContent" v-text="contentItem.text"></p>
                  <p class="newTime" v-text="contentItem.time"></p>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="features">
        <div class="featuresTitle">
          <img class="featuresTitleIcon" src="../assets/title_left.png">
          <p class="featuresTitleText">游戏特色</p>
          <img class="featuresTitleIcon" src="../assets/title_right.png">
        </div>
        <div class="featuresBox">
          <transition-group name="featuresL" mode="out-in">
            <div
              class="featureImageBox"
              :class="{imageLeft:imageItem.isLeft,imageRight:imageItem.isRight}"
              key="imageItem"
              v-for="imageItem in featuresImage"
              v-show="imageItem.show">
              <img
                class="featureImage"
                :class="{ ImageBig:select(imageItem) , ImageSmall:!select(imageItem)}"
                :src="imageItem.url">
            </div>
          </transition-group>
        </div>
      </div>
      <div class="gamePictures">
        <div class="gamePicTileBox">
          <img class="featuresTitleIcon" src="../assets/title_left.png">
          <p class="featuresTitleText">游戏截图</p>
          <img class="featuresTitleIcon" src="../assets/title_right.png">
        </div>
        <div class="gamePicBox">
          <div class="gamePics" v-for="gamePicsItem in gamePictures">
            <a class="gamePic" v-for="picItem in gamePicsItem.content" :href="picItem.href">
              <img class="pic" :src="picItem.url">
              <p class="picText" v-text="picItem.picText"></p>
            </a>
          </div>
        </div>
      </div>
    </div>
    <app-footer></app-footer>
  </div>
</template>
<script>
  import Header from '../components/header.vue';
  import Footer from '../components/footer.vue';
  import ScrollToTop from '../components/scrollListener.vue'
  var slideTime,reStartTime,zoomTime;
  export default{
    data(){
      return {
        className:['.home','.homeBg','.news'],
        slideIndex: 0,
        slideOk: true,
        animationName: 'slideL',
        Pictures: [
          {
            index: 0,
            show: true,
            imageUrl: window.baseUrl + 'com/180/pic/PL-8emqREi2fT.jpg',
            link: 'http://sw.duoyi.com/act/daiyan/xs/',
            pointBgColor: '#ffffff'
          },
          {
            index: 1,
            show: false,
            imageUrl: window.baseUrl + 'com/180/pic/PL-O4q5Zb9rXY.jpg',
            link: 'http://swsy.duoyi.com/news/swzz.shtm',
            pointBgColor: '#7d7d7d'
          },
          {
            index: 2,
            show: false,
            imageUrl: window.baseUrl + 'com/180/pic/PL-WqnwjVqCor.jpg',
            link: 'http://swsy.duoyi.com/newcont/shenbing/',
            pointBgColor: '#7d7d7d'
          },
          {
            index: 3,
            show: false,
            imageUrl: window.baseUrl + 'com/180/pic/PL-oTBrkxhL9w.jpg',
            link: 'http://swsy.duoyi.com/news/news_5480.shtm',
            pointBgColor: '#7d7d7d'
          },
          {
            index: 4,
            show: false,
            imageUrl: window.baseUrl + 'com/180/pic/PL-xYGEjk6lT8.jpg',
            link: 'http://swsy.duoyi.com/news/news_5508.shtm',
            pointBgColor: '#7d7d7d'
          }
        ],
        newsMore: 'http://swsy.duoyi.com/news/',
        News: [
          {
            index:0,
            name: '新闻',
            className: 'newTitle',
            bgColor:'rgba(250,205,137,0.5)',
            contentShow: true,
            content: [
              {
                text: '《神武2》手游新增110级装备灵 新征程更有新礼包',
                time: '2017-01-01',
                link: 'http://swsy.duoyi.com/news/news_5541.shtm'
              },
              {
                text: '跨平台新服“春风化雨”4月7日开启',
                time: '2017-01-01',
                link: 'http://swsy.duoyi.com/news/news_5521.shtm'
              },
              {
                text: '神武2跨界合作浙江卫视《天生是优我》',
                time: '2017-01-01',
                link: 'http://swsy.duoyi.com/news/news_5516.shtm'
              },
              {
                text: '《神武2》手游快乐抽奖活动上线 多重豪礼送不停',
                time: '2017-01-01',
                link: 'http://swsy.duoyi.com/news/news_5514.shtm'
              },
              {
                text: '全新内容“神兵出世”今日开启 人物套装华丽亮相',
                time: '2017-01-01',
                link: 'http://swsy.duoyi.com/news/news_5508.shtm'
              }
            ]
          },
          {
            index:1,
            name: '活动',
            className: 'newTitle',
            bgColor:'transparent',
            contentShow: false,
            content: [
              {
                text: '全新内容“神兵出世”今日开启 人物套装华丽亮相',
                time: '2017-01-02',
                link: 'http://swsy.duoyi.com/news/news_5533.shtm'
              },
              {
                text: '《神武2》手游快乐抽奖活动上线 多重豪礼送不停',
                time: '2017-01-02',
                link: 'http://swsy.duoyi.com/news/news_5532.shtm'
              },
              {
                text: '神武2跨界合作浙江卫视《天生是优我》',
                time: '2017-01-02',
                link: 'http://swsy.duoyi.com/news/news_5531.shtm'
              },
              {
                text: '你有一份春天的礼物待领取 《神武2》手游暖心迎春',
                time: '2017-01-02',
                link: 'http://swsy.duoyi.com/news/news_5360.shtm'
              },
              {
                text: '领嵩鼠新手礼包 赠许嵩演唱会门票',
                time: '2017-01-02',
                link: 'http://swsy.duoyi.com/news/news_5337.shtm'
              }
            ]
          },
          {
            index:2,
            name: '战报',
            className: 'newTitle',
            bgColor:'transparent',
            contentShow: false,
            content: [
              {
                text: '这是男人之间的对决！第十八届甲组冠军采访实录',
                time: '2017-01-03',
                link: 'http://swsy.duoyi.com/news/news_5520.shtm'
              },
              {
                text: '原来三龙宫背后的故事是这样 第十八届乙组冠军采访实录',
                time: '2017-01-03',
                link: 'http://swsy.duoyi.com/news/news_5518.shtm'
              },
              {
                text: '极品项链大杂烩！第十八届神武之战甲组冠军鉴赏',
                time: '2017-01-03',
                link: 'http://swsy.duoyi.com/news/news_5496.shtm'
              },
              {
                text: '红心大桂花简直666！第十八届神武之战乙组冠军鉴赏',
                time: '2017-01-03',
                link: 'http://swsy.duoyi.com/news/news_5495.shtm'
              },
              {
                text: '第十八届神武之战冠军出炉 麻将队再次卫冕！',
                time: '2017-01-03',
                link: 'http://swsy.duoyi.com/news/news_5489.shtm'
              },
            ]
          },
          {
            index:3,
            name: '文章',
            className: 'newTitle',
            bgColor:'transparent',
            contentShow: false,
            content: [
              {
                text: '神武大讲坛 反制剑气与高速法宠打书加点推荐',
                time: '2017-01-04',
                link: 'http://swsy.duoyi.com/news/news_5528.shtm'
              },
              {
                text: '神武大讲坛 克制隐攻和克制法打书加点推荐',
                time: '2017-01-04',
                link: 'http://swsy.duoyi.com/news/news_5527.shtm'
              },
              {
                text: '神武大讲坛 千速和物理配速宠打书加点推荐',
                time: '2017-01-04',
                link: 'http://swsy.duoyi.com/news/news_5526.shtm'
              },
              {
                text: '玩家故事集  遇见人山人海，唯独你最珍贵',
                time: '2017-01-04',
                link: 'http://swsy.duoyi.com/news/news_5524.shtm'
              },
              {
                text: '神武大讲坛 耐剑气、耐单法打书加点推荐',
                time: '2017-01-04',
                link: 'http://swsy.duoyi.com/news/news_5445.shtm'
              }
            ]
          }
        ],
        fImgSelectIndex:0,
        featuresImage:[
          {
            index:0,
            show:true,
            isLeft:false,
            isRight:false,
            url:window.baseUrl + 'Resource/swsy/v3/img/tese/1s.jpg'
          },
          {
            index:1,
            show:true,
            isLeft:false,
            isRight:true,
            url:window.baseUrl + 'Resource/swsy/v3/img/tese/2s.jpg'
          },
          {
            index:2,
            show:false,
            isLeft:false,
            isRight:false,
            url:window.baseUrl + 'Resource/swsy/v3/img/tese/3s.jpg'
          },
          {
            index:3,
            show:false,
            isLeft:false,
            isRight:false,
            url:window.baseUrl + 'Resource/swsy/v3/img/tese/4s.jpg'
          },
          {
            index:4,
            show:false,
            isLeft:false,
            isRight:false,
            url:window.baseUrl + 'Resource/swsy/v3/img/tese/5s.jpg'
          },
          {
            index:5,
            show:false,
            isLeft:false,
            isRight:false,
            url:window.baseUrl + 'Resource/swsy/v3/img/tese/6s.jpg'
          },
          {
            index:6,
            show:false,
            isLeft:false,
            isRight:false,
            url:window.baseUrl + 'Resource/swsy/v3/img/tese/7s.jpg'
          },
          {
            index:7,
            show:false,
            isLeft:false,
            isRight:false,
            url:window.baseUrl + 'Resource/swsy/v3/img/tese/8s.jpg'
          },
          {
            index:8,
            show:false,
            isLeft:false,
            isRight:false,
            url:window.baseUrl + 'Resource/swsy/v3/img/tese/9s.jpg'
          },
          {
            index:9,
            show:true,
            isLeft:true,
            isRight:false,
            url:window.baseUrl + 'Resource/swsy/v3/img/tese/10s.jpg'
          }
        ],
        gamePictures:[
          {
            content:[
              {
                picText:'金刚葫芦娃',
                url:window.baseUrl + 'Resource/swsy/v3/img/jietu/index/game_pic02.jpg',
                href:'http://swsy.duoyi.com/picture/content.shtm?show=album38#gallery-content'
              },
              {
                picText:'蓝色大海传说',
                url:window.baseUrl + 'Resource/swsy/v3/img/jietu/index/game_pic03.jpg',
                href:'http://swsy.duoyi.com/picture/content.shtm?show=album39#gallery-content'
              }
            ]
          },
          {
            content:[
              {
                picText:'全区第一熊',
                url:window.baseUrl + 'Resource/swsy/v3/img/jietu/index/game_pic04.jpg',
                href: 'http://swsy.duoyi.com/picture/content.shtm?show=album40#gallery-content'
              },
              {
                picText:'误入贼窝',
                url:window.baseUrl + 'Resource/swsy/v3/img/jietu/index/game_pic05.jpg',
                href:'http://swsy.duoyi.com/picture/content.shtm?show=album44#gallery-content'
              }
            ]
          }
        ]
      }
    },
    methods:{
      slide(){
          let _this = this;
          let indexShow = _this.slideIndex;
          let indexHidden;
          let length = _this.Pictures.length;
          _this.animationName = 'slideL';
          slideTime = setInterval(() => {
            indexHidden = (indexShow + 1) % length;
            _this.Pictures[indexShow].show = false;
            _this.Pictures[indexShow].pointBgColor = '#7d7d7d';
            _this.Pictures[indexHidden].show = true;
            _this.Pictures[indexHidden].pointBgColor = '#ffffff';
            indexShow = indexHidden;
          },3000);
      },
      leftTip(){
          let _this = this;
          let indexShow,indexHidden;
          let length =  _this.Pictures.length;
          _this.slideStop();
          _this.stopReStartTime();
          _this.animationName = 'slideL';
          indexShow = _this.slideIndex;
          indexHidden = (indexShow + 1) % length;
          _this.Pictures[indexShow].show = false;
          _this.Pictures[indexShow].pointBgColor = '#7d7d7d';
          _this.Pictures[indexHidden].show = true;
          _this.Pictures[indexHidden].pointBgColor = '#ffffff';
          _this.slideIndex = indexHidden;
          _this.reStartSlide();
      },
      rightTip(){
          let _this = this;
          let indexShow,indexHidden;
          let length =  _this.Pictures.length;
          _this.slideStop();
          _this.stopReStartTime();
          _this.animationName = 'slideR';
          indexShow = _this.slideIndex;
          if (indexShow == 0){
            indexHidden = (4 - indexShow) % length;
          }else {
            indexHidden = (indexShow - 1) % length;
          }
          _this.Pictures[indexShow].show = false;
          _this.Pictures[indexShow].pointBgColor = '#7d7d7d';
          _this.Pictures[indexHidden].show = true;
          _this.Pictures[indexHidden].pointBgColor = '#ffffff';
          _this.slideIndex = indexHidden;
          _this.reStartSlide();
      },
      slideStop(){
          let _this = this;
          let i = 0;
          let length =  _this.Pictures.length;
          clearInterval(slideTime);
          for (i;i < length; i++){
              if (_this.Pictures[i].show){
                  _this.slideIndex = _this.Pictures[i].index;
                  break;
              }
          }
      },
      reStartSlide(){
          let _this = this;
          reStartTime = setTimeout(() => {
              _this.slide();
          },1000)
      },
      stopReStartTime(){
          clearTimeout(reStartTime);
      },
      pointClick(obj){
          let _this = this;
          let clickIndex = obj.index;
          _this.slideStop();
          _this.stopReStartTime();
          _this.animationName = 'fade';
          _this.Pictures.forEach(item => {
              if(item.index != clickIndex){
                  item.show = false;
                  item.pointBgColor = '#7d7d7d';
              }else {
                  item.show = true;
                  item.pointBgColor = '#ffffff';
              }
          });
          _this.slideIndex = clickIndex;
          _this.reStartSlide();
      },
      newContent(){
          let _this = this;
          let Head;
          _this.News.forEach(item => {
              Head = item.name;
              item.content.forEach(contentItem => {
                  contentItem.text = '['+ Head +'] ' + contentItem.text;
              })
          })
      },
      newsTitleClick(obj){
          let _this = this;
          let clickIndex = obj.index;
          _this.News.forEach(item => {
              if(item.index != clickIndex){
                  item.contentShow = false;
                  item.bgColor = 'transparent';
              }else {
                  item.contentShow = true;
                  item.bgColor = 'rgba(250,205,137,0.5)';
              }
          })
      },
      zoom(){
        let _this = this;
        let selectIndex = _this.fImgSelectIndex;
        let leftIndex = 0;
        let rightIndex = 0;
        let length = _this.featuresImage.length - 1;
        zoomTime = setInterval(() => {
          leftIndex = selectIndex == 0 ? length - selectIndex : selectIndex - 1;
          rightIndex = (selectIndex + 1) % (length+1);
          _this.featuresImage.forEach(item => {
              item.show = false;
              item.select = false;
              item.isLeft = false;
              item.isRight = false;
          });
          _this.featuresImage[selectIndex].show = true;
          _this.featuresImage[leftIndex].show = true;
          _this.featuresImage[leftIndex].isLeft = true;
          _this.featuresImage[rightIndex].show = true;
          _this.featuresImage[rightIndex].isRight = true;
          selectIndex = rightIndex;
        },3000);
      },
      isLeft(obj){
        let _this = this;
        let selectIndex = _this.fImgSelectIndex;
        let index = obj.index;
        let length = _this.featuresImage.length - 1;
        let isSelect = obj.select;
        return (!isSelect && (index == length && selectIndex == 0) || index < selectIndex )? 'imageLeft' : '';
      },
      isRight(obj){
        let _this = this;
        let selectIndex = _this.fImgSelectIndex;
        let index = obj.index;
        let length = _this.featuresImage.length - 1;
        let isSelect = obj.select;
        return (!isSelect && (index == 0 && selectIndex == length) || (index > selectIndex && !(index == length && selectIndex == 0)) )?  'imageRight' : '';
      },
      select(obj){
        return (!obj.isLeft && !obj.isRight) ? true : false;
      }
    },
    components:{
      'app-header':Header,
      'app-footer':Footer,
      'app-toTop':ScrollToTop
    },
    computed:{
    },
    created(){
    },
    mounted(){
        this.$nextTick(() => {
            this.slide();
            this.newContent();
            this.zoom();
        })
    }
  }
</script>
<style scoped>
  .home{
    display: flex;
    flex: 1;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: #eeeeee;

    display: -webkit-flex;
    -webkit-flex-direction: column;
    -webkit-justify-content: center;
    -webkit-align-items: center;
  }
  .toTop{
    position: fixed;
    right: 0.3rem;
    bottom: 3rem;
    z-index: 10;
  }
  .appHead{
    z-index: 5;
  }
  .content{
    display: flex;
    flex: 1;
    flex-direction: column;
    width: 100%;
  }
  .homeBg{
    margin-top: 2rem;
    width: 100%;
    height: 10.69rem;
    background-image: url("https://raw.githubusercontent.com/linyuang/Text-shenWu/master/assets/home_page_bg.jpg");
    background-size: cover;

    -webkit-background-image: url("https://raw.githubusercontent.com/linyuang/Text-shenWu/master/assets/home_page_bg.jpg");
    -webkit-background-size: cover;
  }
  .homeBgLink{
    display: block;
    width: 100%;
    height: 8rem;
  }
  .downloadLinkBox {
    display: flex;
    flex: 1;
    width: 100%;
    height: 2.69rem;
    flex-direction: row;
    justify-content: space-around;
    align-content: center;

    display: -webkit-flex;
    -webkit-flex: 1;
    -webkit-flex-direction: row;
    -webkit-justify-content: space-around;
    -webkit-align-items: center;
  }
  .downloadAndroid,.downloadMac{
    width: auto;
    height: 1.5rem;
  }
  .news {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
    width: 100%;
    height: 20rem;
    background-image: url("https://raw.githubusercontent.com/linyuang/Text-shenWu/master/assets/news_bg.jpg");
    background-size: cover;
    border-top: 2px solid #eeeeee;
    border-bottom: 2px solid #eeeeee;

    display: -webkit-flex;
    -webkit-flex-direction: column;
    -webkit-justify-content: center;
    -webkit-align-items: center;
    -webkit-background-image: url("https://raw.githubusercontent.com/linyuang/Text-shenWu/master/assets/news_bg.jpg");
    -webkit-background-size: cover;
  }
  .slidePictureBox,.slideNewsBox{
    display: flex;
    justify-content: center;

    display: -webkit-flex;
    -webkit-justify-content: center;

  }
  .slidePictureBox {
    flex: 2;
    align-items: flex-end;

    -webkit-flex: 2;
    -webkit-align-content: flex-end;
  }
  .slidePicture{
    width: 12.92rem;
    height: 6.67rem;
    overflow: hidden;
    position: relative;
    z-index: 1;
  }
  .pictures{
    width: 12.92rem;
    height: 6.67rem;
    position: absolute;
  }
  .picture{
    width: 12.92rem;
    height: 6.67rem;
  }
  .pointGroup{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 1.5rem;
    background-color: rgba(0,0,0,0.2);
    position: absolute;
    bottom:0;
  }
  .point{
    width: 0.5rem;
    height: 0.5rem;
    border-radius: 0.25rem;
    margin: 0.1rem;
  }
  .slideNewsBox{
    flex: 3;
    align-items: center;

    -webkit-flex: 3;
    -webkit-align-content: center;
  }
  .slideNews{
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 12.92rem;
    height: 10rem;
    background-color: rgba(255,255,255,0.8);

    display: -webkit-flex;
    -webkit-flex-direction: column;
    -webkit-align-items: center;
  }
  .newsHeadBox{
    display: flex;
    flex: 1;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    width:11.92rem;
    border-bottom: 2px solid rgb(230,204,135);

    display: -webkit-flex;
    -webkit-flex: 1;
    -webkit-flex-direction: row;
    -webkit-align-items: center;
    -webkit-justify-content: space-between;
  }
  .newTitleBox{
    display: flex;
    width: 8rem;
    flex-direction: row;
    align-items: center;

    display: -webkit-flex;
    -webkit-flex-direction: row;
    -webkit-align-items: center;
  }
  .newTitle{
    display: flex;
    width: 2.92rem;
    justify-content: center;
    align-items: center;

    display: -webkit-flex;
    -webkit-flex: 1;
    -webkit-justify-content: center;
    -webkit-align-items: center;
  }
  .titleText{
    font-size: 0.5rem;
  }
  .newsMore{
    display: block;
    text-decoration: none;
    color: #000000;
    font-size: 0.5rem;
  }
  .newsContentBox{
    display: flex;
    flex: 7;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    width: 11.92rem;

    display: -webkit-flex;
    -webkit-flex: 5;
    -webkit-flex-direction: column;
    -webkit-justify-content: flex-start;
    -webkit-align-items: center;
  }
  .newsPage{
    display: flex;
    flex-direction: column;
    width: 100%;

    display: -webkit-flex;
    -webkit-flex-direction: column;
  }
  .newBox{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    height: 2rem;
    text-decoration: none;
    color: #000000;

    display: -webkit-flex;
    -webkit-flex-direction: row;
    -webkit-justify-content: space-between;
    -webkit-align-items: center;
  }
  .newContent{
    width: 6rem;
    padding-left: 0.5rem;
    font-size: 0.5rem;
    overflow: hidden;
    white-space: nowrap;
    text-overflow:ellipsis;
  }
  .newContent:hover{
    color: red;
    text-decoration: none;
  }
  .newTime{
    width: 4rem;
    text-align: right;
    font-size: 0.5rem;
  }
  .features{
    display: flex;
    flex-direction: column;
    align-items: center;
    background-image:url("https://raw.githubusercontent.com/linyuang/Text-shenWu/master/assets/featuresBg.jpg");
    background-size: cover;
    width: 16rem;
    height: 12.01rem;
    overflow-x: hidden;
    overflow-y: visible;

    display: -webkit-flex;
    -webkit-flex-direction: column;
    -webkit-align-items: center;
    -webkit-background-image:url("https://raw.githubusercontent.com/linyuang/Text-shenWu/master/assets/featuresBg.jpg");
    -webkit-background-size: cover;
  }
  .featuresTitle{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    width: 10rem;
    height: 2rem;
    margin-bottom: 0.8rem;

    display: -webkit-flex;
    -webkit-flex-direction: row;
    -webkit-justify-content: center;
    -webkit-align-items: center;
  }
  .featuresTitleIcon{
    width: 2rem;
    height: auto;
  }
  .featuresTitleText{
    font-size: 0.8rem;
    color: rgb(53,76,177);
    margin: 0 0.4rem;
    font-weight: bold;
  }
  .featuresBox{
    position: relative;
    width: 10rem;
    height: 7.5rem;
  }
  .featureImageBox{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 10rem;
    height: 7.5rem;
    position: absolute;
    left:0;

    transition: 1s left ease-in-out;
    -webkit-transition: 1s left ease-in-out;
  }
  .featureImage{
    width: 10rem;
    height: 7.5rem;
    transform: perspective(10rem) translateZ(0rem);

    transition: 1s transform ease-in-out;
    -webkit-transition: 1s transform ease-in-out;
  }
  .ImageBig{
    transform: perspective(10rem) translateZ(2rem);
    z-index: 2;
  }
  .ImageSmall{
    transform: perspective(10rem) translateZ(-1rem);
    z-index: 1;
  }
  .imageLeft{
    left: -10rem;
  }
  .imageRight{
    left: 10rem;
  }
  .gamePictures {
    display: flex;
    flex-direction: column;
    width: 16rem;
    height: 12rem;
    background: linear-gradient( rgb(241, 249, 252),rgb(255,255,255));

    display: -webkit-flex;
    -webkit-flex-direction: column;
    background: -webkit-linear-gradient( rgb(241, 249, 252),rgb(255,255,255));
  }
  .gamePicTileBox{
    display: flex;
    flex: 1;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    width: 16rem;

    display: -webkit-flex;
    -webkit-flex: 1;
    -webkit-flex-direction: row;
    -webkit-justify-content: center;
    -webkit-align-items: center;
  }
  .gamePicBox{
    display: flex;
    flex: 5;
    flex-direction: column;
    width: 16rem;

    display: -webkit-flex;
    -webkit-flex: 5;
    -webkit-flex-direction: column;
  }
  .gamePics{
    display: flex;
    flex: 1;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    width: 16rem;

    display: -webkit-flex;
    -webkit-flex: 1;
    -webkit-flex-direction: row;
    -webkit-justify-content: space-around;
    -webkit-align-items: center;
  }
  .gamePic{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-decoration: none;
    width: 6rem;
    height: 4rem;
    color: #000000;

    display: -webkit-flex;
    -webkit-flex-direction: column;
    -webkit-justify-content: center;
    -webkit-align-items: center;
  }
  .gamePic:hover{
    color: #ff0000;
  }
  .pic{
    width: 6rem;
    height: auto;
  }
  .picText{
    font-size: 0.5rem;
  }
</style>

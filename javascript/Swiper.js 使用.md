## Swiper.js 使用



### 导航条 Navbar

```js
const swiper = new Swiper("#swiper", {
    autoplay: false,
    loop: false, // 无限循环
    //resistanceRatio: 0, // 边缘抵抗力的大小比例，值越小抵抗越大越难将slide拖离边缘，0时完全无法拖离。
    freeMode: true, // 是否开启惯性滑动
    freeModeMomentumRatio: 0.5, // 移动惯量，设置的值越大，当释放slide时的滑动时间越长。
    slidesPerView : 'auto', // 设置slider容器能够同时显示的slides数量, 设置`auto`根据slide的宽度自动计算。
    on: {
        // 设置点击时自动偏移量
        tap: function() {
            const swiperWidth = this.$el[0].clientWidth;
            const maxTranslate = this.maxTranslate();
            const maxWidth = -maxTranslate + swiperWidth / 2;
            const slide = this.slides[this.clickedIndex];
            const slideLeft = slide.offsetLeft;
            const slideWidth = slide.clientWidth;
            const slideCenter = slideLeft + slideWidth / 2; // 被点击slide的中心点
            this.setTranslate(300);
            if (slideCenter < swiperWidth / 2) {
                this.setTranslate(0);
            } else if (slideCenter > maxWidth) {
                this.setTranslate(maxTranslate);
            } else {
                const nowTlanslate = slideCenter - swiperWidth / 2;
                this.setTranslate(-nowTlanslate);
            }
            //$("#swiper .active").removeClass('active');
            //$("#swiper .swiper-slide").eq(this.clickedIndex).addClass('active');
        }
    }
});
```

[参考API文档]: https://www.swiper.com.cn/api/index.html


<template>
  <div class="header">
    <div class="content-wrapper">
      <div class="avatar">
        <img :src="seller.avatar" width="64px" height="64px">
      </div>
      <!--内容-->
      <div class="content">
        <!--店名-->
        <div class="title">
          <span class="brand"></span>
          <span class="title-name">{{seller.name}}</span>
        </div>
        <!--描述-->
        <div class="description">
          {{seller.description}}/{{seller.deliveryTime}}分钟送达
        </div>
        <!--优惠-->
        <div class="support" v-if="seller.supports">
          <span class="icon" :class="classMap[seller.supports[0].type]"></span>
          <span class="text">{{seller.supports[0].description}}</span>
        </div>
      </div>
      <!--右边小图标-->
      <div class="support-count" v-if="seller.supports">
        <span class="count">{{seller.supports.length}}个</span>
        <i class="icon-keyboard_arrow_right"></i>
      </div>
    </div>
    <div class="bulletin-wrapper">

    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    props: {
      seller: {
        type: Object
      }
    },
    created() {
        this.classMap = ['decrease', 'discount', 'special', 'guarantee', 'invoice'];
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/mixin.styl";
  .header
    background-color: gray;
    .content-wrapper
      position: relative
      padding: 24px 12px 18px 24px
      font-size: 0
      color: #fff
      .avatar
        display: inline-block
        vertical-align top
        img
          border-radius: 2px
          overflow: hidden
      .content
        display: inline-block
        margin-left 16px
        .title
          margin: 2px 0 8px 0
          .brand
            display: inline-block
            width: 30px
            height: 18px
            vertical-align top
            bg-image('brand');
            background-size: 30px 18px
            background-repeat no-repeat
          .title-name
            margin-left: 6px
            font-size 16px
            line-height: 18px;
            font-weight: bold;


        .description
          font-size: 12px
          line-height: 12px
          margin-bottom: 10px
        .support
          .icon
            display: inline-block
            width: 12px
            height: 12px
            margin-right: 4px
            background-size: 12px 12px
            background-repeat: no-repeat
            vertical-align top
            &.decrease
              bg-image('./decrease_1')
            &.discount
              bg-image('./discount_1')
            &.guarantee
              bg-image('./guarantee_1')
            &.invoice
              bg-image('./invoice_1')
            &.special
              bg-image('./special_1')
          .text
            line-height: 12px
            font-size: 12px



      .support-count
        position: absolute
        right: 12px
        bottom: 12px
        padding: 0 8px
        line-height: 24px
        height: 24px
        background: rgba(0, 0, 0, 0.2);
        font-size: 12px
        border-radius: 14px
        .count
          vertical-align: top
        .icon-keyboard_arrow_right
          line-height: 24px
          margin-left: 2px


</style>

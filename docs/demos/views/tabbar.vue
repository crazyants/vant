<template>
  <demo-section>
    <demo-block :title="$t('basicUsage')">
      <van-tabbar v-model="active">
        <van-tabbar-item icon="shop">{{ $t('tab') }}</van-tabbar-item>
        <van-tabbar-item icon="chat" dot>{{ $t('tab') }}</van-tabbar-item>
        <van-tabbar-item icon="records" info="5">{{ $t('tab') }}</van-tabbar-item>
        <van-tabbar-item icon="gold-coin" info="20">{{ $t('tab') }}</van-tabbar-item>
      </van-tabbar>
    </demo-block>

    <demo-block :title="$t('title2')">
      <van-tabbar v-model="active2">
        <van-tabbar-item icon="shop">
          <span>{{ $t('custom') }}</span>
          <template slot="icon" slot-scope="props">
            <img :src="props.active ? icon.active : icon.normal" />
          </template>
        </van-tabbar-item>
        <van-tabbar-item icon="chat">{{ $t('tab') }}</van-tabbar-item>
        <van-tabbar-item icon="records">{{ $t('tab') }}</van-tabbar-item>
      </van-tabbar>
    </demo-block>
  </demo-section>
</template>

<script>
export default {
  i18n: {
    'zh-CN': {
      title2: '自定义图标'
    },
    'en-US': {
      title2: 'Custom icon'
    }
  },

  data() {
    return {
      active: 0,
      active2: 0,
      icon: {
        normal: 'https://img.yzcdn.cn/public_files/2017/10/13/c547715be149dd3faa817e4a948b40c4.png',
        active: 'https://img.yzcdn.cn/public_files/2017/10/13/793c77793db8641c4c325b7f25bf130d.png'
      }
    }
  }
}
</script>


<style lang="postcss">
.demo-tabbar {
  .van-tabbar {
    position: relative;

    &-item {
      cursor: pointer;
    }
  }
}
</style>

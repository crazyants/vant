<template>
  <transition name="van-dialog-bounce">
    <div class="van-dialog" v-show="value">
      <div class="van-dialog__header" v-if="title" v-text="title" />
      <div class="van-dialog__content van-hairline">
        <slot>
          <div class="van-dialog__message" v-if="message" :class="{ 'van-dialog__message--withtitle': title }" v-html="message" />
        </slot>
      </div>
      <div class="van-dialog__footer" :class="{ 'is-twobtn': showCancelButton && showConfirmButton }">
        <van-button
          size="large"
          class="van-dialog__cancel"
          v-show="showCancelButton"
          @click="handleAction('cancel')"
        >
          {{ cancelButtonText || $t('cancel') }}
        </van-button>
        <van-button
          size="large"
          class="van-dialog__confirm"
          :class="{ 'van-hairline--left': showCancelButton && showConfirmButton }"
          v-show="showConfirmButton"
          @click="handleAction('confirm')"
        >
          {{ confirmButtonText || $t('confirm') }}
        </van-button>
      </div>
    </div>
  </transition>
</template>

<script>
import VanButton from '../button';
import Popup from '../mixins/popup';
import { i18n } from '../locale';

export default {
  name: 'van-dialog',

  components: {
    VanButton
  },

  mixins: [Popup, i18n],

  props: {
    title: String,
    message: String,
    callback: Function,
    confirmButtonText: String,
    cancelButtonText: String,
    showConfirmButton: {
      type: Boolean,
      default: true
    },
    showCancelButton: {
      type: Boolean,
      default: false
    },
    overlay: {
      default: true
    },
    closeOnClickOverlay: {
      default: false
    },
    lockOnScroll: {
      default: true
    }
  },

  methods: {
    handleAction(action) {
      this.$emit('input', false);
      this.$emit(action);
      this.callback && this.callback(action);
    }
  }
};
</script>

<template>
  <div class="modal__outer-wrapper">
    <div class="modal__inner-wrapper">
      <div class="modal__photo">
        <img :src="photo" alt="modal-photo">
      </div>
      <div class="modal__description">
        <h2 class="modal__description-title">
          {{ title }}
        </h2>
        <p class="modal__description-text">
          {{ description }}
        </p>
      </div>
    </div>
    <div class="modal__close" @click="$emit('closeModal')"></div>
  </div>
</template>
<script>
export default {
  name: 'Modal',
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      photo: null,
      title: null,
      description: null,
    };
  },
  mounted() {
    this.photo = this.item.links[0].href;
    this.title = this.item.data[0].title;
    this.description = this.item.data[0].description;
  },
};
</script>
<style lang="scss" scoped>
  @import '~@/scss/settings';

  .modal {
    &__outer-wrapper {
      position: fixed;
      max-width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      background-color: $modal-bg-color;

      @media (min-width: $screen-md) {
        max-width: 70%;
        height: 60%;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
        margin: auto;
        box-shadow: 0 30px 30px -10px rgba(0,0,0, .3);
      }
    }

    &__inner-wrapper {
      display: flex;
      height: 100%;
      padding: 50px;
      justify-content: center;
      align-items: center;
      flex-direction: column;

      @media (min-width: $screen-md) {
        flex-direction: row;
      }
    }

    &__close {
      padding: 30px;
      position: absolute;
      width: 30px;
      height: 30px;
      right: 0;
      top: 0;
      cursor: pointer;

      &::before,
      &::after {
        content: '';
        display: block;
        position:absolute;
        top: 30px;
        right: 20px;
        width: 20px;
        height: 2px;
        background-color: black;
      }

      &::before {
        transform: rotate(45deg);
      }

      &::after {
        transform: rotate(-45deg);
      }
    }

    &__description {
      max-height: 66%;
      overflow-y: auto;
      word-break: break-word;
      color: $modal-text-color;
    }

    &__description-title {
      color: $modal-title-color;
    }

    &__photo {
      width: 100%;
      height: auto;
      background-color: black;

      @media (min-width: $screen-md) {
        min-width: 50%;
        margin-right: 20px;
      }

      img {
        width: 100%;
      }
    }
  }
</style>

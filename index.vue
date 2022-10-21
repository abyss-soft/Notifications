<template>
  <div :class="['notification', theme]">
    <div class="notification__image">
      <svg-icon class="icon" :name="img" />
    </div>
    <div class="notification__text-wrapper">
      <div class="notification__title">
        <slot name="title"></slot>
      </div>
      <div class="notification__text">
        <slot name="text"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NotificationUI",
  props: {
    theme: {
      type: String,
      required: true,
      validator: (v) =>
        [
          "loader",
          "warning",
          "success",
          "error",
          "darkInfo",
          "lightInfo",
        ].includes(v),
    },
    /**
     * link to custom icon
     */
    icon: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      themesImg: {
        loader: "dark_loader",
        warning: "warning",
        error: "error",
        success: "success",
        darkInfo: "info",
        lightInfo: "info",
      },
    };
  },
  computed: {
    img() {
      if (this.icon) return this.icon;
      return `notification/${this.themesImg[this.theme]}`;
    },
  },
};
</script>

<style src="./styles.scss" lang="scss" scoped></style>

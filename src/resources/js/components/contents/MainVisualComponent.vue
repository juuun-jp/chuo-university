<template>
<div class="main-visual">
  <slot name="inner">
  <span class="main-visual__title" v-text="messages.MainVisual.Top"></span>
  </slot>
</div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
.main-visual{
  width: 100%;
  height: 100vh;
  @include gradient(color(deepDarkblue), color(darkblue), horizontal);
  @include flex(
    $flow:column nowrap,
    $justify-content:center,
    $align-items:center
  );


  &__title {
    color: color(white);
    white-space: pre-wrap;
    font-family: Arial, Helvetica, sans-serif;
    font-size: font(mv);
    font-weight: bold;
    text-shadow: 3px 3px 0px color(orange);

    // pc style
    @include mq(md) {
      line-height: 1.2;
      font-size: font(mv-lg);
    };
  }
}
</style>

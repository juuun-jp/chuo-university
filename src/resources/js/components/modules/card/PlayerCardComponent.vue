<template>
<div class="player-card">
  <figure class="player-card__figure">
    <img :src="`/image/${player.img.src}`" :alt="player.img.alt">
  </figure>

  <div class="player-card__information">
    <div class="player-card__information-name-wrap">
      <span class="player-card__information-name">{{ player.name.ja }}</span>
      <span class="player-card__information-name-english">{{ player.name.en }}</span>
    </div>

    <div class="player-card__information-tags">
      <position-tag-component :position="player.position"/>
      <tag-component v-if="player.post.club" :content="player.post.club"/>
      <grade-tag-component :grade="player.grade"/>
    </div>
  </div>
</div>
</template>

<script>
// component import
import TagComponent from '../tag/TagComponent';
import PositionTagComponent from '../tag/PositionTagComponent';
import GradeTagComponent from '../tag/GradeTagComponent';

export default {
  components: {
    TagComponent,
    PositionTagComponent,
    GradeTagComponent,
  },
  props: {
    player: {
      type: Object,
      default: null,
    }
  }
}
</script>

<style lang="scss">
.player-card {
  width: 60%;

  @include mq(sm) {
    width: 30%;
  }

  @include mq(md) {
    width: 20%;
  }

  &__figure {
    @include trimming(aspect(square));
    border-bottom: 2px solid color(darkblue);
    background-color: color(white);
  }

  &__information {
    background-color: color(lightgrey);
    padding: interval(1);

    &-name {
      font-size: font(sm);
      font-weight: bold;
      margin: 0 interval(1) 0 interval(.5);
    }

    &-name-english {
      font-weight: bold;
      font-size: font(xs);
    }

    &-tags {
      @include flex($flow: row wrap);
      align-content: space-around;
      padding: interval(1) 0;
    }
  }
}
</style>

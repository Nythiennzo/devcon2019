<template>
  <div class="speaker-box" :id="speaker.fullName">
    <div class="speaker-image" v-if="speaker">
      <img :src="speaker.profilePicture" alt>
    </div>
    <div class="bizin-trouv-bien"></div>
    <div class="speaker-meta">
      <div class="name">{{ speaker.fullName }}</div>
      <div class="occupation">{{ speaker.tagLine }}</div>
      <div class="alias"></div>
      <div class="talk-count" v-if="speaker.sessions.length > 1">
        {{
        speaker.sessions.length }} talks
      </div>
      <div class="talk-count" v-else>{{ speaker.sessions.length }} talk</div>
      <div class="social-media-wrapper"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["speaker"],
};
</script>

<style lang="scss" scoped>
.speaker-box {
  --width: 170px;
  //   --size: 215px;
  --spacing: 10px;

  width: calc(var(--width) * 1.7);
  z-index: 10;
  height: calc(var(--width) * 2.5);
  position: relative;

  .speaker-image {
    height: 100%;
    position: absolute;
    background: black;
    &:after {
      content: " ";
    }

    transform-origin: left bottom;
    transform: skew(-18deg);
    border-radius: 30px;
    overflow: hidden;
    width: calc(var(--width) * 1.2);
    left: 0;
    transition: all 0.3s ease-out;

    img {
      display: block;
      width: auto;
      height: 100%;
      transform: skew(18deg);
      margin-left: calc(var(--width) * -1 / 2);
    }
  }

  .bizin-trouv-bien {
    position: absolute;
    background: linear-gradient(transparent, transparent, #000);

    width: calc(var(--width) * 1.2);
    height: 100%;
    border-radius: 30px;

    transform-origin: left bottom;
    transform: skew(-18deg);
    transition: all 0.3s ease-out;
  }

  .speaker-meta {
    letter-spacing: 2px;
    text-shadow: 0 1px 2px #000;
    position: absolute;
    bottom: 5%;
    left: 20%;

    .name {
      font-size: 25px;
      font-weight: 800;
      padding-bottom: var(--spacing);
      text-align: right;
    }
    .occupation {
      font-size: 16px;
      padding-bottom: var(--spacing);
      text-transform: capitalize;
    }
    .alias {
      font-size: 16px;
      text-transform: uppercase;
      padding-bottom: var(--spacing);
      font-weight: 500;
    }
    .talk-count {
      display: inline-block;
      padding: 10px 13px 5px;
      font-size: 12px;
      border-radius: 7px;
      text-shadow: none;
      padding-bottom: var(--spacing);
      text-transform: uppercase;
      background: linear-gradient(to right, rgb(252, 218, 159) 0%, rgb(255, 95, 56) 0%, rgb(192, 37, 51) 100%);
    }
    .social-media-wrapper {
    }
  }

  &:before {
    content: " ";
    width: var(--width);
    height: calc(var(--width) * 1.9);
    // left: 50%;
    top: calc(var(--width) / 2);
    left: 0;
    margin-left: -calc(var(--width) / 2);

    position: absolute;
    background-image: url("../../assets/menu-hover.svg");
    background-repeat: no-repeat;
    background-position: center center;
    background-size: contain;
    transform: translate(0px, 10px);
    opacity: 0.5;
    transition: all 0.2s ease-in;
  }
  &:after {
    content: " ";
    z-index: -1;
    width: var(--width);
    height: calc(var(--width) * 0.75);
    left: calc(var(--width) * 1.35);
    top: 0px;
    // left: 0;
    // margin-left: -calc(var(--width) / 2);

    position: absolute;
    background-image: url("../../assets/menu-hover.svg");
    background-repeat: no-repeat;
    background-position: center center;
    background-size: contain;
    transform: translate(0px, 10px);
    opacity: 0.5;
    transition: all 0.2s ease-in;
  }

  &:hover {
    &:before {
      // width: var(--width);
      // height: calc(var(--width) * 1.9);
      // left: 50%;
      // top: calc(var(--width) / 2);
      // left: 0;
      // margin-left: -calc(var(--width) / 2);

      transform: translate(-15px, 10px);
      opacity: 1;
      transition: all 0.3s ease-out;
    }
    &:after {
      // width: var(--width);
      // height: calc(var(--width) * 0.75);
      // left: calc(var(--width) * 1.2);
      // top: 0px;

      transform: translate(15px, 10px);
      opacity: 1;
      transition: all 0.3s ease-out;
    }
  }

  @media screen and (max-width: $tablet-portrait) {
    --width: 100px;
  }
}
</style>

<script setup lang="ts">
import { onMounted, onUnmounted } from 'vue';

function handleScroll() {
  let zSpacing = -1000,
    lastPos = zSpacing / 5,
    $frames = document.getElementsByClassName('frame'),
    frames = Array.from($frames),
    zVals: number[] = [];

  let top = document.documentElement.scrollTop,
    delta = lastPos - top;

  lastPos = top;

  frames.forEach(function (_, i) {
    zVals.push(i * zSpacing + zSpacing);
    zVals[i] += delta * -5.5;
    let frame = frames[i],
      transform = `translateZ(${zVals[i]}px)`,
      opacity = zVals[i] < Math.abs(zSpacing) / 1.8 ? 1 : 0;
    frame.setAttribute('style', `transform: ${transform}; opacity: ${opacity}`);
  });
}

onMounted(() => {
  window.scrollTo(0, 1);
  window.addEventListener('scroll', handleScroll);
});
onUnmounted(() => window.removeEventListener('scroll', handleScroll));
</script>

<template>
  <section class="gallery">
    <div class="frame">
      <div class="frame__content">
        <h2>Flowers gallery</h2>
      </div>
    </div>
    <div class="frame">
      <div class="frame__content">
        <div
          class="frame-media frame-media_left"
          :style="{ backgroundImage: 'url(/assets/images/flower1.jpg)' }"
        ></div>
      </div>
    </div>

    <div class="frame frame_bg">
      <div class="frame__content">
        <div
          class="frame-media frame-media_right"
          :style="{ backgroundImage: 'url(/assets/images/flower2.jpg)' }"
        ></div>
      </div>
    </div>

    <div class="frame"></div>

    <div class="frame">
      <div class="frame__content text-right">
        <h3>Some about flowers</h3>
        <p>
          Lorem ipsum dolor sit amet, consectetur elit adipisicing. Nemo fugit,
          rerum dolorem assumenda consequatur dicta error iure laboriosam
          temporibus.
        </p>
      </div>
    </div>

    <div class="frame frame_bg">
      <div class="frame__content">
        <div
          class="frame-media frame-media_left"
          :style="{ backgroundImage: 'url(/assets/images/flower3.jpg)' }"
        ></div>
      </div>
    </div>

    <div class="frame"></div>

    <div class="frame frame_bg">
      <div class="frame__content">
        <div
          class="frame-media frame-media_right"
          :style="{ backgroundImage: 'url(/assets/images/flower4.jpg)' }"
        ></div>
      </div>
    </div>

    <div class="frame"></div>

    <div class="frame">
      <div class="frame__content text-left">
        <h3>More about flowers</h3>
        <p>
          Lorem ipsum dolor sit amet, consectetur elit. Rerum dolorem assumenda
          consequatur dicta error iure laboriosam temporibus omnis quae eaque
          aliquam esse unde accusamus dolores non soluta.
        </p>
      </div>
    </div>

    <div class="frame frame_bg">
      <div class="frame__content">
        <div
          class="frame-media frame-media_right"
          :style="{ backgroundImage: 'url(/assets/images/flower5.jpg)' }"
        ></div>
      </div>
    </div>

    <div class="frame">
      <div class="frame__content">
        <div
          class="frame-media frame-media_left"
          :style="{ backgroundImage: 'url(/assets/images/flower6.jpg)' }"
        ></div>
      </div>
    </div>

    <div class="frame"></div>
    <div class="frame"></div>

    <div class="frame frame_bg">
      <div class="frame__content">
        <div
          class="frame-media frame-media_right"
          :style="{ backgroundImage: 'url(/assets/images/flower7.jpg)' }"
        ></div>
      </div>
    </div>

    <div class="frame frame_bg">
      <div class="frame__content">
        <div class="frame__content">
          <div
            class="frame-media"
            :style="{ backgroundImage: 'url(/assets/images/flower8.jpg)' }"
          ></div>
        </div>
      </div>
    </div>

    <div class="frame"></div>
    <div class="frame"></div>

    <div class="frame">
      <div class="frame__content">Thank you for watching</div>
    </div>
  </section>
</template>

<style scoped>
.gallery {
  transform-style: preserve-3d;
  height: 100%;
}

.frame {
  width: 100%;
  height: 100%;
  position: absolute;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: var(--transition), opacity 0.75s ease;
  will-change: transform;
  transform-style: preserve-3d;
}

.frame h2 {
  text-align: center;
  font-size: calc(var(--index) * 3.3);
}

.frame-media {
  position: relative;
  width: calc(var(--index) * var(--side-small));
  height: calc(var(--index) * var(--side-big));
  background-position: center;
  background-size: cover;
}

.frame-media_left {
  right: calc(var(--side-small) / 2 * var(--index) + var(--gutter));
}

.frame-media_right {
  left: calc(var(--side-small) / 2 * var(--index) + var(--gutter));
}

.frame_bg {
  background-color: rgb(0 0 0 / 0.87);
}

.text-right > * {
  position: relative;
  left: 18vw;
}
.text-left > * {
  position: relative;
  right: 18vw;
}
.frame h3 {
  font-size: calc(var(--index) * 3);
}
.frame p {
  max-width: 30vw;
  margin-top: 3vh;
}
</style>

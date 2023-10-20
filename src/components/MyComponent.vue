<template>
  <div class="main">
    <h1>Filter your image with US</h1>
    <div class="container">
      <div>
        <div class="image">
          <img
            v-if="isImageVisible"
            :class="[imgFilters]"
            :style="imgStyles"
            src="../assets/nature-photo.jpg"
          />
          <p v-else>Don't worry, your image will return soon!<br /><br />Press "Show"</p>
        </div>
        <div class="controls">
          <button
            @click="isImageVisible = !isImageVisible"
            :class="isImageVisible ? ' ' : 'active'"
          >
            {{ isImageVisible ? "Hide" : "Show" }}
          </button>
        </div>
      </div>
      <div>
        <h2>Filters</h2>
        <div class="btn-group flex">
          <button
            type="button"
            @click="imgFilters.sepia = !imgFilters.sepia"
            :class="imgFilters.sepia ? 'active' : ' '"
          >
            Sepia
          </button>
          <button
            type="button"
            @click="imgFilters.grayscale = !imgFilters.grayscale"
            :class="imgFilters.grayscale ? 'active' : ' '"
          >
            Grayscale
          </button>
          <button
            type="button"
            @click="imgFilters.border = !imgFilters.border"
            :class="imgFilters.border ? 'active' : ' '"
          >
            Border
          </button>
          <button
            type="button"
            @click="imgFilters.shadow = !imgFilters.shadow"
            :class="imgFilters.shadow ? 'active' : ' '"
          >
            Shadow
          </button>
        </div>
        <h2>Choose Size</h2>
        <div class="for-size">
          <label>
            Width: {{ imgSizes.currentWidth }} px
            <input
              type="range"
              :value="imgSizes.currentWidth"
              @input="imgSizes.currentWidth = $event.target.value"
              :min="imgSizes.minWidth"
              :max="imgSizes.maxWidth"
            />
          </label>
          <label>
            Height: {{ imgSizes.currentHeight }} px
            <input
              type="range"
              :value="imgSizes.currentHeight"
              @input="imgSizes.currentHeight = $event.target.value"
              :min="imgSizes.minHeight"
              :max="imgSizes.maxHeight"
            />
          </label>
        </div>
        <h2>Rotate</h2>
        <div class="rotate">
          <label>
            Angle: {{ rotate.value }}
            <input
              type="range"
              :value="rotate.value"
              @input="rotate.value = $event.target.value"
              :min="rotate.min"
              :max="rotate.max"
            />
          </label>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyComponent",
  data() {
    return {
      isImageVisible: true,
      imgFilters: {
        sepia: false,
        border: false,
        shadow: false,
        grayscale: false,
      },
      imgSizes: {
        maxWidth: 680,
        maxHeight: 480,
        minHeight: 300,
        minWidth: 400,
        currentWidth: 680,
        currentHeight: 480,
      },
      rotate: {
        min: 0,
        max: 360,
        value: 0,
      },
    };
  },
  computed: {
    imgStyles() {
      return {
        width: `${this.imgSizes.currentWidth}px`,
        height: `${this.imgSizes.currentHeight}px`,
        transform: `rotate(${this.rotate.value}deg)`,
      };
    },
  },
};
</script>

<style></style>

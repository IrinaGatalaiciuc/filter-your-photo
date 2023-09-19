<template>
  <div class="main">
    <div>
      <div class="image">
        <img v-if="isImageVisible" :class=[imgFilters] :style="imgStyles" src="../assets/nature-photo.jpg">
        <p v-else>V will return soon</p>
      </div>
      <div class="controls">
        <h1>Visions of V</h1>
        <h2>Filters</h2>
        <div class="btn-group flex">
          <button type="button" @click="imgFilters.sepia = !imgFilters.sepia" :class="imgFilters.sepia ? 'active' : ' '">
            Sepia
          </button>
          <button type="button" @click="imgFilters.border = !imgFilters.border"
            :class="imgFilters.border ? 'active' : ' '">
            Border
          </button>
          <button type="button" @click="imgFilters.shadow = !imgFilters.shadow"
            :class="imgFilters.shadow ? 'active' : ' '">
            Shadow
          </button>
        </div>
        <h2>Choose Size</h2>
        <div class="btn-group">
          <label>
            Width: {{ imgSizes.currentWidth }}
            <input type="range" :value="imgSizes.currentWidth" @input="imgSizes.currentWidth = $event.target.value"
              :min="imgSizes.minWidth" :max="imgSizes.maxWidth">
          </label>
          <label>
            Height: {{ imgSizes.currentHeight }}
            <input type="range" :value="imgSizes.currentHeight" @input="imgSizes.currentHeight = $event.target.value"
              :min="imgSizes.minHeight" :max="imgSizes.maxHeight">
          </label>
        </div>
        <h2>Rotate</h2>
        <div class="btn-group">
          <label>
            Angle: {{ rotate.value }}
            <input type="range" :value="rotate.value" @input="rotate.value = $event.target.value" :min="rotate.min"
              :max="rotate.max">
          </label>
        </div>
        <button @click="isImageVisible = !isImageVisible">
          {{ isImageVisible ? ' Show ' : 'Hide' }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MyComponent',
  data() {
    return {
      isImageVisible: true,
      imgFilters: {
        sepia: false,
        border: false,
        shadow: false
      },
      imgSizes: {
        maxWidth: 680,
        maxHeight: 480,
        minHeight: 300,
        minWidth: 400,
        currentWidth: 680,
        currentHeight: 480
      },
      rotate: {
        min: 0,
        max: 360,
        value: 0
      }
    }
  },
  computed: {
    imgStyles() {
      return {
        width: `${this.imgSizes.currentWidth}px`,
        height: `${this.imgSizes.currentHeight}px`,
        transform: `rotate(${this.rotate.value}deg)`
      }
    }
  }
}
</script>

<style>
.image {
  height: 480px;
  width: 680px;
  background: #808080;
}

img {
  height: 100%;
  width: 100%;
  object-fit: cover;
  transition: 0.2s ease;

  &.sepia {
    filter: sepia(100%);
  }

  &.border {
    border: 5px dashed black;
  }

  &.shadow {
    box-shadow: 7px 7px 10px 0 grey;
  }
}

button {
  margin-right: 10px;

  &.active {
    background-color: aquamarine;
  }
}

h2 {
  margin-bottom: 10px;
}

.btn-group {
  margin-bottom: 20px;
}
</style>

<script>
import Lightbox from 'vue-my-photos'
const photoDir
  = 'https://unpkg.com/vue-my-photos@1.0.0/src/assets/'

const imageList
  = [{
    name: 'mountains.jpg',
    alt: 'The Dolomites',
    filter: 'nature',
    id: 'image1',
  },

  {
    name: 'bird.jpg',
    alt: 'It is a bird on a tree!',
    filter: 'animals',
    id: 'image2',
  },

  {
    name: 'alps.jpg',
    alt: 'I will live here someday',
    filter: 'nature',
    id: 'image3',
  },

  {
    name: 'bear.jpg',
    alt: 'Friendly bear',
    filter: 'animals',
    id: 'image4',
  },

  {
    name: 'canyon.jpg',
    alt: 'A worthy hike',
    filter: 'nature',
    id: 'image5',
  },

  {
    name: 'monumentvalley.jpg',
    alt: 'Monument Valley',
    filter: 'nature',
    id: 'image6',
  },

  {
    name: 'puppy.jpg',
    alt: 'Puppy with a feather',
    filter: 'animals',
    id: 'image7',
  },

  {
    name: 'redwoods.jpg',
    alt: 'Foggy evening in the Redwoods',
    filter: 'nature',
    id: 'image8',
  }]
export default {
  components: {
    Lightbox,
  },
  data() {
    return {
      thumbnailDir: photoDir,
      images: imageList,
      galleryFilter: 'all',
      currentImageName: '',
    }
  },
  computed: {
    filteredImages() {
      if (this.galleryFilter === 'all')
        return this.images
      else
        return this.images.filter(image => image.filter === this.galleryFilter)
    },
  },
  methods: {
    showLightbox(imageName) {
      this.currentImageName = imageName
    },
    onLightboxClose(imageName) {
      this.currentImageName = imageName
    },
    updateFilter(filterName) {
      this.galleryFilter = filterName
    },
  },
}
</script>

<template>
  <div class="detail-posters">
    <div id="filters">
      <form>
        <fieldset>
          <span>
            <input
              id="all" type="radio"
              name="filters" checked
              @click="updateFilter('all')"
            >
            <label for="all">All</label>
          </span>
          <span>
            <input
              id="animals" type="radio"
              name="filters"
              @click="updateFilter('animals')"
            >
            <label for="animals">Animals</label>
          </span>
          <span>
            <input
              id="natue" type="radio"
              name="filters"
              @click="updateFilter('nature')"
            >
            <label for="nature">Nature</label>
          </span>
        </fieldset>
      </form>
    </div>

    <transition-group name="thumbnailfade" tag="div">
      <img
        v-for="thumb in filteredImages"
        :key="thumb.id"
        :src="thumbnailDir + thumb.name"
        :alt="thumb.alt"
        :title="thumb.alt"
        @click="showLightbox(thumb.name)"
      >
    </transition-group>

    <lightbox
      id="mylightbox"
      ref="myLightbox"
      :images="images"
      :directory="thumbnailDir"
      :filter="galleryFilter"
      :timeout-duration="5000"
      :close-on-backdrop-click="true"
      :current-image-name="currentImageName"
      @on-lightbox-close="onLightboxClose"
      @on-lightbox-change="onLightboxChange"
    />
  </div>
</template>

<style scoped>
.detail-posters {
  display: flex;
  flex-direction: column;
  align-items: center;
}

fieldset {
  display: flex;
  justify-content: center;
}

#filters {
  width: 500px;
  margin: 30px auto;
}

#filters span {
  margin: 15px;
}

img {
  width: 470px;
  height: 280px;
  margin: 46px;
  border-radius: 0px;
  cursor: pointer;
  transition: all 0.4s ease;
}

.thumbnailfade-leave-active,
.thumbnailfade-enter-active {
  transition: all 0.4s ease;
}

.thumbnailfade-enter-active {
  transition-delay: 0.4s;
}

.thumbnailfade-enter,
.thumbnailfade-leave-to {
  opacity: 0;
}
</style>

<route lang="yaml">
meta:
  layout: detail
</route>

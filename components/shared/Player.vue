<template>
    <div id="frame">
        <vue-plyr>
            <div v-if="youtubeProgressive" class="plyr__video-embed">
                <iframe
                    v-if="this.videoId"
                    :src="videoSource" 
                    allowfullscreen 
                    allowtransparency 
                    allow="autoplay">
                </iframe>
            </div>
            <div 
                v-else-if="youtubeSimple" 
                data-plyr-provider="youtube" 
                :data-plyr-embed-id="videoId">
            </div>
        </vue-plyr>
    </div>
</template>

<script>
import "vue-plyr";
import "vue-plyr/dist/vue-plyr.css";

import configs from "~/configs/config";

export default {
  props: {
    youtubeProgressive: {
      type: Boolean,
      default: true
    },
    youtubeSimple: {
      type: Boolean,
      default: false
    },
    videoId: {
      type: String,
      default: ""
    }
  },
  computed: {
    videoSource() {
      return `https://www.youtube.com/embed/${
        this.videoId
      }?iv_load_policy=3&modestbranding=1&playsinline=1&showinfo=0&rel=0&enablejsapi=1&origin=${
        configs.baseUrl
      }`;
    }
  }
};
</script>

<style scoped>
#frame {
  border: 2px solid teal;
  margin: 0 auto;
  width: 100%;
}
</style>
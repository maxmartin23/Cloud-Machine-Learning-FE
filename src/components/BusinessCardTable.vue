<template>
  <div>
    <div class="row">
      <div
        v-for="businessCard in businessCards"
        :key="businessCard.id"
        class="col-12 col-md-6 col-lg-4 mb-4"
      >
        <div class="pa-4 blue-grey lighten-5">
          <div class="row">
            <div class="col-md-6">
              <div
                class="business-card-photo"
                :style="`background-image: url(${businessCard.imageUrl})`"
              ></div>
            </div>
            <div class="col-md-6">
              <p v-for="(entity, i) in businessCard.entities" :key="i">
                <span
                  class="
                    text-capitalize
                    font-weight-medium
                    grey--text
                    text--darken-3
                  "
                  >{{ entity.type }}:</span
                >
                &nbsp;
                <span class="font-weight-bold">{{ entity.value }}</span>
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "BusinessCardTable",
  props: {
    businessCards: Array,
  },
};
</script>

<style lang="stylus" scoped>
.business-card-photo {
  aspect-ratio: 3 / 2;
  width: 100%;
  max-width: 100%;
  background-position: center;
  background-size: cover;
}
</style>
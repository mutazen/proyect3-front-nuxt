<template>
  <v-container fluid class="choose">
    <v-row align="center" justify="center" class="mt-5">
      <ButtonRestFilter
        v-if="params"
        :params="params"
        :restaurants="restaurants"
      />
      <v-spacer></v-spacer>
      <v-col class="d-flex justify-end px-lg-15" xs="6" sm="4">
        <v-btn-toggle>
          <nuxt-link
            :to="{ query: { ...params }, params: { ...params }, name: 'search-rest-3' }"
            style="text-decoration: none; color: inherit"
          >
            <v-btn
              v-if="$vuetify.breakpoint.smAndDown"
              class="ma-0"
              color="secondary"
            >
              <v-icon color="white">mdi-arrow-left-bold</v-icon>
            </v-btn>
            <v-btn v-else class="me-2 secondary">VOLVER</v-btn>
          </nuxt-link>
          <nuxt-link
            :to="{ query: { ...params }, name: 'places-results' }"
            style="text-decoration: none; color: inherit"
          >
            <v-btn
              v-if="$vuetify.breakpoint.smAndDown"
              class="mx-2"
              color="#FF9A00"
            >
              <v-icon color="white">mdi-arrow-right-bold</v-icon>
            </v-btn>
            <v-btn v-else dark color="#FF9A00"> SIGUIENTE </v-btn>
          </nuxt-link>
        </v-btn-toggle>
      </v-col>
    </v-row>

    <v-row align="center" justify="center">
      <v-col
        v-for="(price, idx) in prices"
        :key="idx"
        class="px-lg-15"
        cols="12"
        xs="12"
        sm="4"
      >
        <CardRestaurantMobile
          v-if="$vuetify.breakpoint.xs"
          :image="price.image"
          :name="price.price"
          :value="price.value"
          nview="restaurants-results"
        />

        <CardRestaurant
          v-else
          :image="price.image"
          :name="price.price"
          :value="price.value"
          nview="places-results"
        />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const restaurants = await $axios.get('/places/search', {
      params: { ...params },
    })
    if (params === {}) return { restaurants: restaurants.data }

    return { restaurants: restaurants.data, params }
  },
  data() {
    return {
      prices: [
        {
          price: 'Económico (<15€)',
          value: 'Económico',
          image: 'economico.jpg',
        },
        {
          price: 'Moderado (15-25€)',
          value: 'Moderado',
          image: 'moderado.jpg',
        },
        {
          price: 'Elevado (>25€)',
          value: 'Elevado',
          image: 'elevado.jpg',
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
.choose {
  display: absolute;
  width: 100%;
  height: 100%;
}
</style>
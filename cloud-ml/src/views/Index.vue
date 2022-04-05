<template>
  <v-container class="white px-4 px-md-16 py-5" style="min-height: 100%">
    <v-dialog v-model="errorDialog" width="32rem">
      <v-sheet class="pa-4">
        <h2 class="mb-4">Error getting cards</h2>
        <p class="grey--text text--darken-2">
          There was an error getting the cards. Please refresh the page and try
          again.
        </p>
        <v-btn color="primary" rounded class="py-6" @click="retry()">
          Retry
        </v-btn>
      </v-sheet>
    </v-dialog>
    <h1 class="mb-8">Business Card Organizer</h1>
    <div v-if="businessCards">
      <div
        v-if="businessCards.length === 0"
        class="pa-8 blue-grey lighten-5 d-flex align-center"
      >
        <h3>No business cards yet</h3>
      </div>
      <div v-else>
        <div v-for="businessCard in businessCards" :key="businessCard.id">
          {{ businessCard.name }}
        </div>
      </div>
      <div class="mt-8">
        <v-btn color="primary" rounded class="py-6" @click="1">
          <v-icon left> mdi-plus</v-icon> Add new
        </v-btn>
      </div>
    </div>
    <div v-else class="pa-8 blue-grey lighten-5 d-flex align-center">
      <v-progress-circular
        indeterminate
        color="primary"
        size="32"
        width="2"
        class="mr-4"
      ></v-progress-circular>
      <h3>Getting business cards</h3>
    </div>
  </v-container>
</template>

<script>
export default {
  name: "Index",
  data() {
    return {
      errorDialog: false,
      businessCards: null,
    };
  },
  created() {
    
    this.$http
      .get("/business-cards")
      .then(({ data }) => {
        this.businessCards = data;
      })
      .catch(() => {
        this.errorDialog = true;
      });
  },
  methods: {
    retry() {
      window.location.reload();
    },
  },
};
</script>
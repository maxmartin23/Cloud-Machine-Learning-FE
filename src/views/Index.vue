<template>
  <div style="height: 100vh; overflow-y: auto">
    <v-container class="white px-4 px-md-16 py-5 pb-16" style="min-height: 100%">
      <v-dialog v-model="errorDialog" width="32rem">
        <v-sheet class="pa-4">
          <h2 class="mb-4">Error getting cards</h2>
          <p class="grey--text text--darken-2">
            There was an error getting the cards. Please refresh the page and
            try again.
          </p>
          <v-btn color="primary" rounded class="py-6" @click="retry()">
            Retry
          </v-btn>
        </v-sheet>
      </v-dialog>
      <h1>All business cards</h1>
      <h4 class="grey--text text--darken-2 font-weight-medium mb-4">
        Showing {{ businessCards.length }} cards
      </h4>
      <div class="mb-6">
        <v-btn color="primary" class="py-6" @click="1">
          <v-icon left>mdi-plus</v-icon> Add new
        </v-btn>
      </div>
      <div v-if="businessCards">
        <div
          v-if="businessCards.length === 0"
          class="pa-8 blue-grey lighten-5 d-flex align-center"
        >
          <h3>No business cards yet</h3>
        </div>
        <business-card-table :businessCards="businessCards" v-else />
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
  </div>
</template>

<script>
import businessCards from "@/assets/sampledata";
import BusinessCardTable from "../components/BusinessCardTable.vue";
export default {
  name: "Index",
  components: {
    BusinessCardTable,
  },
  data() {
    return {
      errorDialog: false,
      businessCards,
    };
  },
  created() {
    // this.$http
    //   .get("/business-cards")
    //   .then(({ data }) => {
    //     this.businessCards = data;
    //   })
    //   .catch(() => {
    //     this.errorDialog = true;
    //   });
  },
  methods: {
    retry() {
      window.location.reload();
    },
  },
};
</script>
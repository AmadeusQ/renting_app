<template>
  <div class="custom-search-filter">
    <div class="q-mb-sm filter-city">Алматы</div>
    <div class="q-mb-md">
      <q-btn
        style="background-color: #d9d9d9; border-radius: 10px"
        class="q-mr-md"
        @click="activateBtn('buy')"
        :class="search.buyType === 'buy' ? 'active-btn' : ''"
        >{{ $t("searchFilter.buy") }}</q-btn
      >
      <q-btn
        style="background-color: #d9d9d9; border-radius: 10px"
        @click="activateBtn('rent')"
        :class="search.buyType === 'rent' ? 'active-btn' : ''"
        >{{ $t("searchFilter.rent") }}</q-btn
      >
    </div>
    <div class="flex justify-between q-mb-md" style="width: 400px">
      <q-select
        class="q-pt-none"
        dense
        outlined
        stack-label
        v-model="search.roomType"
        style="background-color: white; border-radius: 10px; width: 47%"
        color="black"
        :label="$t('searchFilter.roomType')"
        :options="roomTypes"
        :option-value="'id'"
        :option-label="'name'"
        filled
      />
      <q-input
        class="q-pt-none"
        dense
        type="number"
        step="1"
        min="1"
        outlined
        stack-label
        v-model="search.numOfRooms"
        style="background-color: white; border-radius: 10px; width: 47%"
        color="black"
        :label="$t('searchFilter.numOfRooms')"
      />
    </div>
    <div class="flex justify-between q-mb-lg" style="width: 400px">
      <q-input
        class="q-pt-none"
        dense
        type="number"
        step="10000"
        min="0"
        outlined
        stack-label
        v-model="search.priceFrom"
        style="background-color: white; border-radius: 10px; width: 47%"
        color="black"
        :label="$t('searchFilter.priceFrom')"
      />
      <q-input
        class="q-pt-none"
        dense
        type="number"
        step="10000"
        min="0"
        outlined
        stack-label
        v-model="search.priceTo"
        style="background-color: white; border-radius: 10px; width: 47%"
        color="black"
        :label="$t('searchFilter.priceTo')"
      />
    </div>
    <div class="flex justify-between">
      <q-btn
        style="background-color: #29ca7c; border-radius: 10px"
        class="q-mr-md"
        @click="clearSearch()"
        >{{ $t("searchFilter.clear") }}</q-btn
      >
      <q-btn style="background-color: #29ca7c; border-radius: 10px">{{
        $t("searchFilter.show")
      }}</q-btn>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchFilter",
  data() {
    return {
      search: {
        buyType: "buy",
        numOfRooms: 1,
        priceFrom: 0,
        priceTo: 0,
        roomType: { id: 0, name: this.$t("searchFilter.apartment") },
      },
      roomTypes: [
        { id: 0, name: this.$t("searchFilter.apartment") },
        { id: 1, name: this.$t("searchFilter.house") },
      ],
    };
  },
  methods: {
    activateBtn(buyType) {
      this.search.buyType = buyType;
    },
    clearSearch() {
      this.search.numOfRooms = 1;
      this.search.priceFrom = 0;
      this.search.priceTo = 0;
      this.search.buyType = "buy";
      this.search.roomType = { id: 0, name: this.$t("searchFilter.apartment") };
    },
  },
};
</script>

<style scoped>
.custom-search-filter {
  display: flex;
  margin-top: 100px;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 80%;
  height: 500px;
  border-radius: 15px;
  background-color: #221f1f;
}

.filter-city {
  color: #fff;
  font-size: 48px;
}
.active-btn {
  background-color: #21ab69 !important;
}
</style>

<template>
  <q-page class="">
    <div class="custom-search-filter container">
      <div class="q-mb-sm filter-city">Алматы</div>
      <!-- <div class="q-mb-md">
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
      </div> -->
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
          min="0"
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
        <q-btn
          style="background-color: #29ca7c; border-radius: 10px"
          @click="searchListings()"
          >{{ $t("searchFilter.show") }}</q-btn
        >
      </div>
    </div>
    <q-separator color="black" class="q-my-xl" />
    <div class="listings">
      <ListingItem
        v-for="(item, i) in filteredListings"
        :key="i"
        :item="item"
      />
    </div>
  </q-page>
</template>

<script>
import ListingItem from "src/components/ListingItem.vue";

export default {
  name: "ListingsPage",
  components: { ListingItem },
  data() {
    return {
      search: {
        buyType: "buy",
        numOfRooms: null,
        priceFrom: null,
        priceTo: null,
        roomType: {
          id: 0,
          name: this.$t("searchFilter.apartment"),
          generalName: "apartment",
        },
      },
      roomTypes: [
        {
          id: 0,
          name: this.$t("searchFilter.apartment"),
          generalName: "apartment",
        },
        {
          id: 1,
          name: this.$t("searchFilter.house"),
          generalName: "apartment",
        },
      ],
      listings: [
        {
          desc: "2-комн. квартира, 3 этаж, 45 кв. м., помесячно",
          price: 100000,
          numOfRooms: 2,
          floor: 3,
          area: 90,
          type: "apartment",
        },
        {
          desc: "2-комн. квартира, 6 этаж, 70 кв. м., помесячно",
          price: 200000,
          numOfRooms: 2,
          floor: 6,
          area: 70,
          type: "apartment",
        },
        {
          desc: "3-комн. квартира, 18 этаж, 90 кв. м., помесячно",
          price: 300000,
          numOfRooms: 3,
          floor: 18,
          area: 90,
          type: "apartment",
        },
        {
          desc: "4-комн. квартира, 2 этаж, 120 кв. м., помесячно",
          price: 400000,
          numOfRooms: 4,
          floor: 2,
          area: 120,
          type: "apartment",
        },
        {
          desc: "2-комн. квартира, 3 этаж, 45 кв. м., помесячно",
          price: 100000,
          numOfRooms: 2,
          floor: 3,
          area: 90,
          type: "apartment",
        },
        {
          desc: "2-комн. квартира, 6 этаж, 70 кв. м., помесячно",
          price: 200000,
          numOfRooms: 2,
          floor: 6,
          area: 70,
          type: "apartment",
        },
        {
          desc: "3-комн. квартира, 18 этаж, 90 кв. м., помесячно",
          price: 300000,
          numOfRooms: 3,
          floor: 18,
          area: 90,
          type: "apartment",
        },
        {
          desc: "4-комн. квартира, 2 этаж, 120 кв. м., помесячно",
          price: 400000,
          numOfRooms: 4,
          floor: 2,
          area: 120,
          type: "apartment",
        },
        {
          desc: "2-комн. квартира, 3 этаж, 45 кв. м., помесячно",
          price: 100000,
          numOfRooms: 2,
          floor: 3,
          area: 90,
          type: "apartment",
        },
        {
          desc: "2-комн. квартира, 6 этаж, 70 кв. м., помесячно",
          price: 200000,
          numOfRooms: 2,
          floor: 6,
          area: 70,
          type: "apartment",
        },
        {
          desc: "3-комн. квартира, 18 этаж, 90 кв. м., помесячно",
          price: 300000,
          numOfRooms: 3,
          floor: 18,
          area: 90,
          type: "apartment",
        },
        {
          desc: "4-комн. квартира, 2 этаж, 120 кв. м., помесячно",
          price: 400000,
          numOfRooms: 4,
          floor: 2,
          area: 120,
          type: "apartment",
        },
      ],
      filteredListings: [],
    };
  },
  methods: {
    activateBtn(buyType) {
      this.search.buyType = buyType;
    },
    clearSearch() {
      this.search.numOfRooms = null;
      this.search.priceFrom = null;
      this.search.priceTo = null;
      this.search.buyType = "buy";
      this.search.roomType = {
        id: 0,
        name: this.$t("searchFilter.apartment"),
        generalName: "apartment",
      };
      this.filteredListings = this.listings;
    },
    searchListings() {
      this.filteredListings = this.listings.filter((item) => {
        return (
          (this.search.numOfRooms !== null
            ? item.numOfRooms === parseInt(this.search.numOfRooms, 10)
            : true) &&
          (this.search.priceFrom !== null && !isNaN(this.search.priceFrom)
            ? item.price >= parseInt(this.search.priceFrom, 10)
            : true) &&
          (this.search.priceTo !== null && !isNaN(this.search.priceTo)
            ? item.price <= parseInt(this.search.priceTo, 10)
            : true) &&
          item.type === this.search.roomType.generalName
        );
      });
    },
  },
  mounted() {
    this.filteredListings = this.listings;
  },
};
</script>

<style scoped>
.custom-search-filter {
  display: flex;
  margin-top: 48px;
  flex-direction: column;
  justify-content: center;
  align-items: center;
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
.listings {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  row-gap: 30px;
}
</style>

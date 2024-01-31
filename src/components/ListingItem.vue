<template>
  <q-card class="my-card">
    <q-card-section horizontal>
      <q-img src="https://cdn.quasar.dev/img/parallax2.jpg" class="my-card-img">
        <div class="absolute-bottom text-h6" style="padding: 8px 16px">
          {{ item.price + " ₸" }}
        </div>
      </q-img>

      <q-card-section vertical>
        <div class="flex items-center q-mb-md">
          <q-icon
            name="fa-solid fa-location-dot"
            size="sm"
            class="q-mr-sm"
            style="color: rgb(158, 0, 0)"
          ></q-icon>
          <p class="q-mb-none">Здесь будет адрес</p>
        </div>
        <div class="flex items-center q-mb-md">
          <div class="flex items-center q-mr-md">
            <q-icon
              name="fa-solid fa-door-closed"
              size="sm"
              class="q-mr-sm"
            ></q-icon>
            <p class="q-mb-none">{{ item.numOfRooms }}</p>
          </div>
          <div class="flex items-center q-mr-md">
            <q-icon
              name="fa-regular fa-square"
              size="sm"
              class="q-mr-sm"
            ></q-icon>
            <p class="q-mb-none">{{ item.area + $t("meterSquare") }}</p>
          </div>
          <div class="flex items-center q-mr-md">
            <q-icon
              name="fa-solid fa-building"
              size="sm"
              class="q-mr-sm"
            ></q-icon>
            <p class="q-mb-none">{{ item.floor }}</p>
          </div>
        </div>
        <div>{{ item.desc }}</div>
      </q-card-section>
    </q-card-section>
  </q-card>
</template>

<script>
export default {
  name: "ListingItem",
  props: ["item"],
  data() {
    return {};
  },
};
</script>

<style scoped>
.my-card {
  width: 100%;
}
.my-card-img {
  width: 20%;
}
</style>

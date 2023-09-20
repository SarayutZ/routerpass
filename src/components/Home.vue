<!-- Home.vue -->
<template>
  <div class="container text-center">
    <div class="row">
      <div
        class="col mt-5"
        v-for="(restaurant, index) in travelList"
        :key="index"
      >
        <div class="card" style="width: 18rem">
          <img
            :src="restaurant.imagesP"
            class="card-img-top"
            :width="sizeW"
            :height="sizeH"
          />
          <div class="card-body">
            <h2>ร้านที่ : {{ index+1 }}</h2>
            <h5 class="card-title">ชื่อร้าน : {{ restaurant.name }}</h5>
            <p class="card-text">ราคาเริ่ม : {{ restaurant.price }}</p>
            <button
              class="btn btn-danger"
              data-bs-toggle="modal"
              data-bs-target="#staticBackdrop"
              @click="goToOtherComponent(restaurant.name, restaurant.imagesP,index)"
            >
              จองร้าน
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'; // import ref

export default {
  methods: {
    goToOtherComponent(name, imagesP,index) {
      // ส่งค่าไปยังคอมโพเนนต์ OtherComponent.vue ผ่านคิวรี่พารามิเตอร์
      this.$router.push({
        name: 'other',
        query: {
          index:index,
          restaurantName: name,
          restaurantImagesP: imagesP,
        },
      });
    },
  },
  setup() {
    const travelList = ref([
      
        {
    name: "ร้าน ก๋วยเตี๋ยว",
    price: 1500,
    imagesP:
      "https://i.pinimg.com/564x/e7/df/6d/e7df6d197bb73f8177549c69d2229b00.jpg",
  },
  {
    name: "ร้าน ผัดไทย",
    price: 70,
    imagesP:
      "https://i.pinimg.com/736x/98/9a/e6/989ae63f69fa7dcc0927ea1323209bb3.jpg",
  },
  {
    name: "ร้าน กะเพราหมูสับ",
    price: 45,
    imagesP:
      "https://i.pinimg.com/564x/f6/f2/86/f6f286c357db32aad0d5f5ffe5846356.jpg",
  },
  {
    name: "ร้าน มาม่าผัดขี้เมา",
    price: 65,
    imagesP:
      "https://i.pinimg.com/564x/f5/e0/de/f5e0de18579b1f6900e86b1087468df3.jpg",
  },
  {
    name: "ร้าน ส้มตำ",
    price: 40,
    imagesP:
      "https://i.pinimg.com/736x/d9/62/af/d962af31373b46a60c6d60d28afca945.jpg",
  },
    ]);

    const sizeW = 350;
    const sizeH = 250;

    return { // return ตัวแปรออกมาจาก setup
      travelList,
      sizeW,
      sizeH,
    };
  },
};
</script>

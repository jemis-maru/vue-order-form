<template>
  <div>
    <div>
      <h1 class="title">Services</h1>
    </div>
    <div class="list-container">
      <div
        class="list"
        :class="{ selectedItem: service.active }"
        v-for="(service, index) in services"
        :key="service.name"
        @click="selectItem(index)"
      >
        <p class="test">{{ service.name }}</p>
        <p>$ {{ service.price }}</p>
      </div>
    </div>
    <div class="hr-line"></div>
    <div class="list total-container">
      <p>Total:</p>
      <p>$ {{ totalPrice }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      services: [
        {
          name: "Web Development",
          price: 300,
          active: true,
        },
        {
          name: "Design",
          price: 400,
          active: false,
        },
        {
          name: "Integration",
          price: 250,
          active: false,
        },
        {
          name: "Training",
          price: 220,
          active: false,
        },
      ],
    };
  },
  methods: {
    selectItem(index){
      this.services[index].active = !this.services[index].active;
    },
  },
  computed: {
    totalPrice(){
      let sum = 0;
      this.services.forEach(item => {
        if(item.active){
          sum = sum + item.price;
        }
      });
      return sum;
    },
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  background-color: #01a5c2;
}
.title {
  text-align: center;
}
.list-container {
  margin-top: 40px;
}
.test{
  /* font-size: 500; */
}
.list {
  display: flex;
  justify-content: space-between;
  font-size: 20px;
  font-weight: bold;
  margin: auto;
  margin-top: 10px;
  max-width: 500px;
  padding: 10px;
  background-color: #e65773;
  cursor: pointer;
}
.selectedItem {
  background-color: #76e497;
}
.hr-line{
  margin: auto;
  margin-top: 30px;
  max-width: 700px;
  border: none;
  border-bottom: 1px solid #000000;
}
.total-container{
  background: none;
  margin-top: 30px;
}
</style>

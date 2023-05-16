<script setup>
import { ref } from "vue";

const sportSelect = ref("");
const dataequipments = ref("");
const sports = [
  {
    name: "Football",
    bg_color: "#6bb46e",
    equipments: ["Ball", "Football Shoes", "Goalpost"],
  },
  {
    name: "Volleyball",
    bg_color: "#c30f42",
    equipments: ["Ball", "Nets"],
  },
  {
    name: "Badminton",
    bg_color: "#2a82be",
    equipments: ["Shuttlecock", "Nets", "Racket"],
  },
];

const color = ref("");

const name = (e) => {
  sportSelect.value = e.target.value;
  sports.map((sport) => {
    if (sport.name === e.target.value) {
      dataequipments.value = sport.equipments;
      color.value = sport.bg_color;

      if (sport.name === "Badminton") {
        document.querySelector(".card-me").style.transform = "translateY(85px)";
        const badminton = document.getElementById("badminton");
        console.log(badminton);
        const position = badminton.getBoundingClientRect();
        console.log(position);
      } else if (sport.name === "Volleyball") {
        // document.querySelector(".card-me").style.background = "green";
        document.querySelector(".card-me").style.transform = "translateX(85px)";
        const vollyball = document.getElementById("volleybal");
        const position = vollyball.getBoundingClientRect();
        console.log(position);
        console.log(vollyball);
      } else if (sport.name === "Football") {
        document.querySelector(".card-me").style.transform =
          "translateX(-85px)";

        const foodball = document.getElementById("foodball");
        console.log(foodball);

        const position = foodball.getBoundingClientRect();
        console.log(position);
        // change position of card-me
      }
    }
  });
};
</script>

<template>
  <div>
    <p>Do tyou want mantan</p>
    <div class="container-radio">
      <div
        class="container-radio gap-4"
        v-for="(sporte, index) in sports"
        :key="index"
      >
        <input type="radio" id="sport" :value="sporte.name" @click="name" />
        <p>{{ sporte.name }}</p>
      </div>
    </div>

    <div class="container-iamge" :style="{ background: color }">
      <div class="content-top">
        <div class="content">
          <div class="card" id="foodball">
            <p>foodball</p>
          </div>
        </div>
        <div class="content">
          <div class="card" id="volleybal">
            <p>Volleyball</p>
          </div>
        </div>
      </div>
      <div class="conetent-center">
        <div class="card card-me">
          <p>ME</p>
        </div>
      </div>
      <div class="content-bottom">
        <div class="card" id="badminton">
          <p>Badminton</p>
        </div>
      </div>
    </div>
    <div>select Sport:{{ sportSelect }}</div>
    equipments:
    <div v-for="(sporte, index) in dataequipments" :key="index">
      <li>{{ sporte }}</li>
    </div>
  </div>
</template>

<style scoped>
.container-radio {
  display: flex;
  justify-content: space-between;
}
.container-iamge {
  width: 300px;
  height: 250px;
  background-color: #fff;
  padding: 20px;
}

.content-top {
  display: flex;
  justify-content: space-between;
}

.conetent-center {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 10px 0;
}

.content-bottom {
  display: flex;
  justify-content: center;
  align-items: center;
}

.card {
  color: black;
  border: 1px solid black;
  width: 30px;
  height: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.card.card-me {
  color: #fff;
  background: black;
  border: 1px solid black;
  width: 30px;
  height: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}
</style>

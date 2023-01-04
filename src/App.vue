<template>
  <div>
    <div>
      <button @click="AddCircles()" class="addmargin">Add circle</button>
    </div>
    <div class="addmargin">Number of Grey circles : {{ NumberOfGreyCircles }}</div>
    <div v-for="(itm, idx) in CirclesList" :key="idx">
      <div :class="itm.bg_color == false ? 'circle' : 'colorCircle'" :key="idx" @click="addbackgroundColor(idx)"></div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    NumberOfGreyCircles: 0,
    CirclesList: [],
  }),
  mounted() {
    this.CirclesList = [];
  },
  methods: {
    AddCircles() {
      if (this.CirclesList.length == 0) {
        this.CirclesList.push({ id: 1, bg_color: false });
      } else {
        this.CirclesList.push({ id: this.CirclesList.length + 1, bg_color: false });
      }
    },
    addbackgroundColor(idx) {
      this.CirclesList[idx].bg_color = this.CirclesList[idx].bg_color == true ? false : true;
      let InitNumber = 0;
      this.CirclesList.forEach((itm) => {
        if (itm.bg_color == true) {
          InitNumber += 1;
        }
      });
      this.NumberOfGreyCircles = InitNumber;
    },
  },
};
</script>

<style>
.addmargin {
  margin-top: 20px;
}

.circle {
  border-radius: 50%;
  width: 100px;
  height: 100px;
  border: 1px solid black;
  margin: 10px;
}

.colorCircle {
  border-radius: 50%;
  width: 100px;
  height: 100px;
  border: 1px solid black;
  margin: 10px;
  background-color: grey;
}
</style>

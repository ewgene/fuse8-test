<template>
  <div id="Homes">
    <div class="header">
      <h1>Our Latest Developments</h1>
      <label for="filter">Filter</label>
      <input type="text" id="filter" />
    </div>
    <div v-for="house in homes"
      v-bind:key="house.id"
      class="house"
      :class="house.type">
      <div class="image">
        <p class="type">{{ house.type }}</p>
      </div>
      <div class="bottom">
        <p class="title">{{ house.title }}</p>
        <p class="address">{{ house.address }}</p>
        <p class="price">New Properties for Sale from <span>£{{ house.price }}</span></p>
        <p class="desc">Shared Ownership Available</p>
      </div>
    </div>
    <div class="footer">
      <button class="more">See more</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data () {
    return {
      homes: []
    }
  },
  created () {
    axios
      .get('https://603e38c548171b0017b2ecf7.mockapi.io/homes')
      .then(response => (this.homes = response.data))
  },
  watch: {
    homes: {
      handler () {
        for (let i = 0; i < this.homes.length; i++) {
          this.homes[i].price = this.homes[i].price.toLocaleString('en')
        }
      }
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#Home {
  width: 1180px;
}
.header {
  width: 100%;
  height: 224px;
  position: relative;
}
h1 {
  font-family: Open Sans;
  font-size: 36px;
  font-style: normal;
  font-weight: 700;
  line-height: 49px;
  letter-spacing: 0px;
  text-align: center;
  color: #45852D;
}
#filter {
  position: absolute;
  top: 129px;
  left: 117px;
  width: 418px;
  height: 50px;
  border: 1px solid #D8D8D8;
  box-sizing: border-box;
  border-radius: 25px;
}
label {
  position: absolute;
  top: 141px;
  left: 70px;
  width: 195px;
  height: 26px;
  font-family: Open Sans;
  font-size: 16px;
  font-style: normal;
  font-weight: 700;
  line-height: 24px;
  letter-spacing: -0.3px;
  text-align: left;
}
.house {
  width: 380px;
  height: 380px;
  margin: 10px;
  display: inline-block;
  border: 1px solid #D8D8D8
}
.image {
  width: 380px;
  height: 227px;
  background-image: url(../assets/house.png);
  background-position: top center;
  background-repeat: no-repeat;
  position: relative;
}
.bottom {
  padding: 0 20px;
}
.bottom > * {
  font-family: Open Sans;
  text-align: left;
  margin: 5px 0;
  letter-spacing: 0px;
}
.type {
  width: 134px;
  height: 30px;
  background-color: #006F79;
  color: #FFF;
  position: absolute;
  margin: 0;
  bottom: 0;
  right: 0;
  text-align: center;
  font-family: Open Sans;
  font-size: 12px;
  font-style: normal;
  font-weight: 700;
  line-height: 30px;
}
.title {
  font-size: 20px;
  font-style: normal;
  font-weight: 700;
  line-height: 27px;
  margin-top: 15px;
}
.address {
  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 22px;
}
.price {
  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 22px;
  margin-top: 15px;
}
span {
  font-weight: 700;
}
.desc {
  font-size: 14px;
}
.footer {
  position: relative;
  width: 100%;
  height: 185px;
  text-align: center;
  padding-top: 30px;
}
.more {
  width: 150px;
  height: 50px;
  border: 1px solid #D8D8D8;
  box-sizing: border-box;
  border-radius: 25px;
  display: inline-block;
  font-family: Open Sans;
  font-style: normal;
  font-weight: bold;
  font-size: 16px;
  line-height: 24px;
  letter-spacing: -0.3px;
  color: #363636;
}
</style>

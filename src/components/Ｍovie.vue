<script setup>
import { onMounted, ref } from "vue";

const itemNum = ref(3);

const startNum = ref(0);

const teamEnd = ref(3);

const movieArray = ref([
  {
    name: "商品1",
    price: 555,
  },
  {
    name: "商品2",
    price: 555,
  },
  {
    name: "商品3",
    price: 555,
  },
  {
    name: "商品4",
    price: 555,
  },
  {
    name: "商品5",
    price: 555,
  },
  {
    name: "商品6",
    price: 555,
  },
  {
    name: "商品7",
    price: 555,
  },
  {
    name: "商品8",
    price: 555,
  },
  {
    name: "商品9",
    price: 555,
  },
]);

const nextStep = () => {
  //第一次 3                                // 9
  //第二次 6                                 // 9
  //第三次 9                                 // 9
  if (startNum.value + itemNum.value < movieArray.value.length) {
    //第一次 6       // 3            // 3
    //第二次  9       // 6             // 3
    // 第三次 12        // 9            // 3
    teamEnd.value = teamEnd.value + itemNum.value;

    //第一次  3          //  0            //   3
    // 第二次 6          // 3            // 3
    //  第三次 9          // 6              // 3
    startNum.value = startNum.value + itemNum.value;

    console.log("end範圍", teamEnd.value);
    console.log("start", startNum.value);
    console.log(movieArray.value);
  } else {
    console.log("已超出");
    teamEnd.value = 9;
    startNum.value = 6;
  }
};
</script>

<template>
  <div class="movie-box">
    <div class="title">
      <span></span>
      <h2 class="title-text">即將上映000</h2>
    </div>
    <div class="time-box">
      <div class="time-line"></div>

      <div class="circle-box">
        <div class="circle-father">
          <div class="semicircle"></div>
          <div class="date">
            <p class="date-text">5月31日</p>
          </div>
          <div
            class="movie-pic"
            v-for="item in movieArray.slice(startNum, teamEnd)"
            :key="item.key"
          >
            {{ item.name }}
            <br />
            {{ item.price }}
            <!-- <img
              src="https://image.tmdb.org/t/p/w500/zuXZnzHvXdWyVDVPZcLvPNrKvEq.jpg"
              style="width: 181px; height: 271px"
              alt=""
            /> -->
          </div>
        </div>
        <!--  -->
      </div>
    </div>

    <button @click="nextStep" class="nextStep">➡️</button>
    <button class="returnStep">⬅️</button>
  </div>
</template>

<style lang="scss" scoped>
* {
  border: none !important;
}

.movie-box {
  background-color: var(--color-gray-50);
  box-shadow: 10px 10px 5px #888888;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 1rem;
  .title {
    width: 100%;
    display: flex;

    justify-content: flex-start;
    align-items: center;
    padding-left: 2.5rem;
    gap: 0.5rem;
    span {
      background-color: blue;
      display: block;
      width: 1rem;
      height: 1rem;

      border-radius: 0.25rem;
    }
  }
  .time-box {
    width: 100%;
    display: flex;
    // border: 10px solid gray;
    flex-direction: column;
    // gap: 10rem;
    padding: 0.5rem 0;
    position: relative;
    .time-line {
      width: 100%;
      border: 0.1rem solid gray !important;
      position: absolute;
      top: 28px;
    }
    .circle-box {
      width: 270px;
      overflow: hidden;
      align-items: center;
      display: flex;
      border: 8px solid green !important;
      gap: 0.5rem;
      // justify-content: space-around;
      margin: 0 auto;
      .circle-father {
        gap: 0.5rem;
        border: 6px solid orange;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        width: 200px;

        .semicircle {
          width: 15px;
          height: 15px;
          background-color: gray;
          border-radius: 100%;
          border-bottom: 1px solid hotpink;
        }
        .date {
          width: 5rem;
          color: rgb(19, 126, 49);
          text-align: center;
          border: 2px solid turquoise;
          padding: 0.5rem 0;

          .date-text {
            text-align: center;
            color: rgb(24, 170, 70);
            border: 7px solid rebeccapurple;
          }
        }
        .movie-pic {
          display: flex;
          flex-direction: col;

          color: #888888;
        }
      }
    }
  }
  button {
    padding: 20px;
    border-radius: 100%;
    font-size: 1.5rem;
  }
}

.range {
  border: 3px solid red !important;
}
</style>

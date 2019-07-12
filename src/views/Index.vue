<template>
  <div class="timer">
    <div class="left">
      <div class="container">
        <div class="mission">
          <input type="text" class="add" placeholder="ADD A NEW MISSION" />
          <span>+</span>
        </div>
        <div class="first">
          <div class="circle"></div>
          <input type="text" placeholder="THE FIRST THING TO DO TODAY" class="fir" />
        </div>
        <div class="clock">{{timer}}</div>
        <div class="box">
          <div class="lists">
            <div class="circle"></div>
            <input type="text" class="list" />
            <img src="@/assets/icons/playBtn.png" class="playBtn" alt />
          </div>
        </div>

        <p class="more">MORE</p>
      </div>
      <div class="count">
        <div class="circle">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="60"
            height="60"
            viewBox="0 0 24 24"
            fill="#FF4384"
          >
            <path d="M8 5v14l11-7z" />
            <path d="M0 0h24v24H0z" fill="none" />
          </svg>
        </div>
        
      </div>
      <div class="progress"></div>
    </div>
    <div class="right">
      <ul class="nav">
        <li @click="open">
          <img src="@/assets/icons/list.png" alt />
        </li>
        <li>
          <img src="@/assets/icons/chart.png" alt />
        </li>
        <li>
          <img src="@/assets/icons/music.png" alt />
        </li>
      </ul>
    </div>
    <transition name="pop">
      <todo v-if="isTodo" @close="isTodo=false"></todo>
    </transition>
  </div>
</template>

<script>
import todo from "@/components/Todo.vue";
export default {
  components: { todo },
  data() {
    return {
      list: [],
      timer: "25:00",
      isTodo: false
    };
  },
  methods: {
    open() {
      this.isTodo = true;
    }
  }
};
</script>

<style lang="scss" scoped>
$pink: #ff4384;
.timer {
  width: 1280px;
  height: 800px;
  display: flex;
  box-sizing: border-box;
  margin: 0 auto;
  .left {
    width: 830px;
    background: #ffedf7;
    padding-top: 48px;
    padding-left: 58px;
    margin-right: 0;
    position: relative;
    .container {
      width: 454px;
      .mission {
        height: 58px;
        line-height: 58px;
        display: flex;
        align-items: center;
        position: relative;
        .add {
          width: 445px;
          height: 40px;
          border: none;
        }
        .add::placeholder {
          font-size: 16px;
          color: $pink;
          font-style: italic;
          font-weight: bold;
        }
        span {
          font-size: 28px;
          font-weight: 900;
          left: 420px;
          position: absolute;
          color: $pink;
        }
      }
      .first {
        margin-top: 104px;
        width: 100%;
        display: flex;
        align-items: flex-start;
        .circle {
          box-sizing: border-box;
          width: 48px;
          height: 48px;
          border-radius: 50%;
          border: 2px solid #003164;
        }
        .fir {
          border: none;
          background: #ffedf7;
          flex-grow: 1;
          height: 28px;
          margin-left: 16px;
        }
        .fir::placeholder {
          font-size: 24px;
          color: #003164;
          font-weight: 700;
        }
      }
      .clock {
        font-size: 176px;
        color: $pink;
        font-weight: 700;
      }
      .box {
        width: 445px;
        height: 114.5px;
        margin-top: 107px;
        .lists {
          width: 100%;
          height: 28px;
          display: flex;
          border-bottom: 1px solid rgba(0, 49, 100, 0.2);
          padding-bottom: 10px;
          margin-bottom: 9px;
          .circle {
            box-sizing: border-box;
            width: 24px;
            height: 24px;
            border-radius: 50%;
            border: 2px solid #003164;
          }
          .list {
            height: 19px;
            margin-left: 4px;
            width: 90%;
            border: none;
            background: #ffedf7;
            margin-left: 4px;
          }
          .list::placeholder {
            font-size: 16px;
            color: #003164;
            font-weight: 700;
          }
          .playBtn {
            width: 24px;
            height: 24px;
          }
        }
      }
      .more {
        text-align: end;
        font-size: 16px;
        color: $pink;
        font-weight: bold;
      }
    }
    .count {
      width: 540px;
      height: 540px;
      border-radius: 50%;
      border: 4px solid $pink;
      position: absolute;
      left: 580px;
      top: 130px;
      display: flex;
      align-items: center;
      justify-content: center;

      z-index: 9;
      // background-image: radial-gradient(
      //   circle,
      //   $pink 260px,
      //   rgba(255, 255, 255, 0) 10px
      // );
      .circle {
        width: 96px;
        height: 96px;
        border-radius: 50%;
        background: white;
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 9;
      }
      
    }
    // .progress {
    //   position: absolute;
    //     width: 541px;
    //     height: 541px;
    //     background-image: linear-gradient(to right, transparent 50%, $pink 0);
    //     border-radius: 50%;
    //     z-index: 0;
    //   left: 580px;
    //   top: 130px;
    //   }
    //   .progress::before {
    //     content: "";
    //     display: block;
    //     margin-left: 50%;
    //     height: 100%;
    //     background: rgba(255, 255, 255, 0);
    //     border-radius: 0 100% 100% 0 / 50%;
    //     transform-origin: left;
    //     transform: rotate(1turn);
    //     // z-index: 1;
    //   }
  }

  .right {
    width: 450px;
    background: #003164;
    text-align: end;
    ul {
      margin-right: 85px;
      padding-top: 48px;
      list-style: none;
      li {
        margin-bottom: 48px;
      }
    }
  }
}

.pop-enter-active {
  transition: 0.25s;
  transform: scale(1);
}

.pop-enter {
  transform: scale(0);
}

.pop-leave-active {
  transition: 0.25s;
  transform: scale(0);
}
.pop-leave {
  transform: scale(1);
}
</style>

<template>
  <div class="todo">
    <div class="left">
      <ul class="nav">
        <li class="active">
          <img src="@/assets/icons/list.png" alt />
          <span>TO-DO LIST</span>
        </li>
        <li>
          <img src="@/assets/icons/chart.png" alt />
          <span>ANALYTICS</span>
        </li>
        <li>
          <img src="@/assets/icons/music.png" alt />
          <span>RINGTONES</span>
        </li>
      </ul>

      <div class="semicircle">
        <div class="count">
          <div class="playBtn">
            <svg
              class="btn"
              xmlns="http://www.w3.org/2000/svg"
              width="45"
              height="45"
              viewBox="0 0 24 24"
              fill="#ffffff"
            >
              <path d="M8 5v14l11-7z" />
              <path d="M0 0h24v24H0z" fill="none" />
            </svg>
          </div>
        </div>
        <div class="timer">{{timer}}</div>
        <div class="task">{{task}}</div>
      </div>
    </div>
    <div class="right">
      <div class="mission">
        <input type="text" class="add" placeholder="ADD A NEW MISSION" />
        <span>+</span>
      </div>
      <div class="listNav">
        <span>TO-DO</span>
        <img src="@/assets/icons/arrowup.png" alt />
      </div>
      <div class="lists">
        <div class="circle"></div>
        <input type="text" class="list" />
        <img src="@/assets/icons/playBtn.png" class="playBtn" alt />
      </div>
      <div class="listNav">
        <span>DONE</span>
        <img src="@/assets/icons/arrowup.png" alt />
      </div>
    </div>
    <img class="close" src="@/assets/icons/close.png" @click="close" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      timer: "25:00",
      task: "THE FIRST THING TO DO"
    };
  },
  methods:{
    close(){
      this.$emit("close")
    }
  }
};
</script>


<style lang="scss" scoped>
$pink: #ff4384;
.todo {
  width: 1280px;
  height: 800px;
  background: #003164;
  position: fixed;
  display: flex;
  padding-top: 48px;
  .left {
    width: 350px;
    height: 100%;
    margin-left: 85px;
    ul {
      list-style: none;
      padding-left: 0;
      margin-top: 0;
      li {
        margin-bottom: 42px;
        display: flex;
        align-content: center;
        span {
          font-size: 36px;
          color: rgba(255, 255, 255, 0.2);
          font-weight: bold;
          margin-left: 8px;
        }
        &.active {
          span {
            color: $pink;
          }
        }
      }
    }
    .semicircle {
      width: 350px;
      height: 175px;
      margin-top: 375px;
      background: #ffedf7;
      border-top-left-radius: 180px;
      border-top-right-radius: 180px;
      overflow: hidden;
      display: inline-block;
      .count {
        box-sizing: border-box;
        position: absolute;
        width: 97px;
        height: 97px;
        border: 5px solid #003164;
        border-radius: 50%;
        z-index: 99;
        background: $pink;
        top: 622px;
        left: 212px;
        .playBtn {
          box-sizing: border-box;
          position: absolute;
          left: 2px;
          top: 2px;
          width: 83px;
          height: 83px;
          border-radius: 50%;
          border: 6px solid #003164;
          .btn {
            margin-left: 13px;
            margin-top: 13px;
          }
        }
      }
      .timer {
        margin-top: 50px;
        font-size: 64px;
        text-align: center;
        font-weight: bold;
        color: $pink;
      }
      .task {
        font-size: 16px;
        text-align: center;
        color: #003164;
        font-weight: bold;
      }
    }
  }
  .right {
    width: 445px;
    height: 100%;
    margin-left: 125px;
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
    .listNav {
      margin-top: 48px;
      height: 44px;
      width: 100%;
      line-height: 44px;
      background: rgba(255, 255, 255, 0.2);
      color: #ffffff;
      font-size: 24px;
      // padding-left: 16px;
      // padding-right: 16px;
      display: flex;
      justify-content: space-between;
      span {
        margin-left: 16px;
      }
      .img {
        height: 24px;
      }
    }
    .lists {
      width: 100%;
      height: 28px;
      display: flex;
      border-bottom: 1px solid rgba(255, 255, 255, 0.2);
      padding-bottom: 10px;
      margin-top: 16px;
      margin-bottom: 9px;
      .circle {
        box-sizing: border-box;
        width: 24px;
        height: 24px;
        border-radius: 50%;
        border: 2px solid #ffffff;
      }
      .list {
        height: 19px;
        margin-left: 4px;
        width: 90%;
        border: none;
        background: #003164;
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
  .close{
    height: 48px;
    margin-left: 142px;
  }
}
</style>

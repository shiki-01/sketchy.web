<script lang="ts">
  import logo from "$lib/assets/sketchy_title.svg";

  import { themeList } from "$lib/theme/themeList";
  import { currentTheme } from "$lib/theme/theme";
  let theme = false;

  $: {
    themeList.forEach((item) => {
      currentTheme.update((value) => {
        value[item.name] = theme ? item.mode.dark : item.mode.light;
        return value;
      });
    });
  }
</script>

<div id="wrap">
  <div id="head">
    <div id="picture">
      <div class="slider">
        <img
          src="https://placehold.jp/1500x1500.png"
          class="slide-01"
          alt="slide"
        />
        <img
          src="https://placehold.jp/1500x1501.png"
          class="slide-02"
          alt="slide"
        />
        <img
          src="https://placehold.jp/1500x1502.png"
          class="slide-03"
          alt="slide"
        />
        <div>
          <p>スケッチ</p>
          <img src={logo} alt="logo" />
        </div>
      </div>
    </div>
  </div>
  <div id="mainContent">
    <h1 style="color: {$currentTheme.main.color};">
      それはまるで、スケッチのように
    </h1>
    <a class="download" href="/download">sketchyを手に入れる！</a>
    <div>
      <p style="color: {$currentTheme.main.color};">
        スケッチのようなデザインで、
        <br />
        あなたのアプリケーションを作成しましょう！
      </p>
    </div>
  </div>
</div>

<style lang="scss">
  #head {
    #picture {
      .slider {
        position: relative;
        width: calc(100% - 2rem);
        height: 60vh;
        overflow: hidden;
        margin: 0 auto;

        .slide-01,
        .slide-02,
        .slide-03 {
          position: absolute;
          top: 0;
          left: 0;
          width: 100%;
          height: 100%;
          background-size: cover;
          object-fit: cover;
          background-repeat: no-repeat;
        }

        .slide-01 {
          animation: slide-animation-01 24s infinite;
        }

        .slide-02 {
          animation: slide-animation-02 24s infinite;
        }

        .slide-03 {
          animation: slide-animation-03 24s infinite;
        }

        @keyframes slide-animation-01 {
          0% {
            opacity: 1;
            transform: scale(1);
          }
          30% {
            opacity: 1;
          }
          40% {
            opacity: 0;
            transform: scale(1.15);
          }
          90% {
            opacity: 0;
          }
          100% {
            opacity: 1;
            transform: scale(1);
          }
        }
        @keyframes slide-animation-02 {
          0% {
            opacity: 0;
          }
          30% {
            opacity: 0;
            transform: scale(1.1);
          }
          40% {
            opacity: 1;
          }
          60% {
            opacity: 1;
          }
          70% {
            opacity: 0;
            transform: scale(1);
          }
          100% {
            opacity: 0;
          }
        }
        @keyframes slide-animation-03 {
          0% {
            opacity: 0;
          }
          60% {
            opacity: 0;
            transform: scale(1);
          }
          70% {
            opacity: 1;
          }
          90% {
            opacity: 1;
          }
          100% {
            opacity: 0;
            transform: scale(1.1);
          }
        }

        &:after {
          content: "";
          position: absolute;
          top: 0;
          left: 0;
          width: 100%;
          height: 100%;
          background-color: rgba(238, 238, 238, 0.5);
        }

        div {
          position: absolute;
          width: 60%;
          top: 50%;
          left: 50%;
          transform: translate(-50%, -50%);
          z-index: 2;
          text-align: center;

          p {
            font-size: 2rem;
            color: white;
          }
        }
      }
    }
  }

  #mainContent {
    text-align: center;
    width: 100%;

    h1 {
      font-size: 4rem;
      margin: 2rem 0;
      transition: all 0.3s;
    }

    .download {
      display: inline-block;
      padding: 1rem 2rem;
      background-color: #ff6f61;
      color: white;
      text-decoration: none;
      border-radius: 0.5rem;
      font-size: 1.5rem;
      margin-top: 2rem;
      margin-bottom: 2rem;

      &:hover {
        background-color: #ff4f3f;
      }
    }
  }
</style>
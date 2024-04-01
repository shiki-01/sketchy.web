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

<header style="background-color: {$currentTheme.header.background};">
  <div id="logo">
    <a href="/"><img src={logo} alt="logo" /></a>
  </div>
  <div id="menu">
    <div id="link">
      <div id="home">
        <a href="/" style="color: {$currentTheme.header.color};">Home</a>
      </div>
      <div id="about">
        <a href="/about" style="color: {$currentTheme.header.color};">About</a>
      </div>
      <div id="learn">
        <a href="/learn" style="color: {$currentTheme.header.color};">Learn</a>
      </div>
      <div id="download">
        <a href="/download" style="color: {$currentTheme.header.color};"
          >Download</a
        >
      </div>
    </div>
    <div id="theme">
      <input type="checkbox" id="color" name="color" bind:checked={theme} />
      <label for="color"><span></span></label>
    </div>
    <div id="lang">
      <select>
        <option value="ja">日本語</option>
        <option value="en">English</option>
      </select>
    </div>
  </div>
</header>
<main style="background-color: {$currentTheme.main.background};">
  <slot />
</main>
<footer style="background-color: {$currentTheme.header.background};">
  <p style="color: {$currentTheme.header.color};">
    © 2024 <a href="https://github.com/shiki-01" style="color: {$currentTheme.header.color};">🔗shiki-01</a>
  </p>
</footer>

<style lang="scss">
  :global(body) {
    font-family: "M PLUS 1", sans-serif;
    font-weight: 500;
    font-style: normal;
  }

  main {
    margin-top: 3rem;
    padding: 1rem;
    width: 100%;
    min-height: calc(100vh - 3rem - 2rem - 200px);
    transition: all 0.3s;
  }

  header {
    z-index: 1000;
    width: 100%;
    height: 3rem;
    position: fixed;
    top: 0;
    transition: all 0.3s;
    display: grid;
    padding: 0 1rem;
    grid-template-columns: 6rem 1fr;
    gap: 1rem;
    align-items: center;

    #logo {
      display: grid;
      align-items: center;
      grid-column: 1 / 2;
      width: 100%;
      height: 3rem;

      a {
        display: grid;
        align-items: center;
        cursor: pointer;
      }
    }

    #menu {
      display: grid;
      grid-column: 2 / 3;
      grid-template-columns: 22rem 1fr 4rem 6rem;
      gap: 1rem;
      justify-items: center;
      align-items: center;
      height: 3rem;

      #link {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 1rem;
        justify-items: center;
        align-items: center;
        height: 3rem;

        div {
          display: grid;
          justify-items: center;
          align-items: center;
          height: 3rem;

          a {
            display: block;
            width: 100%;
            height: 100%;
            text-align: center;
            line-height: 3rem;
            text-decoration: none;
            transition: all 0.3s;

            &:hover {
              text-decoration: underline;
            }
          }
        }
      }

      #theme {
        grid-column: 3 / 4;
      }

      #lang {
        grid-column: 4 / 5;
        width: 6rem;
        height: 3rem;
        display: grid;
        align-items: center;

        select {
          display: block;
          width: 6rem;
          height: 2rem;
          background: #f0f0f0;
          border: none;
          border-radius: 0.3rem;
          cursor: pointer;
          padding: 0 0.6rem;
          font-size: 1rem;
          color: #000;
          appearance: none;
        }
      }
    }

    #theme {
      display: block;
      grid-column: 2 / 3;
      width: 4rem;
      height: 3rem;

      label {
        display: flex;
        align-items: center;
        width: 4rem;
        height: 1.8rem;
        margin: 0.6rem 0;
        background: #f0f0f0;
        border-radius: 2rem;
        cursor: pointer;

        span {
          display: block;
          width: 1.5rem;
          height: 1.5rem;
          background: #b4b4b4;
          border-radius: 50%;
          transform: translateX(calc(0.3rem / 2));
          transition: all 0.3s;
        }
      }

      input {
        display: none;

        &:checked ~ label span {
          transform: translateX(calc(4rem - 1.5rem - 0.3rem / 2));
        }
      }
    }
  }

  footer {
    width: 100%;
    height: 200px;
    margin-top: 2em;
    text-align: center;
    display: grid;
    align-items: center;
    transition: all 0.3s;

    p {
      transition: all 0.3s;
      a {
        text-decoration: none;
        transition: all 0.3s;

        &:hover {
          text-decoration: underline;
        }
      }
    }
  }
</style>

<script>
  import JoinButton from "$lib/components/Button.svelte";
  import { onMount } from "svelte";
  let loadingArr = "LOADING...".split("");
  let textArr = ["DISCOVER", "CREATE", "LISTEN", "REPEAT"];
  const BASE_URL = "https://api.unsplash.com/";
  const photoKey = "FkjKMeG-arrW_qolpGUoya8HBCEBUCkjH3j9BB2dwms";
  let y;
  $: innerHeight = 0;
  $: outerHeight = 0;
  let bg = [];
  let middlePhoto = [];

  onMount(async () => {
    /**
     * Delays the execution of a function to remove the loading screen
     * after a specified time interval (3 seconds in this case).
     */
    setTimeout(async () => {
      document.querySelector(".loading").remove();
    }, 3000);

    /**
     * Fetches photo data from the Unsplash API for two specific photos using their IDs.
     */
    let res = await fetch(
      `${BASE_URL}photos/6-Y_Hxoh7VU?client_id=${photoKey}`
    );
    let json = await res.json();
    middlePhoto = json.urls.regular;

    res = await fetch(`${BASE_URL}photos/rdmJc2Os4EM?client_id=${photoKey}`);
    json = await res.json();
    bg = json.urls.full;
  });
</script>

<!-- Store the value of the scrollbar's Y position and the inner height of the window -->
<svelte:window bind:scrollY={y} bind:innerHeight />
<svelte:head>
  <link rel="stylesheet" href="css/main.css" />
</svelte:head>

<!-- Loading screen -->
<div class="loading">
  <!-- Renders each letter in the loading array inside a span element.
  The '--i' custom CSS property is used to stagger the animation delay of each span. -->
  {#each loadingArr as letter, i}
    <span style="--i:{i + 1}">{letter}</span>
  {/each}
</div>

<!-- Dashboard div used for footer button to bring scroll back to top -->
<div id="dashboard" />

<!-- Container for page content -->
<div class="home-container">
  <!-- First section content and container -->
  <div class="top-section">
    <div class="header-section">
      <!-- Top section content and container -->
      <div class="header-top container">
        <!-- Logo -->
        <div class="brand">
          <h1 class="brand-name">
            <span class="reveal-delay"> Sonus </span>
          </h1>
          <img
            src="./img/just-icon.png"
            class="brand-logo"
            alt="sona small"
            height="90%"
          />
        </div>
      </div>
      <!-- Slogan container -->
      <div class="header-lower container">
        <span class="reveal-delay">
          <div class="slogan">
            <h1>A million songs - One Sona</h1>
          </div>
        </span>
      </div>
      <!-- Scroll and arrow container -->
      <div class="header-arrow container">
        <div class="scroll reveal-delay">
          <span class="scroll-title reveal-delay"> Scroll down </span>
          <div class="arrow reveal-delay">
            <span class="scroll-down reveal-delay">
              <span class="arrow-down reveal-delay" />
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
  <!-- Reveal content when scroll reaches 100px -->
  {#if y > 100}
    <div class="second-section reveal">
      <div class="middle-container">
        <div class="words">
          {#each textArr as word, x}
            <h2 style="--x:{x + 1}">• {word} •</h2>
          {/each}
        </div>
        <!-- About card and description -->
        <div class="about-section">
          <!-- Reveal content when scrollbar reaches 400px OR if the screen height is smaller than usual -->
          {#if y > 400 || innerHeight <= 800}
            <div class="card-container reveal">
              <div class="about-card">
                <div class="about-inner">
                  <div class="about-front">
                    <img class="about-image" src={middlePhoto} alt="tapes" />
                  </div>
                  <div class="about-back">
                    <h3>Sed ultricies</h3>
                    <p>
                      Est risus sollicitudin tortor. In semper ipsum ligula at
                      nunc. Ut vitae tristique ligula.
                    </p>
                  </div>
                </div>
              </div>
            </div>
            <div class="about-title">
              <h1>
                <span class="reveal"> What is a Sona? </span>
              </h1>
            </div>
            <div class="desc-container">
              <div class="about-description">
                <p class="reveal">
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras
                  vestibulum, neque at scelerisque pharetra, libero nisi
                  condimentum massa, nec aliquet leo tellus at orci. Vestibulum
                  varius sapien id ipsum scelerisque, eget efficitur lacus
                  auctor.
                </p>
              </div>
            </div>
          {/if}
        </div>
      </div>
    </div>
  {/if}
  <!-- Reveal last section when scrollbar reaches 800px -->
  {#if y > 800}
    <div class="fixed-bg reveal" style="background-image:url({bg})">
      <div class="last-section">
        <div class="last-container">
          <!-- title container -->
          <div class="top-grid">
            <h1>
              <span class="reveal"> Discover Your Sona! </span>
            </h1>
          </div>
          <!-- Description container -->
          <div class="middle-grid">
            <p>
              <span class="reveal">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras
                vestibulum, neque at scelerisque pharetra, libero nisi
                condimentum massa, nec aliquet leo tellus at orci.
              </span>
            </p>
          </div>
          <!-- Button container -->
          <div class="button-grid reveal">
            <a href="/profile" class="button-link">
              <JoinButton>
                <p id="button-text">Join Sonus</p>
              </JoinButton>
            </a>
          </div>
        </div>
      </div>
    </div>
  {/if}
</div>

<style>
  .home-container {
    width: 100%;
    height: 100%;
    display: block;
  }

  .top-section {
    position: relative;
    display: block;
    height: 100vh;
    padding: 0 40px;
  }

  .header-section {
    z-index: 2;
    align-items: center;
    width: 100%;
    height: 90%;
    display: grid;
    grid-template-columns: 60%;
    grid-template-areas:
      "main"
      "lower"
      "button";
    grid-template-rows: 50% 10% 25%;
    row-gap: 30px;
    padding-top: 100px;
    flex-wrap: wrap;
    justify-content: center;
  }

  .container {
    justify-content: center;
    position: relative;
    display: flex;
    width: 100%;
    height: 100%;
    background-color: transparent;
  }

  .header-lower {
    display: flex;
    justify-content: center;
  }

  .header-top {
    grid-area: main;
    font-size: 200px;
  }

  .brand {
    width: 100%;
    height: 100%;
    justify-content: center;
    text-align: center;
    animation: pulse 2s infinite linear;
    position: relative;
    grid-area: main;
    font-size: 100%;
  }

  .brand-name {
    position: absolute;
    z-index: 1;
    font-size: inherit;
    height: 100%;
    width: 100%;
    color: #f0a6ca;
    overflow: hidden;
    text-shadow: 1px 1px 1px #efc3e6, 1px 2px 1px #efc3e6, 1px 3px 1px #efc3e6,
      1px 4px 1px #efc3e6, 1px 5px 1px #efc3e6, 1px 6px 1px #efc3e6,
      1px 7px 1px #efc3e6, 1px 8px 1px #efc3e6, 1px 9px 1px #efc3e6,
      1px 10px 1px #efc3e6, 1px 18px 6px rgba(16, 16, 16, 0.4),
      1px 22px 10px rgba(16, 16, 16, 0.2), 1px 25px 35px rgba(16, 16, 16, 0.2),
      1px 30px 40px rgba(16, 16, 16, 0.4);
  }

  .brand-name > .reveal-delay {
    height: 100%;
  }

  .brand-logo {
    animation: fadeIn 3.5s ease-in 3s;
  }

  .slogan h1 {
    color: #efc3e6;
    text-shadow: -4px 3px 1px rgba(16, 16, 16, 0.6);
    font-size: 40px;
  }

  .slogan {
    width: 100%;
    text-align: center;
  }

  .header-lower > .reveal-delay {
    width: 100%;
  }

  .header-arrow {
    align-items: center;
    justify-content: center;
    grid-area: button;
    flex-wrap: wrap;
  }
  .scroll-down {
    display: block;
    position: relative;
    padding: 79px 10px 0;
    margin-top: 15px;
    text-align: center;
    animation: mover 0.5s infinite alternate;
  }

  .arrow-down {
    display: block;
    margin: 0 auto;
    width: 10px;
    height: 20px;
  }
  .arrow-down:after {
    content: "";
    display: block;
    margin: 0;
    padding: 0;
    width: 8px;
    height: 8px;
    border-top: 2px solid #f0a6ca;
    border-right: 2px solid #f0a6ca;
    transform: rotate(135deg);
    box-shadow: 4px -3px 6px rgba(16, 16, 16, 0.425);
  }

  .scroll-title {
    display: block;
    text-transform: uppercase;
    color: #f0a6ca;
    letter-spacing: 0.1em;
    font-size: 20px;
    text-shadow: -2px 3px 1px rgba(16, 16, 16, 0.6);
    margin: 0 10px;
  }

  .scroll-down::before {
    position: absolute;
    top: 0px;
    left: 50%;
    margin-left: -1px;
    width: 2px;
    height: 90px;
    background: #f0a6ca;
    content: " ";
    box-shadow: -1px -3px 6px #efc3e68a, 1px -3px 4px #efc3e68a;
  }

  .second-section {
    background-color: #edede9;
    width: 100%;
    text-align: center;
    font-size: 40px;
    height: fit-content;
    transition: all 1s ease;
    box-shadow: 10px 0px 20px 5px rgba(0, 0, 0, 0.76);
    z-index: 2;
    padding-bottom: 40px;
  }

  .second-section.reveal {
    animation-duration: 0.8s;
  }

  .middle-container {
    width: 100%;
    margin-top: 50px;
    height: fit-content;
    align-items: center;
    justify-content: center;
  }

  .words {
    justify-content: center;
    display: flex;
    margin-bottom: 20px;
    width: 100%;
    transition: all 1s ease;
  }

  .words h2 {
    animation: 3s infinite step-end textAnim;
    animation-delay: calc(0.75s * var(--x));
    transition: all 1s ease;
    color: #efc3e6;
    display: block;
    margin: 20px;
    padding: 10px;
    max-width: 50%;
  }

  .about-section {
    height: 70%;
    display: grid;
    grid-template-columns: 30% 70%;
    grid-template-rows: 20% 80%;
    grid-template-areas:
      "none title"
      "card description";
    margin: 0 40px 0;
    align-items: center;
  }

  .about-title {
    position: relative;
    text-align: bottom;
    color: #9c89b8;
    animation: mover 1s infinite alternate;
    grid-area: title;
    display: flex;
    justify-content: center;
    height: 100%;
    margin-top: 20px;
  }

  .about-title h1 {
    height: 100%;
  }

  .desc-container {
    display: flex;
    grid-area: description;
    justify-content: center;
    height: 100%;
    align-items: center;
  }

  .about-description {
    grid-area: description;
    font-size: 40px;
    line-height: 2em;
    width: 90%;
    color: #1f1f1f;
    height: fit-content;
    justify-content: center;
    display: flex;
  }

  .card-container {
    width: 100%;
    display: flex;
    position: relative;
    grid-area: card;
  }

  .about-card {
    background-color: transparent;
    width: 100%;
    height: 520px;
    border-radius: 30px;
    transition: transform 0.8s;
    grid-area: card;
    margin: 20px;
  }

  .about-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
  }

  .about-image {
    transition: transform 0.8s;
  }

  .about-card:hover .about-back {
    z-index: 1;
  }

  .about-front,
  .about-back {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    justify-content: center;
    color: #1f1f1f;
    background-color: #9c89b8;
    transition: all 0.5s ease;
  }

  .about-image {
    width: 200%;
    height: 100%;
    transition: all 1s ease;
  }

  .about-card:hover .about-front {
    transform: rotateX(90deg);
    transform: scaleX(0);
  }

  .about-card:hover .about-back {
    transform: rotateX(0deg);
  }

  .about-front {
    border-radius: 30px;
  }

  .about-back {
    transform: rotateY(180deg);
    flex-direction: column;
    z-index: -1;
    display: flex;
    border-radius: 30px;
    color: #1f1f1f;
    background-color: #9c89b8;
  }

  .about-back p {
    font-size: 25px;
    margin-top: 20px;
    padding: 20px;
    line-height: 2em;
  }

  .about-back h3 {
    margin-bottom: 40px;
  }

  .fixed-bg {
    height: 150vh;
    position: relative;
    background-size: cover;
    background-position: right;
    background-repeat: no-repeat;
    justify-content: center;
    text-align: center;
  }

  .last-section {
    height: 100%;
    padding: 100px;
    position: relative;
    display: block;
  }

  .last-container {
    width: 100%;
    height: 60%;
    display: grid;
    grid-template-columns: auto;
    grid-template-rows: 30% 40% 30%;
    grid-template-areas:
      "top"
      "middle"
      "button";
    font-size: 100px;
    flex-direction: column;
  }

  .top-grid h1 {
    font-size: 85%;
    text-shadow: -4px 3px 1px #e688d3;
    color: #edede9;
  }

  .top-grid {
    align-items: center;
    justify-content: center;
    display: flex;
    grid-area: top;
  }

  .middle-grid {
    font-size: 35%;
    line-height: 2.4em;
    color: #efc3e6;
    text-shadow: -4px 3px 4px #1f1f1f;
    grid-area: middle;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .middle-grid p {
    width: 80%;
  }

  .button-grid {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
  }

  .button-link {
    height: 77px;
    width: 263px;
    align-items: center;
  }

  #button-text:hover {
    animation: mover 0.5s infinite alternate;
  }

  #button-text {
    padding: 10px;
    font-size: 40px;
  }

  @media (max-width: 1400px) {
    .words h2 {
      font-size: 50px;
    }

    .about-description p {
      font-size: 35px;
    }

    .about-image {
      width: 300%;
      height: 150%;
    }
  }

  @media (max-width: 1200px) {
    .middle-container {
      height: fit-content;
    }

    .about-section {
      height: 80%;
      grid-template-columns: auto;
      grid-template-rows: 20% 40% 40%;
      grid-template-areas:
        "title"
        "description"
        "card";
      margin-top: 100px;
    }

    .about-title {
      padding-bottom: 40px;
    }

    .desc-container {
      height: 100%;
    }

    .words {
      display: block;
      margin: 0;
      height: 60%;
    }

    .words h2 {
      font-size: 100px;
      max-width: 100%;
    }

    .about-description p {
      font-size: 30px;
    }

    .about-title {
      padding: 0;
    }

    .card-container {
      justify-content: center;
    }

    .about-card {
      height: 300px;
      width: 50%;
      margin-top: 40px;
    }

    .about-image {
      width: 200%;
      height: 200%;
    }

    .about-back h3 {
      margin: 0;
    }

    .about-back p {
      margin: 0;
    }
  }

  @media (max-width: 1120px) {
    .header-section {
      grid-template-columns: 100%;
    }

    .brand-name {
      font-size: 80%;
    }

    .middle-grid {
      line-height: 1.8em;
    }

    .middle-grid p {
      font-size: 85%;
    }
  }

  @media (max-width: 870px) {
    .about-section {
      grid-template-rows: 15% 35% 45%;
      justify-content: center;
    }
    .about-description p {
      font-size: 22px;
      line-height: 2em;
    }

    .about-description {
      display: flex;
    }

    .about-card {
      width: 100%;
    }

    .brand-logo {
      width: 50%;
      height: 70%;
    }

    .brand-name {
      font-size: 70%;
    }

    .middle-grid {
      line-height: 1.4em;
    }

    .middle-grid p {
      font-size: 80%;
    }
  }

  @media (max-width: 660px) {
    .about-description p {
      line-height: 1.8em;
    }

    .about-description {
      height: 100%;
    }

    .desc-container {
      height: 100%;
      padding: 40px 0;
    }

    .words h2 {
      font-size: 80px;
    }

    .about-title {
      font-size: 30px;
    }

    .header-top {
      width: 100%;
    }

    .header-section {
      height: 80%;
      grid-template-rows: 40%;
    }

    .slogan h1 {
      font-size: 30px;
      text-shadow: -3px 3px 1px rgba(16, 16, 16, 0.6);
      margin-top: 40px;
    }

    .brand {
      width: 80%;
      display: flex;
    }

    .brand-name {
      font-size: 60%;
    }

    .brand-logo {
      height: 100%;
      width: 70%;
    }

    .scroll-title {
      text-shadow: -2px 3px 1px rgba(16, 16, 16, 0.6);
    }

    .scroll {
      height: 100%;
    }

    .top-section {
      padding: 10px;
    }

    .middle-grid {
      line-height: 1em;
    }

    .middle-grid p {
      font-size: 85%;
    }

    .last-container {
      height: 60%;
    }

    .middle-grid p {
      width: 100%;
    }

    .top-grid h1 {
      font-size: 70%;
    }
  }

  @media (max-width: 570px) {
    .words h2 {
      font-size: 50px;
    }

    .about-title {
      font-size: 25px;
    }

    .about-image {
      width: 250%;
      height: 150%;
    }

    .about-back p,
    h3 {
      font-size: 50%;
    }

    .brand-name {
      width: 100%;
      font-size: 50%;
    }

    .brand-logo {
      height: 80%;
      width: 70%;
    }

    .top-grid h1 {
      font-size: 45%;
      padding: 10px;
    }

    .middle-grid p {
      font-size: 70%;
    }

    #button-text {
      font-size: 30px;
      padding: 0;
    }

    .button-link {
      width: 55%;
    }

    .loading span {
      font-size: 50px;
    }
  }

  @media (max-width: 420px) {
    .brand-name {
      font-size: 45%;
    }

    .brand-logo {
      height: 70%;
      width: 80%;
    }

    .header-section {
      row-gap: 0px;
    }

    .last-section {
      padding: 0 30px;
      align-items: center;
      display: flex;
    }

    .fixed-bg {
      height: 100vh;
    }

    .last-container {
      height: 50%;
      grid-template-rows: 20% 40% 40%;
    }

    .top-grid h1 {
      font-size: 35%;
    }

    .middle-grid p {
      font-size: 50%;
    }

    .button-link {
      width: 50%;
      height: 35%;
    }

    #button-text {
      font-size: 90%;
      padding: 0;
    }
  }

  @media (max-height: 910px) {
    .second-section {
      height: 100%;
    }
  }

  @media (max-height: 600px) {
    .scroll-down {
      display: none;
    }

    .brand-name {
      font-size: 60%;
    }

    .slogan h1 {
      font-size: 30px;
    }
  }
</style>

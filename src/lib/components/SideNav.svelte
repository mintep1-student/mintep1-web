<!-- Side navigation bar -->
<div class="sidenav">
  <nav class="nav-container">
    <!-- Logo section -->
    <a href="/" class="branding">
      <img
        src="./img/Sonus-logos_transparent.png"
        alt="logo"
        height="100px"
        class="logo"
      />
      <img
        src="./img/just-icon.png"
        alt="logo icon"
        height="50px"
        class="icon"
      />
    </a>
    <!-- Pages section -->
    <div class="top-side-nav">
      <a href="/profile" class="nav-link">
        <i class="fa-solid fa-user" style="color: rgb(18, 10, 19)" />
        <svg
          xmlns="http://www.w3.org/2000/svg"
          height="1.5em"
          viewBox="0 0 512 512"
        >
          <path
            d="M224 256A128 128 0 1 0 224 0a128 128 0 1 0 0 256zm-45.7 
          48C79.8 304 0 383.8 0 482.3C0 498.7 13.3 512 29.7 
          512H418.3c16.4 0 29.7-13.3 29.7-29.7C448 383.8 368.2 304 269.7 304H178.3z"
          />
        </svg>
        <p class="nav-text">Profile</p>
      </a>
      <div class="nav-link">
        <i class="fa-brands fa-hive" />
        <svg
          xmlns="http://www.w3.org/2000/svg"
          height="1.5em"
          viewBox="0 0 512 512"
        >
          <path
            d="M260.353,254.878,131.538,33.1a2.208,2.208,0,0,0-3.829.009L.3,
              254.887A2.234,2.234,0,0,0,.3,257.122L129.116,478.9a2.208,
              2.208,0,0,0,3.83-.009L260.358,257.113A2.239,2.239,0,0,0,
              260.353,254.878Zm39.078-25.713a2.19,2.19,0,0,0,1.9,1.111h66.509a2.226,2.226,
              0,0,0,1.9-3.341L259.115,33.111a2.187,
              2.187,0,0,0-1.9-1.111H190.707a2.226,2.226,0,0,0-1.9,3.341ZM511.7,
              254.886,384.9,33.112A2.2,2.2,0,0,0,382.99,32h-66.6a2.226,
              2.226,0,0,0-1.906,3.34L440.652,256,314.481,476.66a2.226,
              2.226,0,0,0,1.906,3.34h66.6a2.2,2.2,0,0,0,1.906-1.112L511.7,
              257.114A2.243,2.243,0,0,0,511.7,254.886ZM366.016,284.917H299.508a2.187,
              2.187,0,0,0-1.9,1.111l-108.8,190.631a2.226,2.226,0,0,0,1.9,3.341h66.509a2.187,
              2.187,0,0,0,1.9-1.111l108.8-190.631A2.226,2.226,0,0,0,366.016,284.917Z"
          />
        </svg>
        <p class="nav-text">Library</p>
      </div>
      <div class="nav-link">
        <i class="fa-solid fa-compact-disc" />
        <svg
          xmlns="http://www.w3.org/2000/svg"
          height="1.5em"
          viewBox="0 0 512 512"
        >
          <path
            d="M0 256a256 256 0 1 1 512 0A256 256 
              0 1 1 0 256zm256 32a32 32 0 1 1 0-64 32 32 0 1 1 0 
              64zm-96-32a96 96 0 1 0 192 0 96 96 0 1 0 -192 0zM96 
                240c0-35 17.5-71.1 45.2-98.8S205 96 240 96c8.8 0 16-7.2 
                16-16s-7.2-16-16-16c-45.4 0-89.2 22.3-121.5 54.5S64 194.6 
                64 240c0 8.8 7.2 16 16 16s16-7.2 16-16z"
          />
        </svg>
        <p class="nav-text">Discover</p>
      </div>
    </div>
  </nav>
  <!-- Exit section -->
  <div class="bottom-side-nav">
    <a href="/goodbye" class="nav-link">
      <i class="fa-solid-icons" style="color: #ffffff;" />
      <svg
        xmlns="http://www.w3.org/2000/svg"
        height="1.5em"
        viewBox="0 0 512 512"
      >
        <path
          d="M502.6 278.6c12.5-12.5 12.5-32.8 0-45.3l-128-128c-12.5-12.5
            -32.8-12.5-45.3 0s-12.5 32.8 0 45.3L402.7 224 192 224c-17.7 0-32 14.3-32 32s14.3 32 32 32l210.7 0-73.4 
            73.4c-12.5 12.5-12.5 32.8 0 45.3s32.8 12.5 45.3 0l128-128zM160 96c17.7 0 32-14.3 32-32s-14.3-32-32-32L96 
            32C43 32 0 75 0 128L0 384c0 53 43 96 96 96l64 0c17.7 0 32-14.3 32-32s-14.3-32-32-32l-64 0c-17.7 0-32-14.3
            -32-32l0-256c0-17.7 14.3-32 32-32l64 0z"
        />
      </svg>
      <p class="nav-text">Exit</p>
    </a>
  </div>
</div>

<style>
  .nav-container {
    display: flex;
    flex-wrap: wrap;
  }

  .sidenav {
    height: 100%;
    width: 250px;
    position: fixed;
    z-index: 2;
    top: 0;
    left: 0;
    background-color: #9c89b8;
    padding: 10px;
    box-shadow: 2px 0px 11px 3px rgba(153, 151, 151, 0.75);
    transition: all 0.5s ease;
  }

  .sidenav .nav-link {
    padding: 15px 25px;
    text-decoration: none;
    font-size: 18px;
    color: rgb(18, 10, 19);
    display: block;
    height: 45px;
    border-radius: 50px;
  }

  .sidenav .nav-link:hover {
    background-color: #efc3e6;
  }

  .sidenav svg {
    fill: rgb(18, 10, 19);
  }

  .sidenav svg,
  .nav-text {
    display: inline-flex;
    animation: grow 1s;
  }

  @keyframes grow {
    0% {
      font-size: 1px;
      opacity: 0;
    }
    80% {
      font-size: 100%;
      opacity: 1;
    }
  }

  .branding {
    height: fit-content;
    position: relative;
    top: 20px;
    left: 26%;
    width: fit-content;
  }

  .branding img {
    margin: 0 0 20px;
    animation: 1.5s fadeIn;
  }

  .branding .icon {
    display: none;
    transition: all 0.8s ease;
  }
  
  .top-side-nav {
    border-top: solid 1px rgb(18, 10, 19);
    margin: 40px 0 0 0;
    padding: 10px;
    height: fit-content;
    flex-wrap: wrap;
    position: relative;
    width: 100%;
    animation: fadeIn 2s;
  }

  .nav-text {
    position: relative;
    padding: 15px 0 0 15px;
    top: -4px;
  }

  .bottom-side-nav {
    position: absolute;
    border-top: solid 1px rgb(18, 10, 19);
    bottom: 32px;
    width: 85%;
    padding: 10px;
    height: fit-content;
    animation: fadeIn 2s;
  }

  @media (max-width: 980px) {
    .sidenav {
      width: 70px;
      justify-content: center;
    }

    .sidenav svg {
      animation: fadeIn 1s;
    }

    .sidenav .nav-link {
      padding: 12px;
      height: fit-content;
    }

    .branding .logo {
      display: none;
    }

    .branding {
      left: 1px;
    }

    .branding .icon {
      display: block;
    }

    .bottom-side-nav {
      top: 80%;
      width: 55%;
    }

    .nav-text {
      display: none;
    }
  }

  @media (max-width: 840px) {
    .sidenav {
      display: none;
    }
  }
</style>

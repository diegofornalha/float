<script>
  export let ipfsHash;
</script>

<img
  class="lantern"
  style="left: {Math.floor(Math.random() * (90 - 10 + 1)) + 10}vw;"
  src="https://ipfs.infura.io/ipfs/{ipfsHash}"
  alt="lantern" />

<style>
  .lantern {
    position: absolute;
    color: lightblue;
    top: 100vh;
    opacity: 1;
    display: block;
    animation-name: slide;
    animation-fill-mode: forwards;
    animation-duration: 5s;
    animation-iteration-count: 1;
    animation-timing-function: ease-in;
    z-index: 10;
  }

  img.lantern {
    width: 60px;
    height: 60px;
    object-fit: cover;
    border-radius: 100%;
    box-shadow: 0px 0px 5px 5px #38e8c6;
  }

  @keyframes slide {
    0% {
      top: 100vh;
      opacity: 1;
    }
    85% {
      opacity: 1;
    }
    99% {
      transform: translateY(-109vh);
      opacity: 0.1;
    }
    100% {
      transform: translateY(-110vh);
      opacity: 0;
    }
  }

  @-webkit-keyframes slide {
    0% {
      top: 100vh;
      opacity: 1;
    }
    85% {
      opacity: 1;
    }
    99% {
      transform: translateY(-109vh);
      opacity: 0.1;
    }
    100% {
      transform: translateY(-110vh);
      opacity: 0;
    }
  }
</style>

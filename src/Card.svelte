<script>
  export let src = ''
  export let excerpt = ''
  export let index = 0

  let isBig = false
  let innerWidthValue = 0

  const handlClick = e => {
    !isBig &&
      index % 2 !== 0 &&
      window.scrollBy({
        top: 600,
        left: 0,
        behavior: 'smooth',
      })

    isBig &&
      index % 2 !== 0 &&
      window.scrollBy({
        top: -600,
        left: 0,
        behavior: 'smooth',
      })

    isBig = !isBig
  }
</script>

<svelte:window bind:innerWidth={innerWidthValue} />

<article class:big={isBig} on:click={innerWidthValue > 500 && handlClick}>
  <img {src} alt="Card" />
  <p>{@html excerpt}</p>
</article>

<style>
  article {
    flex: 1;
    min-width: 350px;
    background: #f0f2f5;
    border-radius: 1em;
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.24);
    overflow: hidden;
    transition: all 500ms ease-in-out;
  }
  img {
    display: block;
    width: 100%;
    height: 350px;
    object-fit: cover;
  }
  p {
    padding: 2rem;
    line-height: 1.5rem;
  }
  .big {
    flex-basis: 100%;
  }
  .big img {
    width: auto;
    height: 100vh;
    margin: auto;
  }
</style>

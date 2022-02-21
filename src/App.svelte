<script>
  import Card from './Card.svelte'

  const endpoint =
    'https://public-api.wordpress.com/rest/v1.1/sites/repo995752852.wordpress.com/posts/?category=graphic-design'

  let posts = []

  const getPosts = async node => {
    const res = await fetch(endpoint)
    const data = await res.json()

    posts = data.posts
  }
</script>

<aside use:getPosts>
  {#each posts as { featured_image, excerpt }, index}
    <Card src={featured_image} {excerpt} {index} />
  {/each}
</aside>

<style>
  aside {
    display: flex;
    justify-content: space-evenly;
    flex-wrap: wrap;
    gap: 4rem;
  }
</style>

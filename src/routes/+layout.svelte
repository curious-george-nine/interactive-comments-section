<script>
  import "../app.css";
  import "../../node_modules/animate.css/animate.min.css";
  import favicon from "$lib/images/favicon-32x32.png";
</script>

<svelte:head>
  <link rel="icon" href={favicon} />
</svelte:head>

<slot />

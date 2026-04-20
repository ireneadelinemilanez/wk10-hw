<!--
@component
TextSlide.svelte — A centered text slide for narrative context between photos.

Displays a headline and body paragraph on a full-screen black background,
providing editorial context within a multimedia gallery sequence.
Optionally displays a background photo.

USAGE EXAMPLE:
<TextSlide slide={{
  headline: 'The Commute',
  body: 'Every day, thousands of riders depend on the L train to cross between Brooklyn and Manhattan.'
}} photo={{
  filename: 'subway-platform.jpg',
  title: 'Subway Platform'
}} />
-->
<script>
  import { base } from '$app/paths';

  let {
    slide, // Object with headline and body text
    photo, // Optional: Object with filename and title
  } = $props();
</script>

<div class="slide" data-slide>
  {#if photo}
    <img src="{base}/photos/{photo.filename}" alt={photo.title} class="bg-image" />
  {/if}
  <div class="content">
    <h2>{slide.headline}</h2>
    <p>{slide.body}</p>
  </div>
</div>

<style>
  .slide {
    height: 100%;
    flex: 0 0 100%;
    background: black;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }

  .bg-image {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: 0;
  }

  .content {
    max-width: 560px;
    padding: 2rem;
    color: white;
    text-align: left;
    position: relative;
    z-index: 1;
  }

  h2 {
    font-family: var(--font-sans);
    font-size: 1.75rem;
    line-height: 1.2;
    margin: 0 0 1rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    color: #eaa928;
  }

  p {
    font-family: var(--font-serif);
    font-size: 1.0625rem;
    line-height: 1.7;
    opacity: 0.8;
    margin: 0;
  }
</style>

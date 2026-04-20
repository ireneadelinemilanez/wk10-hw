<script>
  import SlideGallery from '$lib/components/MultimediaGallery/SlideGallery.svelte';
  import TitleSlide from '$lib/components/MultimediaGallery/TitleSlide.svelte';
  import PhotoSlide from '$lib/components/MultimediaGallery/PhotoSlide.svelte';
  import TextSlide from '$lib/components/MultimediaGallery/TextSlide.svelte';
  import CreditsSlide from '$lib/components/MultimediaGallery/CreditsSlide.svelte';

  let { data } = $props();
</script>

<SlideGallery>
  <TitleSlide
    headline="MAMDANI CELEBRATES FIRST 100 DAYS"
    intro="On Sunday, April 12, Zohran Mamdani held a speech at the Knockdown Center in Maspeth, Queens to share his administrations progress on campaign promises, as well as the work needed to continue."
  />

  {#each data.story as slide (slide.id)}
    {#if slide.type === 'photo'}
      <PhotoSlide photo={slide} />
    {:else if slide.type === 'text'}
      <TextSlide {slide} />
    {/if}
  {/each}

  <CreditsSlide>
    <h2>About These Photographs</h2>
    <p>
      Irene Adeline Milanez is an award winning, visual journalist who shares the stories of underrepresented communities through writing, photography and video. Milanez is pursuing a multimedia journalism career in business reporting at the Craig Newmark Graduate School of Journalism in New York.
    </p>
  </CreditsSlide>
</SlideGallery>
<script>
  import { globalState } from './state.svelte.js';

  import Grid from './components/Grid/Grid.svelte';
  import GridRow from './components/Grid/_GridRow.svelte';
  import SectionLabel from './components/Hero/_SectionLabel.svelte';
  import Headline from './components/Hero/_Headline.svelte';
  import Timestamp from './components/Hero/_Timestamp.svelte';
  import Image from './components/Image/Image.svelte';
  import Dek from './components/Hero/_Dek.svelte';
  import Byline from './components/Hero/_Byline.svelte';
  import Counter from './components/Counter/Counter.svelte';
  import MuteIcon from './components/Video/_MuteIcon.svelte';
  import VolumeIcon from './components/Video/_VolumeIcon.svelte';

  /** @type {{sectionLabel?: string; headline?: string; timestamp?: string; heroImageUrl?: string; heroImageCaption?: string; heroImageAltText?: string; dek?: string; authorName?: string; authorBioUrl?: string;}} */
  let {
    sectionLabel = 'Section label',
    headline = 'Lorem ipsum dolor sit amet consectetur adipiscing elit',
    timestamp = 'December 1, 1977',
    heroImageUrl = 'https://arc.stimg.co/startribunemedia/4SPNT7DI36ANT2SOB5N5EJAIJU.jpg',
    heroImageCaption = 'Lorem ipsum dolor',
    heroImageAltText = '',
    dek = 'Lorem ipsum dolor sit amet consectetur adipiscing elit, fusce sociis at montes vitae tempor enim, venenatis tristique feugiat arcu dis ridiculus.',
    authorName = 'Bryan Brussee',
    authorBioUrl = '',
  } = $props();

  /** @type {HTMLVideoElement | null} */
  let heroVideo = $state(null);
  let isMuted = $state(true);

  function toggleVideoMute() {
    if (!heroVideo) return;
    heroVideo.muted = !heroVideo.muted;
    isMuted = heroVideo.muted;
  }
</script>

<Grid additionalClasses="gap-y-0 md:gap-y-0">
  <GridRow variant={'fullBleed'} additionalClasses="xs:bg-[#00316d] md:bg-none">
    <div
      class="relative flex items-center justify-center h-screen mb-4 overflow-hidden bg-[white] xl:max-h-[1000px] lg:max-h-[900px] md:max-h-[800px] xs:max-h-[650px]"
    >
      <!-- DESKTOP DISP TYPE -->

      <div
        class="md:block xs:hidden absolute left-2 bottom-0 w-full xs:top-2 z-30 text-white"
      >
        <div class="flex mb-4 absolute left-4 bottom-2 w-full">
          <div class="w-full pr-2">
            <h1
              class="ml-0 mr-auto text-shadow-lg text-left font-[publico-headline-banner] xl:text-[3.5rem] lg:text-[3.5rem] md:text-[2.85rem] xs:text-[1.75rem] p-4 !leading-[1.2]"
            >
              How Stillwater synchronized swimming<br />
              dominates Minnesota year after year
            </h1>
          </div>
        </div>
      </div>

      <!-- autoplay="" loop="" muted="true" -->
      <video
        bind:this={heroVideo}
        autoplay
        muted={isMuted}
        playsinline
        loop
        class="object-cover object-center absolute h-full w-full"
      >
        <source
          src="https://d2rhwptr68oefh.cloudfront.net/wp-startribunemedia/20260806/6a74ae4aa9371f6ec4a66182/t_ecfc70d28bc14ca18b930cc36f3a890f_name_SYNCHRO_muted/file_1920x1080-5400-v4.mp4"
          type="video/mp4"
        />Your browser does not support the video tag.
      </video>

      <button
        class="absolute right-4 bottom-4 z-40 bg-black/45 hover:bg-black/60 text-white rounded-full w-10 h-10 flex items-center justify-center transition-colors"
        aria-label={isMuted ? 'Unmute video' : 'Mute video'}
        onclick={toggleVideoMute}
      >
        {#if isMuted}
          <MuteIcon size={18} />
        {:else}
          <VolumeIcon size={18} />
        {/if}
      </button>
    </div>
  </GridRow>
  <GridRow>
    <!-- MOBILE DISP TYPE -->
    <div
      class="md:hidden xs:block !text-[black] text-left bg-[#00316d] !text-white pt-4 pb-4 mt-[-5px]"
    >
      <h1
        class="max-w-[450px] mx-auto text-center font-[publico-headline-banner] xl:text-[3.25rem] lg:text-[2.75rem] md:text-[2.5rem] xs:text-[2rem] pb-10 px-4 !leading-[1.05]"
      >
        How Stillwater synchronized swimming
        dominates Minnesota year after year
      </h1>
      <h2
        class="max-w-[350px] mx-auto text-center font-[publico-headline-light] xl:text-[1.75rem] lg:text-[1.5rem] md:text-[1.25rem] xs:text-[1.35rem] pb-6 px-4 !leading-[1.2]"
      >
        One of Minnesota’s most dominant athletic programs can be found in the
        deep end of the pool.
      </h2>

      <!-- <div class="font-[graphik] text-[14px] mx-auto text-center pl-4 h-[20px]">
By <b>Jana Hollingsworth</b>
</div>
<div class="font-[graphik] text-[14px] mx-auto text-center pl-4 h-[20px]">
Photo and video by <b>Amanda Anderson</b>
</div>
<div class="font-[graphik] text-[14px] mx-auto text-center pl-4 h-[20px]">
The Minnesota Star Tribune
</div>
<div class="font-[graphik] text-[12px] mx-auto text-center pt-4 pl-4 tracking-[4px] uppercase">
May 22, 2026
</div> -->
    </div>
  </GridRow>

  <GridRow
    variant={'inline'}
    additionalClasses="justify-self-left md:max-w-[550px] mx-auto !lg:text-center lg:max-w-[712px] xs:hidden md:block"
  >
    <Dek>
      <h2
        class=" mr-auto ml-0 text-left font-[publico-headline-banner] xl:text-[1.95rem] lg:text-[1.95rem] md:text-[1.95rem] xs:text-[1.15rem] pt-12 pb-0 !leading-[1.2]"
      >
        One of Minnesota’s most dominant athletic programs can be found in the
        deep end of the pool.
      </h2></Dek
    >
  </GridRow>
</Grid>

<!--
@component
### Hero component 
Renders a visual replica of the Immersive Template hero. 

#### Optional properties
- sectionLabel: string;
- headline: string;
- timestamp: string;
- heroImageUrl: string;
- heroImageCaption: string;
- heroImageAltText: string;
- dek: string;
- authorName: string;
- authorBioUrl: string;

#### Example
```svelte
<Hero
  sectionLabel = "Section label",
  headline = "Lorem ipsum dolor sit amet consectetur adipiscing elit",
  timestamp = "Dec. 1, 1977",
  heroImageUrl = "https://arc.stimg.co/startribunemedia/4SPNT7DI36ANT2SOB5N5EJAIJU.jpg",
  heroImageCaption = "",
  heroImageAltText = "",
  dek = "Lorem ipsum dolor sit amet consectetur adipiscing elit, fusce sociis at montes vitae tempor enim, venenatis tristique feugiat arcu dis ridiculus.",
  authorName = "Bryan Brussee",
  authorBioUrl = "https://www.startribune.com/bryan-brussee/8455834",
>
```
-->
<style>
  @font-face {
    font-family: publico-headline-banner;
    src: url('https://static.startribune.com/fonts/PublicoBannerWebFonts/PublicoBanner-Roman-Web.woff2')
      format('woff2');
    font-style: normal;
    font-display: swap;
  }
  h1.font-editorial-news-heading-01,
  h1.font-editorial-enterprise-heading-01 {
    font-family: publico-headline-banner;
    font-weight: normal;
  }
</style>

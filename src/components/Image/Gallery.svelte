<!-- 
@component
### Gallery component
This component implements a swipable, mobile-friendly gallery via {@link https://swiperjs.com/element| Swiper}, the same JS library that the Immersive Template uses.
Its default design and behavior aims to mimic that of the Immersive Template, but designers are encouraged to modify as needed.

#### Properties
- imgs: An array of objects, each of which represents an image and contains the following properties: src, caption and alt. These properties expect strings and determine that image's source url, caption and alt text.

#### One Swiper quirk
Swiper galleries will not loop correctly across all viewports if they contain fewer than five images. To mitigate this behavior, this component will duplicate the passed-in image objects to pad out the gallery create the illusion of a looping gallery. 

#### Example
```svelte
  <GridRow variant="fullBleed">
      <Gallery imgs={[
        {src: "myUrl.jpg", caption="My caption.", alt="Don't forget the alt text!"},
        {src: "myUrl.jpg", caption="My caption.", alt="Don't forget the alt text!"},
        {src: "myUrl.jpg", caption="My caption.", alt="Don't forget the alt text!"},
        {src: "myUrl.jpg", caption="My caption.", alt="Don't forget the alt text!"},
        {src: "myUrl.jpg", caption="My caption.", alt="Don't forget the alt text!"},
      ]}/>
  </GridRow>
 ```  
-->

<script>
  import "swiper/css";
  import "swiper/css/grid";
  import "swiper/css/navigation";
  import "swiper/css/effect-coverflow";
  import {
    Navigation,
    A11y,
    Pagination,
    EffectCoverflow,
  } from "swiper/modules";

  import { register } from "swiper/element/bundle";

  import IconButton from "../Button/IconButton.svelte";
  let {
    imgs = [
      {
        src: "https://arc.stimg.co/startribunemedia/ROUBZPJJ7BFF5BEK7PUHUDLENA.jpg",
        caption: "Stillwater Area High School synchronized swimmers practice their extended group routine on the pool deck on April 14, at Stillwater Middle School.",
        alt: "Stillwater Area High School synchronized swimmers practice their extended group routine on the pool deck on April 14, at Stillwater Middle School.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/WZX7QIEOKVAFHMWCR2OWDD23PQ.jpg",
        caption: "Stillwater Area High School synchronized swimming coaches Kathy Henderson and Juliet Schmit leads their team through a workout on March 24, during practice at Stillwater Middle School.",
        alt: "Stillwater Area High School synchronized swimming coaches Kathy Henderson and Juliet Schmit leads their team through a workout on March 24, during practice at Stillwater Middle School.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/2KF4G2CLYBBUDCAYPPMZSGZNAA.jpg",
        caption: "Stillwater Area High School synchronized swimming assistant coach Juliet Schmit talks with swimmer Audrey Funk as she warms up ahead of their first home meet on March 31, at Stillwater Middle School.",
        alt: "Stillwater Area High School synchronized swimming assistant coach Juliet Schmit talks with swimmer Audrey Funk as she warms up ahead of their first home meet on March 31, at Stillwater Middle School.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/LJTLYNUOABBDLDNQMZBMZFSJI4.jpg",
        caption: "Stillwater Area High School synchronized swimmer Sienna Cruz is lifted out of the water by her teammates during practice.",
        alt: "Stillwater Area High School synchronized swimmer Sienna Cruz is lifted out of the water by her teammates during practice.",
      },
            {
        src: "https://arc.stimg.co/startribunemedia/RQUS5XAVGZCBDLW3XLSFFJUZAA.jpg",
        caption: "Captain Hailey Schmit warms up with the team ahead of practice.",
        alt: "Captain Hailey Schmit warms up with the team ahead of practice.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/V2LVEXOZ2ZCMPDO6XQ7GEIKCBI.jpg",
        caption: "Stillwater Area High School synchronized swimmers practice their extended group routine.",
        alt: "Stillwater Area High School synchronized swimmers practice their extended group routine.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/X3RCG7ZPU5E3NN7T7RJ4X7I4MU.jpg",
        caption: "Stillwater Area High School synchronized swimmers practice their lifts while they are prohibited from touching the bottom of the pool.",
        alt: "Stillwater Area High School synchronized swimmers practice their lifts while they are prohibited from touching the bottom of the pool.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/WKINUSPKGJHMDNOFHGXZMKVDIE.jpg",
        caption: "Stillwater Area High School synchronized swimmers go over video from their extended group routine with assistant coaches Juliet Schmit and Paige Schmit.",
        alt: "Stillwater Area High School synchronized swimmers go over video from their extended group routine with assistant coaches Juliet Schmit and Paige Schmit.",
      },
            {
        src: "https://arc.stimg.co/startribunemedia/YIUGYBO3LBCHJMHVSE4IAIEXQE.jpg",
        caption: "Stillwater Area High School synchronized swimmers compete in a home meet on April 23, at Stillwater Middle School.",
        alt: "Stillwater Area High School synchronized swimmers compete in a home meet on April 23, at Stillwater Middle School.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/UAJ2UHGNB5EKBL2INVB3HKVLRA.jpg",
        caption: "Stillwater Area High School synchronized swimmers compete in a home meet.",
        alt: "Stillwater Area High School synchronized swimmers compete in a home meet.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/LWD46STB45CANP2B2H4VDV45DY.jpg",
        caption: "Stillwater Area High School synchronized swimmers compete in a home meet.",
        alt: "Stillwater Area High School synchronized swimmers compete in a home meet.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/G7Y25RRGS5CZROO3YN5QFPHWWU.jpg",
        caption: "Stillwater Area High School synchronized swimmers compete in a home meet.",
        alt: "Stillwater Area High School synchronized swimmers compete in a home meet.",
      },
            {
        src: "https://arc.stimg.co/startribunemedia/2HL6UY6BF5BNJNAXR3I5YPZTSQ.jpg",
        caption: "Stillwater Area High School synchronized swimmers cheer on teammates at a home meet.",
        alt: "Stillwater Area High School synchronized swimmers cheer on teammates at a home meet.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/BRYYWR3PMRCKHDR76GASDNMPBQ.jpg",
        caption: "Stillwater Area High School synchronized swimming captain Hailey Schmit competes in a home meet.",
        alt: "Stillwater Area High School synchronized swimming captain Hailey Schmit competes in a home meet.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/CC6CI556UNFXPAHRQVRRNOSROU.jpg",
        caption: "Stillwater Area High School synchronized swimmers laugh together after competing in a home meet.",
        alt: "Stillwater Area High School synchronized swimmers laugh together after competing in a home meet.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/3R554EM3RBGI5JC4F2E2WRTNJY.jpg",
        caption: "Teammates help each other with their hair, preparing for the Synchronized Swimming State Invitational.",
        alt: "Teammates help each other with their hair, preparing for the Synchronized Swimming State Invitational.",
      },
            {
        src: "https://arc.stimg.co/startribunemedia/HEWGC4H4MJBBPBHHVPIXIB77F4.jpg",
        caption: "Stillwater Area High School synchronized swimmers compete in the Synchronized Swimming State Invitational.",
        alt: "Stillwater Area High School synchronized swimmers compete in the Synchronized Swimming State Invitational.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/E6Q7V4RMGNHPLFUXG4K4NMPBPU.jpg",
        caption: "Stillwater Area High School synchronized swimmers lift captain Hailey Schmit into the air as they compete in the Synchronized Swimming State Invitational.",
        alt: "Stillwater Area High School synchronized swimmers lift captain Hailey Schmit into the air as they compete in the Synchronized Swimming State Invitational.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/NPRDJTSSWBHG5GXUOFOBGOQJ6Y.jpg",
        caption: "Stillwater Area High School synchronized swimmers compete in the Synchronized Swimming State Invitational.",
        alt: "Stillwater Area High School synchronized swimmers compete in the Synchronized Swimming State Invitational.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/BVVDN25LKRHQ3MBPZH6TTLMIWU.jpg",
        caption: "Stillwater Area High School synchronized swimmers including captain Hailey Schmit, center, hoist their first place trophy into the air after winning the Synchronized Swimming State Invitational on May 22.",
        alt: "Stillwater Area High School synchronized swimmers including captain Hailey Schmit, center, hoist their first place trophy into the air after winning the Synchronized Swimming State Invitational on May 22.",
      },
    ],
  } = $props();

  let paddedImgs = $derived(imgs.length < 5 ? padImgs(imgs) : imgs);
  let activeIndex = $state(0);

  const id = $props.id();
  const nextClass = `swiper-button-next-${id}`;
  const prevClass = `swiper-button-prev-${id}`;

  const swiperParams = {
    effect: "coverflow",
    centeredSlides: true,
    slidesPerView: "auto",
    coverflowEffect: {
      rotate: 0,
      stretch: 0,
      depth: 0,
      modifier: 1,
      slideShadows: true,
    },
    loop: true,
    pagination: { dynamicBullets: true },
    modules: [Navigation, A11y, Pagination, EffectCoverflow],
    navigation: {
      nextEl: `.${nextClass}`,
      prevEl: `.${prevClass}`,
    },
    spaceBetween: 8,
    breakpoints: {
      768: {
        spaceBetween: 16,
      },
      1160: {
        spaceBetween: 24,
      },
    },
    on: {
      init() {},
    },
  };

  function setupSwiper(node) {
    $effect(() => {
      if (!customElements.get("swiper-container")) {
        register();
      }

      if (!node.swiper) {
        Object.assign(node, swiperParams);
        node.initialize();
      }

      return () => {
        node.swiper.destroy(true, true);
      };
    });
  }

  function padImgs(imgs) {
    let paddedImgs = [...imgs];

    while (paddedImgs.length < 5) {
      paddedImgs.push(...paddedImgs);
    }

    return paddedImgs;
  }
</script>

<div class="pt-5">
  <div class="mb-2">
    <swiper-container
      aria-live="polite"
      init="false"
      use:setupSwiper
      onswiperslidechange={(e) => {
        activeIndex = e.detail[0].realIndex;
      }}
    >
      {#each paddedImgs as img}
        {@const aspectRatio = (() => {
          if (typeof window === "undefined") return 1.5;
          const imageEl = new Image();
          imageEl.src = img.src;
          return imageEl.width / imageEl.height;
        })()}

        <swiper-slide
          class="aspect-3/2 flex items-center justify-center max-[389px]:w-[90%] max-w-89.5 md:max-w-133.75 lg:max-w-270 bg-surface-reversed"
        >
          <img
            class={aspectRatio > 1.5 ? "w-full" : "h-full"}
            src={img.src}
            alt={img.alt}
          />
        </swiper-slide>
      {/each}
    </swiper-container>
  </div>

  <div
    class="flex flex-row justify-between gap-5 max-w-89.5 md:max-w-133.75 lg:max-w-270 max-lg:px-4 mx-auto"
  >
    <div class="font-utility-meta-reg-02 text-text-secondary">
      {paddedImgs[activeIndex].caption}
    </div>

    <div class="flex flex-row justify-end gap-1.5">
      <IconButton icon="https://static.startribune.com/news/projects/all/2026-SYNCHRO/svg/chevron-left.svg" additionalClasses={prevClass} />
      <IconButton icon="https://static.startribune.com/news/projects/all/2026-SYNCHRO/svg/chevron-right.svg" additionalClasses={nextClass} />
    </div>
  </div>
</div>

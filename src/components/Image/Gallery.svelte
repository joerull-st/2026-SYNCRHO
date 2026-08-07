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
        caption: "Stillwater synchronized swimmers practice their extended group routine on the pool deck April 14 at Stillwater Middle School.",
        alt: "Stillwater synchronized swimmers practice their extended group routine on the pool deck April 14 at Stillwater Middle School.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/WZX7QIEOKVAFHMWCR2OWDD23PQ.jpg",
        caption: "Stillwater synchronized swimming coaches Kathy Henderson and Juliet Schmit lead their team through a workout March 24.",
        alt: "Stillwater synchronized swimming coaches Kathy Henderson and Juliet Schmit lead their team through a workout March 24.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/2KF4G2CLYBBUDCAYPPMZSGZNAA.jpg",
        caption: "Assistant coach Juliet Schmit talks with swimmer Audrey Funk as she warms up ahead of Stillwater's first home meet March 31.",
        alt: "Assistant coach Juliet Schmit talks with swimmer Audrey Funk as she warms up ahead of Stillwater's first home meet March 31.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/LJTLYNUOABBDLDNQMZBMZFSJI4.jpg",
        caption: "Sienna Cruz is lifted out of the water by her teammates during a practice.",
        alt: "Sienna Cruz is lifted out of the water by her teammates during a practice.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/RQUS5XAVGZCBDLW3XLSFFJUZAA.jpg",
        caption: "Captain Hailey Schmit warms up with the team ahead of practice.",
        alt: "Captain Hailey Schmit warms up with the team ahead of practice.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/V2LVEXOZ2ZCMPDO6XQ7GEIKCBI.jpg",
        caption: "Stillwater synchronized swimmers practice their extended group routine.",
        alt: "Stillwater synchronized swimmers practice their extended group routine.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/WKINUSPKGJHMDNOFHGXZMKVDIE.jpg",
        caption: "Stillwater synchronized swimmers review video of their extended group routine with assistant coaches Juliet Schmit and Paige Schmit.",
        alt: "Stillwater synchronized swimmers review video of their extended group routine with assistant coaches Juliet Schmit and Paige Schmit.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/YIUGYBO3LBCHJMHVSE4IAIEXQE.jpg",
        caption: "Stillwater synchronized swimmers compete in a home meet April 23.",
        alt: "Stillwater synchronized swimmers compete in a home meet April 23.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/UAJ2UHGNB5EKBL2INVB3HKVLRA.jpg",
        caption: "Stillwater synchronized swimmers compete in a home meet.",
        alt: "Stillwater synchronized swimmers compete in a home meet.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/G7Y25RRGS5CZROO3YN5QFPHWWU.jpg",
        caption: "Stillwater synchronized swimmers compete in a home meet.",
        alt: "Stillwater synchronized swimmers compete in a home meet.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/BRYYWR3PMRCKHDR76GASDNMPBQ.jpg",
        caption: "Captain Hailey Schmit competes in a home meet.",
        alt: "Captain Hailey Schmit competes in a home meet.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/CC6CI556UNFXPAHRQVRRNOSROU.jpg",
        caption: "Stillwater synchronized swimmers laugh together after competing in a home meet.",
        alt: "Stillwater synchronized swimmers laugh together after competing in a home meet.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/3R554EM3RBGI5JC4F2E2WRTNJY.jpg",
        caption: "Teammates help each other with their hair as they prepare for the synchronized swimming state invitational May 22 at the University of Minnesota’s Jean K. Freeman Aquatic Center in Minneapolis.",
        alt: "Teammates help each other with their hair as they prepare for the synchronized swimming state invitational May 22 at the University of Minnesota’s Jean K. Freeman Aquatic Center in Minneapolis.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/HEWGC4H4MJBBPBHHVPIXIB77F4.jpg",
        caption: "Stillwater synchronized swimmers compete in the synchronized swimming state invitational.",
        alt: "Stillwater synchronized swimmers compete in the synchronized swimming state invitational.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/E6Q7V4RMGNHPLFUXG4K4NMPBPU.jpg",
        caption: "Stillwater synchronized swimmers lift captain Hailey Schmit into the air as they compete in the synchronized swimming state invitational.",
        alt: "Stillwater synchronized swimmers lift captain Hailey Schmit into the air as they compete in the synchronized swimming state invitational.",
      },
      {
        src: "https://arc.stimg.co/startribunemedia/BVVDN25LKRHQ3MBPZH6TTLMIWU.jpg",
        caption: "Stillwater synchronized swimmers, including captain Hailey Schmit, center, hoist their first-place trophy into the air after winning the synchronized swimming state invitational.",
        alt: "Stillwater synchronized swimmers, including captain Hailey Schmit, center, hoist their first-place trophy into the air after winning the synchronized swimming state invitational.",
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

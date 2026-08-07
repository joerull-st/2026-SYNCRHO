<!-- 
@component
### ArticleBody component
This is a general workspace illustrating what an article body might look like if you use only the components included in this template.  
ArticleBody doesn't accept any props. All contents will need to be hand-placed by a designer directly inside this component.  
In this example, Grid and GridRow help establish the width of the article body's contents. 
Documentation included with those components and accessed by VSCode tooltip explains each component in greater detail.

#### State in this component
- innerWidth: int - pixel width of the viewport.
- isMobile: boolean - derived from innerWidth, true if less than 768 pixels
- isTablet: boolean - derived from innerWidth, true if between 768 pixels inclusive and 1160 pixels exclusive
- isDesktop: boolean - derived from innerWidth, true if greater than 1160 pixels inclusive

#### Using state in this component
You can use any of the three derived states to render different variants of a GridRow component reactively.
The following example uses a ternary to render an image edge-to-edge on mobile but inline otherwise.

#### Example
```svelte
  <GridRow
    variant={isMobile ? "fullBleed" : "inline"}
  >
    <Image
      src="https://arc.stimg.co/startribunemedia/4SPNT7DI36ANT2SOB5N5EJAIJU.jpg"
      alt="Descriptive alt text"
      caption="Caption tk tk tk"
    />
  </GridRow>
```
-->

<script>
  import { globalState } from "./state.svelte.js";

  import Grid from "./components/Grid/Grid.svelte";
  import GridRow from "./components/Grid/_GridRow.svelte";
  import Subhead from "./components/ArticleBody/_Subhead.svelte";
  import Paragraph from "./components/ArticleBody/_Paragraph.svelte";
  import Dropcap from "./components/ArticleBody/_Dropcap.svelte";
  import Image from "./components/Image/Image.svelte";
  import Gallery from "./components/Image/Gallery.svelte";
  import ScrollySection from "./components/Scrolly/ScrollySection.svelte";
  import JWPlayer from "./components/Video/JWPlayer.svelte";
  import Counter from "./components/Counter/Counter.svelte";

  import Video from "./components/Video/Video.svelte";

  import videos from "./data/videos.json";

  let innerWidth = $state(0);
  let isMobile = $derived(innerWidth < 768);
  let isTablet = $derived(innerWidth >= 768 && innerWidth < 1160);
  let isDesktop = $derived(innerWidth >= 1160);
</script>

<svelte:window bind:innerWidth />
<Grid additionalClasses={"gap-y-5 px-4 md:px-6 min-[1080px]:px-0"}>

<GridRow variant={"inline"}>

            <div class="">
              <p class="rt-Text !text-[.875rem] !font-[graphik-semibold] xs:text-left md:text-left text-text-primary relative md:pt-0 xs:pt-8 ">By <a href="https://www.startribune.com/author/chip-scoggins/6370598" >Chip Scoggins</a></p>
              <p class="rt-Text !text-[.875rem] !font-[graphik-semibold] xs:text-left md:text-left text-text-primary relative pb-2">Photos and video by <a href="https://www.startribune.com/author/anthony-souffle/600335199" >Anthony Soufflé</a></p>
            </div> 
            
            <span class="rt-Text text-text-secondary !text-left font-utility-label-reg-02 mb-1 !text-[.875rem]">The Minnesota Star Tribune</span> <span class="!text-[#666666]  !text-[.75rem] tracking-[1px] !text-left rt-Text font-utility-label-reg-caps-03 text-text-secondary mb-2">August 8, 2026</span>
    </GridRow>



  
  <GridRow variant={"inline"} additionalClasses={"gap-y-5"}>

    <Paragraph>
Eight swimmers slipped below the surface of the water in unison. From the pool deck, the group looked like shadowy figures underwater. Down there in the deep end, the swimmers worked to get into position for something dramatic.
</Paragraph>

<Paragraph>
Suddenly, one of the swimmers launched out of the water, twirled 1½ rotations in a backflip, and the show was on. 
</Paragraph>

<Paragraph>
“Sometimes it’s scary,” Stillwater senior Hailey Schmit said of being thrown out of the water and into the air, “but it’s also really fun.” 
</Paragraph>

</GridRow>
    <GridRow variant={"fullBleed"}>
            <div class="md:!max-w-6xl mt-8 mb-8 mx-auto">
                <div class="md:flex">
                    <div class="mr-0 lg:w-1/2 md:w-full xs:w-full md:mr-2 xs:mr-0 xs:mb-2 md:mb-0">
                        <div class="bg-no-repeat bg-cover bg-top !aspect-[1.4/1] mb-0 h-auto" style="background-image: url('https://arc.stimg.co/startribunemedia/C3QGFOAQ5JCGLNERSYKRJ63HJE.jpg?&amp;w=1080');">
                        </div>
                    </div>
                    <div class="md:ml-0 lg:w-1/2 md:w-full xs:w-full xs:ml-0">
                        <div class="bg-no-repeat bg-cover bg-top !aspect-[1.4/1] mb-0 h-auto" style="background-image: url('https://arc.stimg.co/startribunemedia/LGJ44HK47VGSBL7MGRKZ7DSUS4.jpg?&amp;w=1080');">
                        </div>
                    </div>
                </div>
                <div class="w-screen mx-auto max-w-[1800px] !max-w-6xl gap-y-5 pt-2 pb-4"><img alt="" data-chromatic="ignore" data-testid="InLineImage" loading="lazy" width="0" height="0" decoding="async" data-nimg="1" class="object-cover h-auto w-full" src="https://arc.stimg.co/startribunemedia/U3XAUECZZVHS5DUZLLZLOZSLDI.jpg?&amp;w=1080" style="color: transparent;">
                <div class="!text-[#080808] font-utility-meta-reg-02 text-text-tertiary text-center mx-auto pt-4 px-4" style="max-width: 660px !important;">Stillwater synchronized swimmers, top left, dive into the water to practice their extended group routine on April 11 at Stillwater Middle School. Part of this routine, at top right, is launching captain Hailey Schmit into the air. The Ponies show off their launches, bottom, during the synchronized swimming state invitational on May 22 at the University of Minnesota's Jean K. Freeman Aquatic Center, where they won their sixth consecutive state title.</div>
            </div>
</GridRow>
    <GridRow variant={"inline"} additionalClasses={"gap-y-5 pb-8"}>

<Paragraph>
This isn’t horseplay at a neighborhood pool. At Stillwater High, synchronized swimming is serious business. The state championship banners spread across the wall of the aquatic center reveal an expectation of excellence.
</Paragraph>

<Paragraph>
The Ponies <a href="https://varsity.startribune.com/minnesota-2026-high-school-synchronized-swimming-state-invitational-results/601850071" target="_blank" rel="noreferrer" title="https://varsity.startribune.com/minnesota-2026-high-school-synchronized-swimming-state-invitational-results/601850071">claimed their sixth consecutive state championship</a> in late May.
</Paragraph>

<Paragraph>
“These girls know there are no excuses,” longtime coach Kathy Henderson said. 
</Paragraph>

<Paragraph>
Synchronized swimming is a nontraditional sport that has seen participation slip in Minnesota since the COVID-19 pandemic, with only 13 programs remaining statewide. Roster numbers have dwindled as well. The teams and athletes who participate are passionate advocates of a sport that requires a particular blend of skills.
</Paragraph>

<Paragraph>
“It’s a mix of speed swimming, gymnastics, figure skating and dance,” Schmit said.
</Paragraph>

<Paragraph>
I had never seen synchronized swimming until visiting a Ponies practice. I learned a lot, including that these swimmers devote as much time and effort to their craft as athletes in other sports.
</Paragraph>

<Paragraph>
The older Stillwater swimmers practice four hours a day, six days a week. Most of that time is spent in the pool, rehearsing routines and refining individual skills known as “figures.” 
</Paragraph>

<Paragraph>
Meets feature events such as solos, duets, trios and team competitions. A team can have as many as eight swimmers. The more swimmers involved in a routine, the more complicated and challenging it becomes to get everyone in sync with the choreography set to music.
</Paragraph>

<Paragraph>
“It’s so much more interesting and more involved than just swimming laps for two-and-a-half hours straight,” said Henderson, who is in her 34th season with the program as either head coach or assistant.
</Paragraph>

<Paragraph>
Swimmers are prohibited from touching the bottom of the pool. They stay afloat using techniques called “sculling” and “eggbeaters.” They don’t use the term “treading water.” They have cool lingo to describe certain body positions such as “fishtail,” “hook” and “tabletop.”
</Paragraph>




  </GridRow>
    <GridRow variant="fullBleed">
    <Gallery />
  </GridRow>
    <GridRow variant={"inline"} additionalClasses={"gap-y-5 pb-8"}>




<Paragraph>
Swimmers perform precise movements that resemble ballet while sometimes being upside down underwater. Routines last two to four minutes.
</Paragraph>

<Paragraph>
“It’s physical strength, but you also have to have insane artistry and creativity and body awareness,” said Schmit, the state’s top-ranked synchronized swimmer, who will compete for the Gophers club team next season. “It’s a lot of things combined, which I feel you don’t get with a lot of sports. This allows you to express yourself more.”
</Paragraph>

<Paragraph>
Like most of Stillwater’s older swimmers, Schmit writes her own choreography and picks music for it. The coaches help perfect their routines.
</Paragraph>

<Paragraph>
Henderson and her assistants use a microphone to communicate with swimmers inside the noisy aquatic center. Coaches stop routines and make swimmers repeat sequences if someone is a little slow with the count or if something doesn’t look properly aligned. 
</Paragraph>

<Paragraph>
Stamina is essential in this sport. Among other things, swimmers are judged by pool coverage. In other words, how much of the entire pool do they use in their routines? 
</Paragraph>

<Paragraph>
<a href="https://youtu.be/lBLEy5zUUfs">The most difficult choreography takes place in the deep end</a> (click on the link to watch). Swimmers want to get in and get out of the shallow end quickly because they can’t perform as many skills in that area.
</Paragraph>

<Paragraph>
“You want to cram as much choreography in as you can,” Henderson said. “You want to be creative and artistic, but you also want to be strong and difficult and unique.”
</Paragraph>

<Paragraph>
All those things are why the No. 1 trait Henderson expects of her swimmers is “mental toughness.”
</Paragraph>

<Paragraph>
“It takes a lot to be able to make your body do crazy stuff,” she said. “Make it look pretty with a smile on your face.”
</Paragraph>

<Paragraph>
As a team, the Ponies performed 23 routines this season of various sizes and levels of expertise. All but one of those routines qualified for the state meet, and all 22 placed in the top seven, thus earning points.
</Paragraph>

<Paragraph>
The Ponies finished with 179 points to claim the title, well ahead of runner-up Wayzata at 90.
</Paragraph>

<Paragraph>
Stillwater has never finished lower than second place in the five decades that Minnesota has declared a state champion. The Ponies carry that legacy every time they jump into the pool.
</Paragraph>

</GridRow>
    <GridRow variant={"fullBleed"}>
            <div class="md:!max-w-6xl mt-8 mb-8 mx-auto">
                <div class="md:flex">
                    <div class="mr-0 lg:w-1/2 md:w-full xs:w-full md:mr-2 xs:mr-0 xs:mb-2 md:mb-0">
                        <div class="bg-no-repeat bg-cover bg-top !aspect-[1.4/1] mb-0 h-auto" style="background-image: url('https://arc.stimg.co/startribunemedia/MKAX7WFAN5GDLJXNYTDEOUDD5A.jpg?&amp;w=1080');">
                        </div>
                    </div>
                    <div class="md:ml-0 lg:w-1/2 md:w-full xs:w-full xs:ml-0">
                        <div class="bg-no-repeat bg-cover bg-top !aspect-[1.4/1] mb-0 h-auto" style="background-image: url('https://arc.stimg.co/startribunemedia/DXJJSHOM5JARROOOSDZEQ7XXPM.jpg?&amp;w=1080');">
                        </div>
                    </div>
                </div>
                <div class="w-screen mx-auto max-w-[1800px] !max-w-6xl gap-y-5 pt-2 pb-4"><img alt="" data-chromatic="ignore" data-testid="InLineImage" loading="lazy" width="0" height="0" decoding="async" data-nimg="1" class="object-cover h-auto w-full" src="https://arc.stimg.co/startribunemedia/BJXRANLULND5TKGZEP2UNFSSJ4.jpg?&amp;w=1080" style="color: transparent;">
                <div class="!text-[#080808] font-utility-meta-reg-02 text-text-tertiary text-center mx-auto pt-4 px-4" style="max-width: 660px !important;">Stillwater synchronized swimmers sit together, top left, as they prepare to compete in a home meet April 23. At top right, teammates Hanna Wiese, Andelyn Filandrinos and Gabby Lalande talk with head coach Kathy Henderson during practice March 24. Henderson gives a hug to her seniors, bottom, ahead of the synchronized swimming state invitational May 22 at the University of Minnesota’s Jean K. Freeman Aquatic Center.</div>
            </div>
</GridRow>
    <GridRow variant={"inline"} additionalClasses={"gap-y-5 pb-8"}>


<Paragraph>
“A lot of times we talk about family,” Henderson said. “These are like your sisters for 12 weeks. You’re going to fight and cry sometimes, and in the end, you’re going to fight for each other and cry for the good reasons.” 
</Paragraph>

<Paragraph>
Hanging state championship banners every year brings those happy tears.
</Paragraph>

  </GridRow>

  <!-- <GridRow>
    <Counter
      count={globalState.count}
      handleIncrement={() => {
        globalState.count++;
      }}
      handleDecrement={() => {
        globalState.count--;
      }}
    />
  </GridRow>

  <GridRow variant="fullBleed">
    <Gallery />
  </GridRow>

  <GridRow variant={"fullBleed"}>
    <Image
      variant={"captionCentered"}
      src="https://arc.stimg.co/startribunemedia/4SPNT7DI36ANT2SOB5N5EJAIJU.jpg"
      alt="Descriptive alt text"
      caption="Caption tk tk tk"
    />
  </GridRow> -->

  <!-- <GridRow variant="inline">
    <Paragraph
      >Voluptate molestiae, perferendis iusto dolor officiis eaque cum quisquam
      quidem, doloremque dicta temporibus fuga ducimus voluptatum excepturi
      ratione laborum ab omnis quibusdam, accusamus vel eum culpa repellendus
      exercitationem. Fugit, consequatur!</Paragraph
    >






  </GridRow>

  <GridRow variant={isMobile ? "fullBleed" : "inline"}>
    <Image
      src="https://arc.stimg.co/startribunemedia/4SPNT7DI36ANT2SOB5N5EJAIJU.jpg"
      alt="Descriptive alt text"
      caption="Caption tk tk tk"
    />
  </GridRow> -->

  <!-- <GridRow variant={"fullBleed"}>
    <ScrollySection
      data={[
        {
          step: 0,
          color: "#143D11",
          text: "In response to this card's appearance in the viewport, the background color is now #143D11.",
        },
        {
          step: 1,
          color: "#5E95D6",
          text: "In response to this card's appearance in the viewport, the background color is now #5E95D6.",
        },
        {
          step: 2,
          color: "#CCCCCC",
          text: "In response to this card's appearance in the viewport, the background color is now #CCCCCC.",
        },
        {
          step: 3,
          color: "#B13B5B",
          text: "In response to this card's appearance in the viewport, the background color is now #B13B5B.",
        },
        {
          step: 4,
          color: "#804316",
          text: "In response to this card's appearance in the viewport, the background color is now #804316.",
        },
        {
          step: 5,
          color: "#B28333",
          text: "In response to this card's appearance in the viewport, the background color is now #B28333.",
        },
        {
          step: 6,
          color: "#052949",
          text: "In response to this card's appearance in the viewport, the background color is now #052949.",
        },
      ]}
    />
  </GridRow> -->
<!-- 
  <GridRow variant="inline" additionalClasses={"gap-y-5"}>
    <Subhead>Subhead</Subhead>

    <Paragraph
      >Quis quaerat tempore adipisci nostrum quia non. Provident, eum! Non quam
      suscipit omnis asperiores cupiditate, a eos, aliquid libero, reprehenderit
      rerum excepturi ex. Eius perferendis rem fugit nostrum eveniet magnam.</Paragraph
    > -->

    <!-- Native <video> Video component (replaces JW Player). Build-time-resolved
         clip JSON spread in; inline variant keeps the minimal-UX overlay. -->
    <!-- <Video
      {...videos.find((v) => v.uuid === "ca87479d-8b16-4f7b-94e3-be0a28b72be0")}
      credit="Video by the Minnesota Star Tribune"
      variant="inline"
    />

    <Paragraph
      >Quis quaerat tempore adipisci nostrum quia non. Provident, eum! Non quam
      suscipit omnis asperiores cupiditate, a eos, aliquid libero, reprehenderit
      rerum excepturi ex. Eius perferendis rem fugit nostrum eveniet magnam.</Paragraph
    >

    <Paragraph
      >Quis quaerat tempore adipisci nostrum quia non. Provident, eum! Non quam
      suscipit omnis asperiores cupiditate, a eos, aliquid libero, reprehenderit
      rerum excepturi ex. Eius perferendis rem fugit nostrum eveniet magnam.</Paragraph
    >
  </GridRow>

  <GridRow variant={isMobile ? "fullBleed" : "default"}>
    <Image
      src="https://arc.stimg.co/startribunemedia/4SPNT7DI36ANT2SOB5N5EJAIJU.jpg"
      alt="Descriptive alt text"
      caption="Caption tk tk tk"
    />
  </GridRow> -->
</Grid>

<style>
  a {
    text-decoration-line: underline;
    text-decoration-color: #00854b;
    text-underline-offset: 2px;
  }

  a:hover {
    color: #00854b;
  }
</style>

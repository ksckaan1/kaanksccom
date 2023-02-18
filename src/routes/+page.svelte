<script>
    import {fade, fly} from "svelte/transition";
    import ppimg from "../lib/img/pp.png";
    import quoteStart from "../lib/img/quote-start.png";
    import quoteEnd from "../lib/img/quote-end.png";

    const quotes = [
        {
            text: "Any fool can write code that a computer can understand. Good programmers write code that humans can understand.",
            owner: "Martin Fowler"
        },
        {
            text: "Experience is the name everyone gives to their mistakes",
            owner: "Oscar Wilde"
        },
        {
            text: "Perfection is achieved not when there is nothing more to add, but rather when there is nothing more to take away.",
            owner: "Antoine de Saint – Exupery"
        },
        {
            text: "Code is like humor. When you have to explain it, it’s bad",
            owner: "Cory House"
        },
        {
            text: "Optimism is an occupational hazard of programming: feedback is the treatment",
            owner: "Kent Beck"
        },
        {
            text: "Simplicity is the soul of efficiency",
            owner: "Austin Freeman"
        },
        {
            text: "Before software can be reusable it first has to be usable",
            owner: "Ralph Johnson"
        }
    ]

    const randomQuote = () => {
        return quotes[Math.floor(Math.random() * quotes.length)]
    }

    const quote = randomQuote();
</script>
<section class="flex flex-col xl:flex-row">
    <img alt="" class="z-0 xl:absolute top-0 right-0 h-1/2 xl:h-screen w-screen xl:w-2/5 object-cover"
         in:fly={{ x: 500, duration: 500, delay: 200}}
         out:fade={{duration: 200}}
         src="{ppimg}">
    <div class="mx-auto container p-10 xl:h-screen flex flex-col justify-center items-start"
         in:fly={{ x: -500, duration: 500, delay: 200}}
         out:fade={{duration: 200}}
    >
        <div class="xl:w-1/2 flex flex-col items-start gap-y-3">
            <p class="text-3xl font-black text-kWhite xl:text-4xl">HI THERE!</p>
            <p class="text-4xl xl:text-6xl font-black text-kWhite">I'M <span
                    class="text-kYellow whitespace-nowrap">KAAN KUSCU</span>
            </p>
            <div class="flex gap-2 sm:items-center flex-col sm:flex-row">
                <div class="bg-kYellow inline-block text-2xl xl:text-4xl px-3 py-2 font-black text-kPurpleDark whitespace-nowrap"
                     in:fly={{ x: -100, duration: 500, delay: 400}}>
                    BACKEND DEVELOPER
                </div>
                <div class="text-2xl xl:text-4xl text-kWhite">
                    @ <a href="http://www.isimizbu.com.tr/" target="_blank">İŞİMİZBU</a>
                </div>
            </div>

            <span class="text-kWhite text-lg">In the field of software, which we can generally call backend, I develop performance and secure services and cli applications.</span>
            <div
                    class="flex flex-col mt-10 items-start gap-y-3 w-full"
                    in:fly={{ y: 50, duration: 1000, delay: 600}}>
                <img alt="" src="{quoteStart}">
                <span class="text-lg text-kWhite">
                {quote.text}
            </span>
                <div class="flex justify-end w-full gap-x-2">
                    <span class="text-kWhite/50">{quote.owner}</span>
                    <img alt="" src="{quoteEnd}">
                </div>
            </div>
        </div>
    </div>
</section>

<style>
</style>

<script lang="ts">
    import {onMount} from "svelte";
    import {fade, fly} from "svelte/transition"
    import type {IBlog} from "../../models/blog";
    import Loading from "../../components/Loading.svelte";

    let blogs: IBlog[] = [];
    let isBlogLoaded = false;

    onMount(async () => {
        const RSS_URL = "https://dev.to/feed/ksckaan1"

        await fetch(RSS_URL)
            .then((response: Response) => response.text())
            .then((text: string) => {
                let dp = new DOMParser();
                let doc: Document = dp.parseFromString(text, "text/xml");

                let items = doc.querySelectorAll("item");
                items.forEach(el => {
                    let blogItem = {} as IBlog;

                    blogItem.title = el.querySelector("title")?.innerHTML
                    blogItem.pubDate = el.querySelector("pubDate")?.innerHTML
                    blogItem.link = el.querySelector("link")?.innerHTML

                    let cats: string[] = [];

                    el.querySelectorAll("category").forEach(cat => {
                        cats.push(cat.innerHTML)
                    })

                    blogItem.categories = cats

                    blogs = [...blogs, blogItem]
                })
            })
        isBlogLoaded = true;
    })
</script>
<svelte:head>
    <title>Blog | Kaan Kuscu - Backend Developer</title>
</svelte:head>
<div class="template">
    <div class="section-title mb-5"
         in:fly={{ y: 100, duration: 500, delay: 200}}
         out:fade={{duration: 200}}
    >
        BLOG
    </div>
    {#if isBlogLoaded && blogs.length !== 0}
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-5" out:fade={{duration:200}}>
            {#each blogs as blog,i}
                <a target="_blank" rel="noreferrer" href="{blog.link}"
                   in:fly={{x:100,duration:500,delay: (i+1)*100+200}}>
                    <div class="border border-kWhite rounded-lg p-5">
                        <div class="text-kYellow text-lg font-bold">
                            {blog.title}
                        </div>
                        <div class="text-kWhite/50 ">
                            {blog.pubDate.replace(" +0000", "")}
                        </div>
                        <div class="flex flex-row flex-wrap gap-2">
                            {#each blog.categories as cat}
                                <span class="text-kWhite">#{cat}</span>
                            {/each}
                        </div>
                    </div>
                </a>
            {/each}
        </div>
    {:else if isBlogLoaded && blogs.length === 0}
        No blog post found
    {:else}
        <Loading/>
    {/if}
</div>


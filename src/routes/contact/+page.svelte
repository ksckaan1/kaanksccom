<script lang="ts">
    import {fade, fly} from "svelte/transition";
    import githubIcon from "../../lib/img/icons/github.svg"
    import twitterIcon from "../../lib/img/icons/twitter.svg"
    import instagramIcon from "../../lib/img/icons/instagram.svg"
    import redditIcon from "../../lib/img/icons/reddit.svg"
    import youtubeIcon from "../../lib/img/icons/youtube.svg"
    import linkedinIcon from "../../lib/img/icons/linkedin.svg"
    import emailIcon from "../../lib/img/icons/email.svg"

    const contractList = [
        {
            name: "GitHub",
            url: "https://github.com/ksckaan1",
            icon: githubIcon
        },
        {
            name: "Twitter",
            url: "https://twitter.com/ksckaan1",
            icon: twitterIcon
        },
        {
            name: "Instagram",
            url: "https://instagram.com/ksckaan1",
            icon: instagramIcon
        },
        {
            name: "Reddit",
            url: "https://www.reddit.com/user/ksckaan1",
            icon: redditIcon
        },
        {
            name: "YouTube",
            url: "https://www.youtube.com/@ksckaan1",
            icon: youtubeIcon
        },
        {
            name: "Linkedin",
            url: "https://www.linkedin.com/in/ksckaan1/",
            icon: linkedinIcon
        },
        {
            name: "E-mail",
            url: "mailto:me@kaanksc.com",
            icon: emailIcon
        }
    ]
</script>
<svelte:head>
    <title>Contact | Kaan Kuscu - Backend Developer</title>
</svelte:head>
<section class="template" out:fade={{duration: 200}}>
    <div class="section-title mb-5"
         in:fly={{ y: 100, duration: 500, delay: 200}}
         out:fade={{duration: 200}}
    >
        CONTACT
    </div>

    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-5">
        {#each contractList as contact,i}
            <a target="_blank" href="{contact.url}" in:fly={{ x: 500, duration: 500, delay: 100*(i+1)}}>
                <div class="border border-kWhite rounded-lg aspect-square flex flex-col">
                    <div class="w-full h-[calc(100%-70px)] p-10 flex justify-center items-center">
                        <img class="w-2/3" src="{contact.icon}" alt="{contact.name}">
                    </div>
                    <div class="contact-title text-center">{contact.name.toUpperCase()}</div>
                </div>
            </a>
        {/each}
    </div>

</section>

<style lang="postcss">
    .contact-title {
        @apply text-kPurpleDark text-2xl sm:text-4xl font-black tracking-widest;
        -webkit-text-stroke: 1px rgb(245 179 47);
    }
</style>
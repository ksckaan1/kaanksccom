<script lang="ts">
    import {fly} from "svelte/transition";
    import menuIcon from "../lib/img/icons/menu.svg"
    import closeIcon from "../lib/img/icons/close.svg"

    let isDrawerActive = false;


    let navLinks = [
        {
            title: "LANDING",
            url: "/",
        },
        {
            title: "SKILLS",
            url: "/skills"
        },
        {
            title: "PROJECTS",
            url: "/projects"
        },
        {
            title: "BLOG",
            url: "/blog"
        },
        {
            title: "CONTACT",
            url: "/contact"
        }
    ]
</script>

<div class="top">
    <header>
        <nav class="mobile">
            <img alt="" class="btn" on:click={()=> isDrawerActive = true} src="{menuIcon}">
        </nav>
        <nav class="desktop">
            {#each navLinks as link, i}
                <a href="{link.url}">{link.title}</a>
            {/each}
        </nav>
    </header>
</div>

{#if isDrawerActive}
    <div class="drawer" in:fly={{x: -300, duration: 500}} out:fly={{duration:500,x:-300}}>
        <img class="btn" src="{closeIcon}" alt="" on:click={()=> isDrawerActive = false}>

        <nav class="mobile-menu">
            {#each navLinks as link,i}
                <a
                        on:click={()=> isDrawerActive = false}
                        in:fly={{ y: 100, duration: 500, delay: (i+1)*100 }}
                        href="{link.url}">{link.title}</a>
            {/each}
        </nav>
    </div>
{/if}

<style lang="postcss">
    .top {
        @apply absolute top-0 w-screen z-20
    }

    header {
        @apply p-10 container mx-auto
    }

    header nav.desktop {
        @apply gap-x-5 hidden xl:flex
    }

    nav.desktop a {
        @apply text-kPurpleDark xl:text-kWhite text-2xl font-bold hover:text-kYellow transition-all duration-500
    }

    header nav.mobile {
        @apply text-kWhite xl:hidden
    }

    header nav.mobile i {
        @apply text-6xl cursor-pointer text-kYellow
    }

    .drawer {
        @apply w-screen z-20 h-screen bg-kPurpleDark fixed top-0 left-0 transition-all duration-500 flex flex-col p-10 items-start;
    }

    .drawer i {
        @apply text-kYellow text-6xl cursor-pointer
    }

    .mobile-menu {
        @apply flex flex-col gap-y-10 text-4xl text-kWhite font-bold mt-20
    }

    .mobile-menu a {
        @apply hover:text-kYellow transition-all duration-500
    }

    img.btn {
        @apply h-10 cursor-pointer
    }
</style>
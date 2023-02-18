<script lang="ts">
    import {getRepositories} from "../../utils/github";
    import type {IRepo} from "../../models/repo";
    import {onMount} from "svelte";
    import {fade, fly} from "svelte/transition";

    import starIcon from "../../lib/img/icons/star.svg";
    import forkIcon from "../../lib/img/icons/fork.svg";
    import loadingIcon from "../../lib/img/icons/loading.png";

    let isReposLoaded = false;
    let repos: IRepo[] = [];

    onMount(() => {
        getRepositories().then(r => {
            repos = r
            isReposLoaded = true;
        });
    })
</script>
<svelte:head>
    <title>Projects | Kaan Kuscu - Backend Developer</title>
</svelte:head>
<section class="template">
    <div class="section-title mb-5"
         in:fly={{ y: 100, duration: 500, delay: 200}}
         out:fade={{duration: 200}}
    >
        PROJECTS
    </div>
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-5">
        {#if isReposLoaded && repos.length !== 0}
            {#each repos as repo,i}
                <div class="frame" in:fly={{ x: 100, duration: 500, delay: 200 + (i+1)*50}}>
                    <div class="border-b border-kWhite text-kYellow text-center py-1">
                        {repo.name}
                    </div>
                    <div class="bg-gridbg bg-opacity-10 bg-cover flex-1 flex flex-col">
                        <div class="text-kWhite text-center p-3 flex-1">
                            {repo.description || "Açıklama yok"}
                        </div>
                        <div class="flex justify-center mb-5 gap-x-5">
                            <div class="flex gap-x-2 items-center">
                                <img src="{starIcon}" class="h-5" alt="">
                                <span class="text-kWhite">{repo.stargazers_count}</span>
                            </div>

                            <div class="flex gap-x-2 items-center">
                                <img src="{forkIcon}" class="h-5" alt="">
                                <span class="text-kWhite">{repo.forks}</span>
                            </div>
                        </div>

                        <div class="text-center mb-5">
                            <a target="_blank" class="text-kYellow" href="{repo.html_url}">Browse</a>
                        </div>
                    </div>
                </div>
            {/each}
        {:else if isReposLoaded && repos.length === 0}
            Repo bulunamadı
        {:else}
            <img in:fade={{duration: 200, delay:200}} out:fade={{duration: 200}} src="{loadingIcon}" class="loading"
                 alt="">
        {/if}
    </div>
</section>

<style lang="postcss">
    .frame {
        @apply border border-kWhite rounded-lg flex flex-col
    }
</style>

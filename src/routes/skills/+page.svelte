<script lang="ts">
    import {fade, fly} from "svelte/transition";
    import goIcon from "../../lib/img/icons/go.svg"
    import golandIcon from "../../lib/img/icons/goland.svg"
    import fiberIcon from "../../lib/img/icons/fiber.svg"
    import grpcIcon from "../../lib/img/icons/grpc.svg"
    import mongodbIcon from "../../lib/img/icons/mongodb.svg"
    import postgresqlIcon from "../../lib/img/icons/postgresql.svg"
    import rabbitmqIcon from "../../lib/img/icons/rabbitmq.svg"
    import javascriptIcon from "../../lib/img/icons/javascript.svg"
    import typescriptIcon from "../../lib/img/icons/typescript.svg"
    import dartIcon from "../../lib/img/icons/dart.svg"
    import flutterIcon from "../../lib/img/icons/flutter.svg"
    import getxIcon from "../../lib/img/icons/getx.svg"
    import svelteIcon from "../../lib/img/icons/svelte.svg"
    import vueIcon from "../../lib/img/icons/vue.svg"
    import tailwindcssIcon from "../../lib/img/icons/tailwindcss.svg"
    import htmlIcon from "../../lib/img/icons/html.svg"
    import cssIcon from "../../lib/img/icons/css.svg"
    import gitIcon from "../../lib/img/icons/git.svg"
    import githubIcon from "../../lib/img/icons/github.svg"
    import gitlabIcon from "../../lib/img/icons/gitlab.svg"
    import webstormIcon from "../../lib/img/icons/webstorm.svg"
    import postmanIcon from "../../lib/img/icons/postman.svg"
    import figmaIcon from "../../lib/img/icons/figma.svg"
    import lunacyIcon from "../../lib/img/icons/lunacy.svg"
    import dockerIcon from "../../lib/img/icons/docker.svg"
    import awsIcon from "../../lib/img/icons/aws.svg"
    import herokuIcon from "../../lib/img/icons/heroku.svg"

    const backendSkills = [
        {
            name: "golang",
            icon: goIcon
        },
        {
            name: "fiber",
            icon: fiberIcon
        },
        {
            name: "grpc",
            icon: grpcIcon
        },
        {
            name: "mongodb",
            icon: mongodbIcon
        },
        {
            name: "postgresql",
            icon: postgresqlIcon
        },
        {
            name: "rabbitmq",
            icon: rabbitmqIcon
        },
    ]

    const frontendSkills = [
        {
            name: "javascript",
            icon: javascriptIcon
        },
        {
            name: "typescript",
            icon: typescriptIcon
        },
        {
            name: "dart",
            icon: dartIcon
        },
        {
            name: "flutter",
            icon: flutterIcon
        },
        {
            name: "getx",
            icon: getxIcon
        },
        {
            name: "svelte",
            icon: svelteIcon
        },
        {
            name: "vue",
            icon: vueIcon
        },
        {
            name: "tailwindcss",
            icon: tailwindcssIcon
        },
        {
            name: "html",
            icon: htmlIcon
        },
        {
            name: "css",
            icon: cssIcon
        },
    ]

    const tools = [
        {
            name: "git",
            icon: gitIcon
        },
        {
            name: "github",
            icon: githubIcon
        },
        {
            name: "gitlab",
            icon: gitlabIcon
        },
        {
            name: "goland",
            icon: golandIcon
        },
        {
            name: "webstorm",
            icon: webstormIcon
        },
        {
            name: "vscode",
            icon: cssIcon
        },
        {
            name: "postman",
            icon: postmanIcon
        },
        {
            name: "figma",
            icon: figmaIcon
        },
        {
            name: "lunacy",
            icon: lunacyIcon
        },
        {
            name: "docker",
            icon: dockerIcon
        },
        {
            name: "aws",
            icon: awsIcon
        },
        {
            name: "heroku",
            icon: herokuIcon
        },
    ]
</script>
<svelte:head>
    <title>Skills | Kaan Kuscu - Backend Developer</title>
</svelte:head>
<section
        class="template"
        in:fly={{ y: 100, duration: 500, delay: 200}}
        out:fade={{duration: 200}}>
    <div class="section-title">
        BACKEND
    </div>
    <div class="gridList">
        {#each backendSkills as skill,i}
            <div class="gridItem" in:fly={{ x: 500, duration: 500, delay: 100*(i+1)}}>
                <div class="frame">
                    <img class="icon" src="{skill.icon}" alt="">
                </div>
                <div class="title">{skill.name.toUpperCase()}</div>
            </div>
        {/each}
    </div>
    <div class="section-title mt-16">
        FRONTEND
    </div>
    <div class="gridList">
        {#each frontendSkills as skill,i}
            <div class="gridItem" in:fly={{ x: 500, duration: 500, delay: 100*(i+1)}}>
                <div class="frame">
                    <img class="icon" src="{skill.icon}" alt="">
                </div>
                <div class="title">{skill.name.toUpperCase()}</div>
            </div>
        {/each}
    </div>
    <div class="section-title mt-16">
        TOOL & OTHERS
    </div>
    <div class="gridList">
        {#each tools as skill,i}
            <div class="gridItem" in:fly={{ x: 500, duration: 500, delay: 100*(i+1)}}>
                <div class="frame">
                    <img class="icon" src="{skill.icon}" alt="">
                </div>
                <div class="title">{skill.name.toUpperCase()}</div>
            </div>
        {/each}
    </div>
</section>

<style lang="postcss">
    .gridList {
        @apply grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-5 mt-5;
    }

    .gridItem {
        @apply border border-kWhite rounded-lg flex flex-col;
    }

    .gridItem .frame {
        @apply px-10 py-10 aspect-video bg-gridbg bg-cover;
    }

    .gridItem .icon {
        @apply w-full aspect-video;
    }

    .gridItem .title {
        @apply border-t border-kWhite py-3 text-center text-kWhite font-bold text-lg sm:text-xl;
    }

</style>
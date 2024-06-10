<script lang="ts">
    import MdLaunch from 'svelte-icons/md/MdLaunch.svelte';
    import CONTESTS_ from '../contests.json';

    const CONTESTS = (CONTESTS_ as Array<{
        title: string;
        date: string;
        link: string;
        description: string;
    }>)
        .map(c => ({ ...c, date: new Date(c.date) }))
        .filter(c => c.date.getTime() <= Date.now());

    function navTo(uri: string): void {
        window.location.href = uri;
    }
</script>

<style lang="scss">
    @use '../lib/styles/global.scss' as *;
    @use '../lib/styles/breakpoints.scss' as *;
    @use 'sass:map';

    :root {
        --highlight-color: var(--color-secondary);
    }

    .content {
        flex: 1 1 auto;
        display: flex;
        align-items: center;
        width: 100%;
        flex-direction: column;
        
        > .contest {
            background: url('/glitch.gif') repeat, rgba(#000, 0.975);
            background-size: 86ex 24em;
            background-blend-mode: multiply;
            width: 100%;
            flex: 1 1 auto;
            margin: 0;
            font-family: inherit;
            font-weight: inherit;
            font-size: inherit;
            text-align: inherit;
            border: none;
            vertical-align: inherit;
            cursor: pointer;
            color: inherit;
            padding: 8ex;
            
            &:hover {
                background: var(--highlight-color);
                color: black;
            }

            &:hover > .body {
                transform: scale(1.05);
            }
            
            > .body {
                margin: 0 auto;
                max-width: map.get(map.get($breakpoints, 'md'), 'breakpoint');
                transition: transform 0.1s ease-out;

                > h2 {
                    margin: 0;
                    font-style: var(--font-pixel);
                    text-decoration: underline;
                    font-family: 'Groteks-Bold';
                }
    
                > .date {
                    margin-left: 2ex;
                    font-style: italic;
                }
    
                > .link-icon {
                    float:right;
                    height: 1.5em;
                }
    
                > .description {
                    text-align: justify;
                }
            }

            &:not(:last-child) {
                border-bottom: 0.125em dashed var(--highlight-color);
            }
        }
    }
</style>

<div class="content">
    {#each CONTESTS as contest}
    <button class="contest" on:click={() => navTo(contest.link)}>
        <div class="body">
            <div class="link-icon">
                <MdLaunch />
            </div>
            <h2>{contest.title}</h2>
            <div class="date">{contest.date.toLocaleDateString()}</div>
            <div class="description">
                {contest.description}
            </div>
        </div>
    </button>
    {/each}
</div>
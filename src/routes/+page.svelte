<script lang="ts">
    import { goto } from '$app/navigation';
    import MdLaunch from 'svelte-icons/md/MdLaunch.svelte';

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
            background: none;
            color: inherit;
            padding: 8ex;
            
            &:hover {
                background-color: var(--highlight-color);
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
    <button class="contest" on:click={() => navTo('https://dragonfly-xyz.github.io/nottingham-frontend')}>
        <div class="body">
            <div class="link-icon">
                <MdLaunch />
            </div>
            <h2>Searchers of Nottingham</h2>
            <div class="date">06/15/2024</div>
            <div class="description">
                Submit smart contract agents to compete against other merchants at a medieval faire in this multiplayer, MEV-themed game.
            </div>
        </div>
    </button>
    <button class="contest" on:click={() => navTo('https://ctf.dragonfly.xyz')}>
        <div class="body">
            <div class="link-icon">
                <MdLaunch />
            </div>
            <h2>Puzzlebox</h2>
            <div class="date">05/05/2023</div>
            <div class="description">
                Can you unlock this puzzlebox of fiendishly clever, inteconnected Solidity puzzles? How efficently can you do it?
            </div>
        </div>
    </button>
</div>
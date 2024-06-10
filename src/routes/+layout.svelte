<style lang="scss">
    @use '../lib/styles/global.scss' as *;
    @use '../lib/styles/breakpoints.scss' as *;

    :global(body) {
        background-color: black;
        padding: 0;
        margin: 0;
        border: min(2vw, 2vh) solid var(--color-secondary);
        box-sizing: border-box;
        min-height: 100vh;
        display: flex;
        flex-direction: column;

        @include mobile {
            border-left: none;
            border-right: none;
            border-bottom-width: 2vh;
        }
    }

    main {
        flex: 1 1 auto;
        font-family: var(--font-primary);
        color: var(--color-primary);
        font-size: 1.33em;
        padding: 0;
        margin: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    h1 {
        margin: 0;
        padding: 0 2ex 0.5em 4ex;
        background-color: var(--color-secondary);
        font-family: var(--font-title);
        font-weight: bold;;
        text-transform: uppercase;
        letter-spacing: -0.2ex;
        display: flex;
        justify-content: space-between;
        font-size: 2.25em;

        @include mobile {
            font-size: 1.75em;
        }
    }

    .logo {
        letter-spacing: 0.05ex;
        font-weight: bolder;
    }

    .smaller {
        font-size: 0.8em;
    }

    .title {
        letter-spacing: 0.05ex;
        color: white;

        &.mobile {
            display: none;
        }

        @include mobile {
            display: none;
            &.mobile {
                display: initial;
            }
        }
    }

    .home {
        text-decoration: none;
        color: inherit;
        font-weight: inherit;
        display: flex;
        gap: 2ex;
        transition: transform 0.1s ease-out;

        &:hover {
            color: white;
            transform: translate(1ex, 0);
        }

        > .logo {
            margin-top: -0.1em;
        }
    }
</style>

<h1>
    <span class="title mobile">
        ./CTFs
    </span>
    <span class="title desktop">
        ./CAPTURE_THE_FLAGS
    </span>
    <a class="home smaller" href="https://dragonfly.xyz">
        <span>Dragonfly</span>
        <span class="logo">
            &gt;|&lt;
        </span>
    </a>
</h1>
<main>
    <slot />
</main>
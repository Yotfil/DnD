<script>
    import Card from './Card.svelte';

    const arrSkeleton = new Array(100);
    let allMonsters = [];
    let dataCharged = false;

    const getMonsters = () => {
        fetch(`https://www.dnd5eapi.co/api/monsters`)
            .then(function (response) {
                if (response.ok) {
                    return response.json();
                }
            })
            .then((data) => {
                allMonsters = data.results;
                setTimeout(() => {
                    dataCharged = true;
                }, 2000);
            });
    };
    getMonsters();
</script>

{#if dataCharged}
    <main class="main">
        {#each allMonsters as monster}
            <Card monster={monster.url} />
        {/each}
    </main>
{/if}
{#if !dataCharged}
    <main class="main">
        {#each arrSkeleton as monster}
            <div class="cardSkeleton">
                <div class="headerSkeleton" />
            </div>
        {/each}
    </main>
{/if}

<style>
    /* Skeleton */
    .cardSkeleton {
        width: 30%;
        height: 400px;
        background-color: rgb(34, 34, 34);
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
        border-radius: 4px;
        margin: 20px 0;
    }
    .headerSkeleton {
        width: 100%;
        height: 45px;
        background-color: rgb(57, 57, 57);
    }

    /* Real Styles */
    .main {
        max-width: 1200px;
        margin: auto;
        display: flex;
        justify-content: space-between;
        align-items: flex-start;
        flex-wrap: wrap;
    }

    @media screen and (max-width: 768px) {
        .main {
            justify-content: space-around;
        }
        .cardSkeleton {
            width: 45%;
        }
    }
</style>

<script>
    export let size = '';
    export let type = '';
    export let challenge_rating = '';
    export let alignment = '';
    export let languages = '';
    // export let { walk } = '';
    // export let { fly } = '';
    // export let { burrow } = '';
    export let title = '';
    export let speed = '';

    let showCollapsable = false;

    const collapsableShow = (e) => {
        console.log(e);
        showCollapsable = !showCollapsable;
    };
</script>

<div class="contCollapsable">
    <div class="switchCollapsable" on:click={collapsableShow}>
        <i class="fas fa-chevron-down arrow" class:rotate={showCollapsable} />
        <h4 class="title">{title}</h4>
    </div>

    <div class="collapsable" class:showCollapsable>
        <div class="cont">
            <p class="fact"><b>XP: </b>15.000</p>
            <p class="fact"><b>Size: </b> {size}</p>
            <p class="fact"><b>Type: </b> {type}</p>
            <p class="fact"><b>Challenge rating: </b> {challenge_rating}</p>
            <p class="fact"><b>Challenge rating: </b> {alignment}</p>
            <p class="fact"><b>Challenge rating: </b> {languages}</p>
        </div>
        <div class="cont">
            <div class="speed">
                <p class="sub"><b>Speed</b></p>
                {#if speed.fly}
                    <p class="subValue"><b>Fly: </b>{speed.fly}</p>
                {/if}
                {#if speed.walk}
                    <p class="subValue"><b>Walk: </b>{speed.walk}</p>
                {/if}
                {#if speed.burrow}
                    <p class="subValue"><b>Burrow: </b>{speed.burrow}</p>
                {/if}
            </div>
        </div>
    </div>
</div>

<style>
    .contCollapsable {
        width: 90%;
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
        border: 1px solid rgb(25, 25, 25);
        box-shadow: 0 3px 1px -2px rgba(0, 0, 0, 0.2),
            0 2px 2px 0 rgba(0, 0, 0, 0.14), 0 1px 5px 0 rgba(0, 0, 0, 0.12);
        position: relative;
        transition: all 0.5s ease-in-out;
        margin: auto;
    }
    .switchCollapsable {
        height: 34px;
        cursor: pointer;
        width: 100%;
    }
    .collapsable {
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;
        border-radius: 4px;
        overflow: hidden;
        cursor: pointer;
        height: 0;
    }
    .title,
    .fact,
    .sub,
    .subValue,
    .arrow {
        color: rgb(183, 183, 183);
    }
    .arrow {
        position: absolute;
        right: 10px;
        top: 10px;
        transition: all 0.8s ease-in-out;
    }
    .title {
        width: 100%;
        margin-bottom: 10px;
        text-align: center;
    }
    .cont {
        width: 60%;
        display: flex;
        justify-content: center;
        align-items: flex-start;
        flex-direction: column;
    }
    .cont:nth-child(2) {
        width: 35%;
    }
    .fact {
        line-height: 1;
        margin: 5px 0;
    }
    .showCollapsable {
        height: auto;
        transition: all 0.5s ease-in-out;
        margin: 20px auto 10px;
        padding: 0 20px 10px;
        height: auto;
    }
    .rotate {
        transform: rotate(540deg);
        transition: all 0.8s ease-in-out;
    }
</style>

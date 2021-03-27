<script>
    export let nameAbility = '';
    export let valueAbility = '';
    export let modifier = null;
    export let edit = false;
</script>

<div class="contAbility">
    <label class="nameAbility" for=""> {nameAbility} </label>
    <input class:valueAbility type="text" value={valueAbility} />
    {#if modifier}
        <p class="modifier">({modifier})</p>
    {/if}
    {#if edit}
        <i class="fas fa-edit edit" />
    {/if}
</div>

<style>
    .contAbility {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .valueAbility {
        width: 40px;
        background-color: rgba(128, 128, 128, 0.3);
        border: none;
        padding: 5px;
        border-radius: 4px;
        font-size: 14px;
        font-weight: 500;
        margin: 0 5px;
    }
    .nameAbility,
    .modifier,
    .valueAbility {
        color: rgb(183, 183, 183);
    }
    .nameAbility {
        font-weight: 700;
    }
    .modifier {
        font-size: 12px;
    }
    @media screen and (max-width: 768px) {
        .contAbility {
            justify-content: space-around;
        }
    }
</style>

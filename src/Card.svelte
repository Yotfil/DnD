<script>
    /* own components */
    import Header from './Header.svelte';
    import Abilities from './Abilities.svelte';
    import Collapsable from './Collapsable.svelte';

    import { onMount } from 'svelte';

    export let monster = 'acolyte';
    let monsterToRender = {};

    const getMonsters = () => {
        fetch(`https://www.dnd5eapi.co${monster}`)
            .then(function (response) {
                if (response.ok) {
                    return response.json();
                }
            })
            .then((monster) => {
                monsterToRender = monster;
            });
    };

    const modifierValue = (valueAbility) => {
        let valueModifier = 0;

        if (valueAbility > 10) {
            for (let i = 10; i < valueAbility; i += 1) {
                valueModifier += 1;
            }
            return `+${Math.round(valueModifier / 2)}`;
        } else if (valueAbility < 10) {
            for (let i = 10; i > valueAbility; i -= 1) {
                valueModifier -= 1;
            }
            return `${Math.floor(valueModifier / 2)}`;
        } else {
            return (valueModifier = '0');
        }
    };
    onMount(getMonsters);
</script>

<div class="card">
    <Header monsterName={monsterToRender.name} />
    <section class="bodyCard">
        <div class="main">
            <div class="ability">
                <Abilities
                    nameAbility={'HP:'}
                    valueAbility={monsterToRender.hit_points}
                    modifier={monsterToRender.hit_dice}
                />
            </div>
            <div class="ability">
                <Abilities
                    nameAbility={'CA:'}
                    valueAbility={monsterToRender.armor_class}
                />
            </div>
        </div>
        <div class="secondary">
            <div class="ability">
                <Abilities
                    nameAbility={'Str:'}
                    valueAbility={monsterToRender.strength}
                    modifier={modifierValue(monsterToRender.strength)}
                />
            </div>
            <div class="ability">
                <Abilities
                    nameAbility={'Dex:'}
                    valueAbility={monsterToRender.dexterity}
                    modifier={modifierValue(monsterToRender.dexterity)}
                />
            </div>
            <div class="ability">
                <Abilities
                    nameAbility={'Con:'}
                    valueAbility={monsterToRender.constitution}
                    modifier={modifierValue(monsterToRender.constitution)}
                />
            </div>
            <div class="ability">
                <Abilities
                    nameAbility={'Int:'}
                    valueAbility={monsterToRender.intelligence}
                    modifier={modifierValue(monsterToRender.intelligence)}
                />
            </div>
            <div class="ability">
                <Abilities
                    nameAbility={'Wis:'}
                    valueAbility={monsterToRender.wisdom}
                    modifier={modifierValue(monsterToRender.wisdom)}
                />
            </div>
            <div class="ability">
                <Abilities
                    nameAbility={'Cha:'}
                    valueAbility={monsterToRender.charisma}
                    modifier={modifierValue(monsterToRender.charisma)}
                />
            </div>
        </div>
    </section>
    <Collapsable {...monsterToRender} title={'Info'} />
</div>

<style>
    .card {
        width: 32%;
        margin: 20px 0;
        min-height: 400px;
        background-color: rgb(34, 34, 34);
        padding-bottom: 20px;
        box-shadow: 0 3px 1px -2px rgba(0, 0, 0, 0.2),
            0 2px 2px 0 rgba(0, 0, 0, 0.14), 0 1px 5px 0 rgba(0, 0, 0, 0.12);
    }
    .main {
        display: flex;
        justify-content: space-around;
        align-items: center;
        margin: 10px 0;
        padding: 20px;
    }
    .secondary {
        padding: 20px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;
    }
    .secondary .ability {
        width: 30%;
    }
    @media screen and (max-width: 1024px) {
        .secondary .ability {
            width: 48%;
        }
    }
    @media screen and (max-width: 768px) {
        .card {
            width: 45%;
        }
        .main {
            flex-wrap: wrap;
        }
        .main .ability,
        .secondary .ability {
            width: 90%;
        }
    }
    @media screen and (max-width: 550px) {
        .card {
            width: 90%;
        }
    }
</style>

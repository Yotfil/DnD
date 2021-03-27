<script>
    import { Link } from 'svelte-routing';
</script>

<nav class="container">
    <ul class="menu">
        <li class="itemMenu">
            <Link class="linkMenu" to="/">Todos</Link>
        </li>
        <li class="itemMenu">
            <Link class="linkMenu" to="/dashboard">Tablero</Link>
        </li>
    </ul>
</nav>

<style>
    .container {
        width: 50%;
        margin: auto;
        margin-bottom: 50px;
    }
    .menu {
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        width: 100%;
    }
    :global(a) {
        color: rgb(183, 183, 183);
        background-color: rgba(0, 0, 0, 0.1);
        padding: 5px 15px;
        border-radius: 4px;
    }
    :global(a):hover {
        box-shadow: 0 3px 1px -2px rgba(0, 0, 0, 0.2),
            0 2px 2px 0 rgba(0, 0, 0, 0.14), 0 1px 5px 0 rgba(0, 0, 0, 0.12);
    }
</style>

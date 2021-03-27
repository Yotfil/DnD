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
    }
    .menu {
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>

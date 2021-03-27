<script>
    import { Router, Route, Link } from 'svelte-routing';
    import Home from './Home.svelte';
    import Dashboard from './Dashboard.svelte';
    import Menu from './Menu.svelte';

    export let url = '';
</script>

<Router {url}>
    <div class="header">
        <h1 class="imgTitle">
            <figure>
                <img src="img/logoDnD.png" alt="Logo of Dungeond and Dragons" />
                <figcaption>Monster Guide</figcaption>
            </figure>
        </h1>
        <Menu />
    </div>
    <Route path="/">
        <Home />
    </Route>
    <Route path="/dashboard">
        <Dashboard />
    </Route>
</Router>

<style>
    .imgTitle {
        width: 50%;
        margin: auto;
        text-align: center;
        border-radius: 10px;
    }
    .imgTitle img {
        width: 100%;
        margin-bottom: -25px;
    }
    .imgTitle figcaption {
        line-height: 1;
        margin-bottom: 100px;
        color: #e3e3e3;
        font-weight: 300;
    }
</style>

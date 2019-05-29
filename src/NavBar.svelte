<script>
	let isActive = false;
	$:toggle = () => (isActive=!isActive);
</script>

<nav class="navbar is-black">
    <div class="navbar-brand">
        <a href="/" class="navbar-item has-text-white">
            Svelte Todo App
        </a>
        <span role="button" class="navbar-burger {(isActive?'is-active':'')}" aria-label="menu" aria-expanded="false" on:click={toggle}>
            <span aria-hidden="true"></span>
            <span aria-hidden="true"></span>
            <span aria-hidden="true"></span>
        </span>
    </div>
    <div class="navbar-menu {(isActive?'is-active':'')}">
        <a href="/" class="navbar-item is-tab">Home</a>
        <a href="/" class="navbar-item is-tab">About</a>
        <a href="/" class="navbar-item is-tab">Contect</a>
        <a href="//github.com/imsamtar" target="_blank" class="navbar-item is-tab">Github</a>
        <a href="//twitter.com/imsamtar" target="_blank" class="navbar-item is-tab">Twitter</a>
    </div>
</nav>
<nav>
    <div class="nav-container"></div>
    <a href="/" class="nav-logo" title="Go to Homepage">Егор</a>
    {#each nav as link}
        {#if link.isShow}
            <a href="{link.href}" class="link">{link.title}</a>
        {/if}
    {/each}
</nav>
<div class="container">
    <slot></slot>
</div>

<script>
    const nav = [
        {title: "Обо мне", href: "/about", isShow: true},
        {title: "Блог", href: "/blog", isShow: true},
        {title: "Мои проекты", href: "/projects", isShow: true},
        {title: "Контакты", href: "/contacts", isShow: true},
        {title: "temp", href: "/temp", isShow: true},
    ];
</script>

<style>
    .container {
        max-width: 1400px;
        margin: 50px auto;
    }
</style>
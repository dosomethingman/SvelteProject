<nav>
    <div class="nav-container"></div>
    <a href="/" class="nav-logo" title="Go to Homepage">Egor</a>
    <div class="nav-links">
        <a href="/about" class="link">About me</a>
        <a href="/blog" class="link">Blog</a>
        <a href="/projects" class="link">My projects</a>
        <a href="/contacts" class="link">My contacts</a>
    </div>
</nav>
<div class="container">
    <slot></slot>
</div>

<style>
    .container {
        max-width: 1400px;
        margin: 50px auto;
    }
</style>
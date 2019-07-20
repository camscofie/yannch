---
layout: home
---

<div class="index-content blogs">
    <div class="section">
        <ul class="artical-cate">
            <li class="on"><a href="/"><span>Blogs</span></a></li>
            <li style="text-align:center"><a href="/DV"><span>Déjà Vu</span></a></li>
            <li style="text-align:right"><a href="/DR"><span>Gists</span></a></li>
        </ul>

        <div class="cate-bar"><span id="cateBar"></span></div>

        <ul class="artical-list">
        {% for post in site.categories.blogs %}
            <li>
                <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
                <div class="title-desc">{{ post.description }}</div>
            </li>
        {% endfor %}
        </ul>
    </div>
    <div class="aside">
    </div>
</div>

---
layout: home
---

<div class="index-content project">
    <div class="section">
        <ul class="artical-cate">
            
            <li style="text-align:center"><a href="/wedding"><span>简历</span></a></li>
            
        </ul>

        <div class="cate-bar"><span id="cateBar"></span></div>

        <ul class="artical-list">
        {% for post in site.categories.resume %}
            <li>
                <h2>
                    <a href="{{ post.url }}">{{ post.title }}</a>
                </h2>
                <div class="title-desc">{{ post.description }}</div>
            </li>
        {% endfor %}
        </ul>
    </div>
    <div class="aside">
    </div>
</div>

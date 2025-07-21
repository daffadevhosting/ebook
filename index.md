---
layout: default
title: Daftar Bab
capture: Arsip Cerita L Y Я A
pagination:
  enabled: true
  per_page: 4
  collection: bab
---

<section id="bab-list" class="grid grid-cols-1 sm:grid-cols-2 gap-6 md:py-10">
  {% if paginator.posts %}
    {% for bab in paginator.posts %}
      <a href="{{ bab.url | relative_url }}" class="group border border-zinc-800 p-5 rounded-md hover:bg-zinc-900 transition-all duration-300 relative overflow-hidden flex flex-col justify-between min-h-[200px]">
        <h2 class="text-cyan-400 text-lg font-semibold group-hover:underline">
          {{ bab.title }}
        </h2>
        <p class="text-sm text-zinc-500 mt-1">
          {% if bab.date %}
            {{ bab.date | date: "%d %b %Y" }}
          {% endif %}
        </p>
        <p class="mt-3 text-zinc-400 line-clamp-3">{{ bab.excerpt | strip_html }}</p>

        <!-- Decorative background glimmer -->
        <div class="absolute -top-10 -right-10 w-32 h-32 bg-cyan-500/10 rounded-full blur-xl group-hover:scale-125 transition duration-500"></div>
      </a>
    {% endfor %}
  {% else %}
    <p class="text-zinc-400">Belum ada bab yang dipublikasikan.</p>
  {% endif %}
</section>

<nav class="py-8 flex justify-between text-sm text-zinc-400">
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path | relative_url }}" class="hover:text-cyan-400">
      <i class="fa-solid fa-arrow-left mr-2"></i>Sebelumnya
    </a>
  {% else %}
    <span></span>
  {% endif %}

  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path | relative_url }}" class="hover:text-cyan-400">
      Berikutnya<i class="fa-solid fa-arrow-right ml-2"></i>
    </a>
  {% else %}
    <span></span>
  {% endif %}
</nav>

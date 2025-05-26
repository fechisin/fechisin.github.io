---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

<style>
  .tag-remove {
    margin-left: 8px;
    cursor: pointer;
    font-weight: bold;
    display: none;
  }

  .tag:hover .tag-remove {
    display: inline; 
  }

  .active-filters-label {
    font-size: 1rem;
    color: #494e52; 
    font-weight: 600;
    margin-right: 8px;
    margin-bottom: -50px;
    /* You can add more styles here */
  }
</style>

<div id="selected-tags" style="font-size: 1.5rem; margin: 20px 0; color: darkblue;">
</div>

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}

<!-- Old script that works: -->
<!-- <script>
  document.addEventListener('DOMContentLoaded', function () {
    const tagElements = document.querySelectorAll('.tag');
    const selectedTagsContainer = document.getElementById('selected-tags');

    const selectedTags = new Set();

    function slugify(text) {
      return text
        .toString()
        .toLowerCase()
        .replace(/\s+/g, '-')           // Replace spaces with -
        .replace(/[^\w\-]+/g, '')       // Remove all non-word chars
        .replace(/\-\-+/g, '-')         // Replace multiple - with single -
        .replace(/^-+/, '')             // Trim - from start of text
        .replace(/-+$/, '');            // Trim - from end of text
    }

    function renderSelectedTags() {
      selectedTagsContainer.innerHTML = '';

      selectedTags.forEach(tagText => {
        const span = document.createElement('span');
        const slug = slugify(tagText);
        span.className = `tag tag-${slug}`;
        span.textContent = tagText;

        const removeSpan = document.createElement('span');
        removeSpan.className = 'tag-remove';
        removeSpan.textContent = '×';
        removeSpan.title = 'Remove tag';

        removeSpan.addEventListener('click', (e) => {
          e.stopPropagation(); // prevent triggering the main tag click
          selectedTags.delete(tagText);
          renderSelectedTags();
        });

        span.appendChild(removeSpan);
        selectedTagsContainer.appendChild(span);
      });
    }

    tagElements.forEach(tagEl => {
      tagEl.style.cursor = 'pointer';
      tagEl.addEventListener('click', () => {
        const tagText = tagEl.textContent;
        if (!selectedTags.has(tagText)) {
          selectedTags.add(tagText);
          renderSelectedTags();
          window.scrollTo({ top: 0, behavior: 'smooth' });
        }
      });
    });
  });
</script> -->
<script>
document.addEventListener('DOMContentLoaded', () => {
  const postTagEls = document.querySelectorAll('.archive__item-tags .tag');
  const selectedTagsContainer = document.getElementById('selected-tags');
  const postItems = document.querySelectorAll('.publication-item');

  const selectedTags = new Set();

  function slugify(text) {
    return text.toString().toLowerCase()
      .replace(/\s+/g, '-')
      .replace(/[^\w\-]+/g, '')
      .replace(/\-\-+/g, '-')
      .replace(/^-+/, '')
      .replace(/-+$/, '');
  }

  function renderSelectedTags() {
    selectedTagsContainer.innerHTML = '';
    if (selectedTags.size === 0) {
      selectedTagsContainer.textContent = ''; 
      return;
    }

    const label = document.createElement('span');
      label.textContent = 'Active filters: ';
      label.className = 'active-filters-label';  
      selectedTagsContainer.appendChild(label);

    selectedTags.forEach(tagText => {
      const span = document.createElement('span');
      const slug = slugify(tagText);
      span.className = `tag tag-${slug}`;
      span.textContent = tagText;

      const removeBtn = document.createElement('span');
      removeBtn.className = 'tag-remove';
      removeBtn.textContent = '×';
      removeBtn.title = 'Remove tag';
      removeBtn.addEventListener('click', e => {
        e.stopPropagation();
        selectedTags.delete(tagText);
        updateUI();
      });

      span.appendChild(removeBtn);
      selectedTagsContainer.appendChild(span);
    });
  }

  function filterPosts() {
    postItems.forEach(item => {
      const itemTags = (item.dataset.tags || '').split(',').map(t => t.trim());
      const show = selectedTags.size === 0
        || [...selectedTags].every(tag => itemTags.includes(tag));
      item.style.display = show ? '' : 'none';
    });
  }

  function updateUI() {
    renderSelectedTags();
    filterPosts();
  }

  postTagEls.forEach(el => {
    el.style.cursor = 'pointer';
    el.addEventListener('click', () => {
      const tagText = el.textContent.trim();
      if (!selectedTags.has(tagText)) {
        selectedTags.add(tagText);
        updateUI();
        window.scrollTo({ top: 0, behavior: 'smooth' });
      }
    });
  });
});
</script>

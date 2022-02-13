---
layout: archive
title: "Research"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}

<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">

<div class="container">
  <div class="row">
    <div class="col-md-4 col-sm-6 col-xl-4 my-3">
      <div class="card d-block h-100 box-shadow-hover pointer">
        <div class="pt-3 h-75p align-items-center d-flex justify-content-center">
          <img class="img-fluid w-xs-120p" src="https://raw.githubusercontent.com/solodev/boxes-with-distinct-hover-effect/master/images/valkyrie.png" alt="valkyrie ship image">
        </div>
        <div class="card-body p-4">
          <h3 class="h4"><strong>Valkyrie-1</strong></h3>
          <p>As the lean, mean “muscle” of the LunarXP fleet, the Valkyrie-1 series makes safe transportation from surface to orbit a reality.</p>
        </div>
      </div>
    </div>

    <div class="col-md-4 col-sm-6 col-xl-4 my-3">
      <div class="card d-block h-100 box-shadow-hover pointer">
        <div class="pt-3 h-75p align-items-center d-flex justify-content-center">
          <img class="img-fluid w-xs-120p" src="https://raw.githubusercontent.com/solodev/boxes-with-distinct-hover-effect/master/images/talon.png" alt="talon ship image">
        </div>

        <div class="card-body p-4">
          <h3 class="h4"><strong>Talon-2</strong></h3>
          <p>The Talon-2 series is the primary vehicle for crossing the colony and delivering both personnel and goods to habitats – from agriculture to engineering equipment.</p>
        </div>
      </div>
    </div>

    <div class="col-md-4 col-sm-6 col-xl-4 my-3">
      <div class="card d-block h-100 box-shadow-hover pointer">
        <div class="pt-3 h-75p align-items-center d-flex justify-content-center">
          <img class="img-fluid w-xs-120p" src="https://raw.githubusercontent.com/solodev/boxes-with-distinct-hover-effect/master/images/lunar-xplorer.png" alt="ship image">
        </div>
        <div class="card-body p-4">
          <h3 class="h4"><strong>Lunar XPlorer</strong></h3>
          <p>Often referred to as a “container ship in space,” the Lunar XPlorer is the flagship of the LunarXP fleet and the primary mode of transportation for people, equipment, and supplies to the moon.</p>
        </div>
      </div>
    </div>

  </div>
</div>

---
layout: page
title: "Team"
description: "Collaborators working on this project."
---
<html>
<head>
  <style>
    h2  {
		color: rgb(30,144,255);
		display: inline; 
		font-weight: bold;
		}
	.center {
	  display: block;
	  margin-left: auto;
	  margin-right: auto;
	  width: 85%;
		}
  </style>
</head>


<body>
{% for member in site.data.members %} 
	<br>
	<p>
	{% if member.visible == true %}
		<img src="{{ member.img }}" style="margin-top:0px; margin-bottom:5px; margin-right:10px; float:left; width:125px !important">
		
		<h2>{{ member.name }}</h2>
		
		<h3>{{ member.role }}</h3>
		
<!--		{% if member.github %} 
			<span class="social-share-googleplus"><a href="https://github.com/{{ member.github }}" title="Github"><img src="{{ "/assets/img/icons/github-icon.png" | prepend: site.baseurl }}" style="height:20px">Github</a></span> 
		{% endif %}
-->		
		{% if member.url %}
			<span><a href="{{ member.url }}" title="Website"><img src="{{ "/assets/img/icons/url-icon.png"| prepend: site.baseurl }}" style="height:20px">Website</a></span>
			<br>
		{% endif %}

		{% if member.bio %} 
			{{ member.bio }}
			<br>
		{% endif %}	
		
		{% if member.project_link %}
			<span><a href="{{ member.project_link | prepend: site.baseurl }}" title="Project">Link to project description.</a></span>
		{% endif %}
		<br>
	{% endif %}
	<br>
	<hr>
	</p>
{% endfor %}
</body>
</html>
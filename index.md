---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
#header-img: "logo.png"
inverse-img: true
---
<html>

<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
h3		{color: rgb(30,144,255);display: inline; font-weight: bold;}
</style>
</head>

<body>
	<div class="MainBody">
		<h1 class="page-title">What is DARTS?</h1>
		<div class="Philosophy" style="padding-left: 15px;">
			<p text-align="justify">
			<h3>Delft:</h3> we belong to the Civil Engineering and Geoscience (CEG) Department at the Civil Engineering Faculty of TU Delft. The development team directly linked to the new GeoEnergy program which connects Geology, Geophysics and Petroleum Engineering sections of the department.
			<p text-align="justify">
			<h3>Advanced:</h3> the simulation framework is based on the recently proposed Operator-Based Linearization (OBL) approach, which helps to decouple the complex nonlinear physics and advanced unstructured discretization from the core simulation engine. The framework is targeting the solution of forward and inverse problems.
			</p>
			<p text-align="justify">
			<h3>Research:</h3> the development team includes five PhD students from the CEG department and multiple MSc students working on their thesis project on DARTS platform. The simulation platform is developed within <a href = "https://www.tudelft.nl/en/ceg/about-faculty/departments/geoscience-engineering/sections/reservoir-engineering/research/darsim/" target="_blank"><b> Delft Advanced Reservoir Simulation (DARSim)</b></a> program and linked to multiple research in the area of reservoir simulation, inverse modeling and uncertainty quantification.    
			</p>
			<p text-align="justify">
			<h3>Terra:</h3> the developed framework is utilized for forward and inverse problems in petroleum engineering, low- and high-enthalpy geothermal applications, subsurface storage and subsurface integrity. The primary focus and developed capabilities are currently cover low-enthalpy geothermal operations which include multicomponent multiphase flow of mass and heat with complex chemical interactions. Another focus is on thermal-compositional processes for Enhanced Oil Recovery.  
			</p>
			<p text-align="justify">
			<h3>Simulator:</h3> the main simulation kernel implemented on multi-core CPU and many-core GPU architectures. Advance multiscale nonlinear formulation improves the performance of forward and inverse models. Additional afford invested in representative proxy models for complex subsurface processes including multiphase multicomponent flow.			
			</p>
<!--		</div>
	</div> -->
	<div class="BlogPosts">
		<h1 class="page-title">DARTS posts</h1>
		{% for post in site.posts %}
		<div class="post-preview" style="padding-left: 15px;">
			<a href="{{ post.url | prepend: site.baseurl }}">
				<h2 class="page-title">            {{ post.title }}
				</h2>
				{% if post.subtitle %}
				<h3 class="page-subtitle">
					{{ post.subtitle }}
				</h3>
				{% endif %}
			</a>
			<p class="post-meta" style="margin-bottom:5px">Posted by {{ post.author }} on {{ post.date | date: "%B %-d, %Y" }}</p>
			<div class="notepad-index-post-tags" style="">
				{% for tag in post.tags %}<a>{{ tag | capitalize }}</a>{% unless forloop.last %}&nbsp;{% endunless %}{% endfor %}
			</div>
		</div>
		<hr>
		{% endfor %}
	</div>
	&emsp;

<p> <h4> If you want to use DARTS for your research project, please contact <a href = "mailto:D.V.Voskov@tudelft.nl">Denis Voskov</a>. </h4> </p>


<!--</body>
</html> 
Some general links: <br>
[TU Delft website][TUD] <br>

[TUD]: https://www.tudelft.nl
[link_to_repo]: https://github.com/darts-web/darts-web
-->
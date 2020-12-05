---
layout: page
title: Details
#permalink: /details/
#header-img: /assets/img/Cogs-banner-01.png
inverse-img: true
---
<html>

<head>
  <style>
    h4		{color: rgb(30,144,255);display: inline; font-weight: bold;}
  </style>
</head>

<body>
<div class="TechDetails" style="padding-left: 15px;">
	<p><h4>Core simulation capabilities: </h4> 
	unstructured Two-Point Flux Approximation, Open MP and GPU shared memory parallel, Constraint Pressure Residual linear preconditioner, Multi-Segmented Wells and surface facilities.</p>

	<p><h4>Core physics: </h4>
	multiphase thermal-compositional, extended black-oil, general multiphase, chemical precipitation and dissolution, basic foam capabilities.</p>

	<p><h4>Structure: </h4>
	Python-based pre-processing of space, time and physics discretization with C++ and CUDA core simulation capabilities:</p>
	
	<ul>
	  <li><h4>DARTS-engine</h4>: kernel for nonlinear solution of governing equations (C++ and CUDA);</li>
	  <li><h4>DARTS-physics</h4>: main physical kernels for industrial applications (C++ and Python);</li>
	  <li><h4>DARTS-models</h4>: Python-based capabilities for model running and pre/postprocessing;</li>
	  <li><h4>DARTS-opt</h4>: optimization and data assimilation Python-based software framework.</li>
	</ul>
</div>

<h2>Current focus-applications:</h2>
<div class="CurrFocus" style="padding-left: 15px;">
	<p><h4>Forward simulation: </h4>detailed well and near-well modeling with chemical reactions;</p>
	<p><h4>Data assimilation: </h4>geothermal projects, data-driven proxy models;</p>
	<p><h4>Optimization: </h4>geothermal projects, CO2 Enhanced Oil Recovery;</p>
	<p><h4>Inversion: </h4>foam modeling, fractures with dissolution, gas-hydrates modeling.</p>
</div>
</body>
</html>

Some general links: <br>
[TU Delft website][TUD] <br>

[TUD]: https://www.tudelft.nl
[link_to_repo]: https://github.darts-web.io/darts-web

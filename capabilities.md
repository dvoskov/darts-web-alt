---
layout: page
title: Capabilities
permalink: /capabilities/
author: Denis Voskov
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

<meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>jQuery UI Accordion - Default functionality</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css">
  <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
  <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
  <script>
  $( function() {
    $( "#accordion" ).accordion();
  } );
  
  </script>
</head>
<body>
 

 
<div id="accordion">
  <h3>Structure of simulation framework</h3>
  <div>
 	<p text-align="justify"> 
	The key element of DARTS is operator-based linearization (OBL)<sup>1</sup>. The state-based terms of governing equations are parametrized in the physical space of the problem forming dynamically expanding lookup tables where the supporting points for reconstruction of operators are saved in a special two-level sparse storage designed for efficient lookup and re-use. These tables are used in linearization to approximate operators along with derivatives with respect to governing unknowns using piecewise multilinear interpolation in physical space. It allows to detach fluid and rock properties calculations (now only performed at supporting points) from the main nonlinear loop and to relax the performance requirements for such calculations. </p>
	
	<p> <img src="{{ site.baseurl }}/assets/img/project_photos/cap/DARTS_struct.gif" width="70%" class="center">
	<h5><em>Fig.1: Structure of two main DARTS packages: DARTS-engines and DARTS-physics.</em> </h5></p>


	<p> The modular structure of DARTS is demonstrated in Fig.1. On the left, four main components (available physical terms) defining simulation engine are shown. On the right, main five models involved in physical package are listed. Depending on the simulation type, different combination of physical terms in governing partial differential equations and corresponding operators supported by physical package may be required. For example, in geothermal applications, accumulation, convective flux and diffusive (conductive) temperature are required for conservation equations for mass and energy. </p>
	
	<p> Two types of interpolators connect engine and physics. Static iterator pre-computes all supporting points in advance being useful for coarse physical representation and low-dimensional parameter space. Adaptive iterator computes only actually required supporting points along the simulation<sup>2</sup>. When an engine requires values and derivatives of operators for Jacobian and RHS assembly, the interpolator computes them based on the multi-linear interpolation among existing supporting points. Only when some of the required supporting points are missing, the interpolator requests them from physics module. In this case, operator values computed during simulation can be stored and loaded, which can be extremely beneficial in case of running multiple models with the same physical properties (e.g. in optimization process). </p>

  </div>
  
  <h3>Implementations on GPU</h3>
  <div class="accordion-group">

  
	<p text-align="justify">Various novel computing architectures, like massively parallel and multi-core, as well as computing accelerators, like GPUs or TPUs, continue to emerge regularly. In order to harvest the performance benefits of these architectures to the full extent and speed up the simulation, the source code has to be inevitably rewritten, sometimes almost completely. The biggest challenge here in terms of complexity, variety and size is linearization procedure since it depends on the governing equations, choice of primary unknowns, physical/chemical phenomena taken into account, and other factors. Here we present a version of DARTS fully offloaded to GPU device with efficient linear and nonlinear solvers. </p>
	
	<p text-align="justify"> Previously implemented linearization procedure at GPU device<sup>3</sup> was recently complimented with advanced linear solver. At the moment, DARTS is capable of performing the solution of the linear systems arising from any existing physical engine entirely on GPU. Using publicly available cuBLAS, cuSPARSE and AMGX libraries, complemented by our own developed two-stage CPR reduction preconditioner, the linear solver is capable to run 10x-15x faster than on a CPU for large enough models. Fig.2 shows the perfromance of simulation on full SPE10 model with the original dead-oil physics (~2.2M unknowns) and compositional physics representing supercritical CO2 injection for Enchanced Oil Recovery (~4.4M unknowns). </p>
	<br>

	<p>
	<img src="{{ site.baseurl }}/assets/img/project_photos/cap/GPUvsCPU.png" width="75%" class="center">
	<h5><em> Fig.2: DARTS simulations on CPU and GPU (in log scale) for the SPE10 reservoir with original dead-oil (2 equations per block) and compositional (4 equations per block) physical kernels.</em></h5> </p>
	
	<p> These results were obstained on Intel(R) Core(TM) i7-8086K (4.2 GHz) processor with NVidia GeForce RTX 2080 Ti card. Notice that this performance achieved with a gaming-class GPU card (~€1000 worth) which is pluggable to a regular desktop. Using such a card, the total time required for the solution of the full SPE10 comparative problem becomes less than 3 minutes. With this extension, DARTS provides the flexible, modular, computationally efficient modeling package for various applications, including hydrocarbon<sup>2</sup> and geothermal<sup>4</sup> energy production. </p>
  </div>  
  
  <h3>Adaptive Mesh Refinement</h3>
  <div>
  <p>  
  A coupled description of flow and thermal-reactive transport is spanning a wide range of scales in space and time, which often introduces a significant complexity for the modelling of such processes. Subsurface reservoir heterogeneity with complex multi-scale features increases the modelling complexity even further. Traditional Algebraic Multiscale techniques are usually focused on the accuracy of the pressure solution and often ignore the transport. Improving the transport solution can however be quite significant for the performance of the simulation, especially in complex applications related to thermal-compositional flow. The use of an Adaptive Mesh Refinement (AMR) enables the grid to adapt dynamically during the simulation, which facilitates the efficient use of computational resources. This is especially important in applications with reactive flow and transport where the region requires high-resolution calculations as often localized in space. </p>
  
  <p>In this work, the aim is to develop an AMR framework for fully-implict general-purpose reservoir simulation. The approach uses a multi-level connection list and can be applied to fully unstructured grids<sup>5</sup>. The adaptivity of the grid in the developed framework is based on a hierarchical approach. First, the fine-scale model is constructed, which accurately approximates all reservoir heterogeneity. Next, a global flow-based upscaling is applied, where an unstructured partitioning of the original grid is created. An example of two hierarchy levels for unstructured grid is shown in Fig.3. Once the full hierarchy of levels is constructed, the simulation is started at the coarsest grid. Grid space refinement criteria can be developed specifically for a particular application of interest. The multi-level connectivity lists are redefined at each timestep and used as an input for the next.

		<img src="{{ site.baseurl }}/assets/img/project_photos/cap/AMR.gif" width="100%" class="left">
		<h5><em>Fig.3: Two-level hierarchy for AMR on unstructured grid and corresponding solution at fine, AMR and coarse scales with dynamic adaptivity of levels. </em></h5></p>
  
    <p>The developed Adaptive Mesh Refinement framework was implemented in DARTS<sup>6</sup>. The performance of the proposed approach is illustrated for geothermal applications shown in Fig.3. Here adaptive coarsening can accurately reproduce the fine scale solution using 40% less degrees of freedom which expected to bring a proportional improvement in simulation time due to the reduction in the size of the linear system. </p>

  </div>

  <h3>Multi-segment wells</h3>
  <div>
	
  <p>
  Accurate well and near well modelling becomes essential in the reservoir simulation. Recently, advanced (smart) well operations and technologies are employed in the subsurface industry such as long deviated, horizontal and multi-lateral wells. In order to use such technologies intelligently, there must be a robust, supportable model that capture efficiently physics and the expected production scenario. We design a numerical framework for predictive simulation and monitoring of hydrocarbon and geothermal wells based on the general Multi-Segment well (MS-well) model<sup>7</sup> which is able to describe the well topology and accurately represent the thermal multiphase multicomponent flow and transport behavior in the wellbore. </p>
  
  <p> <img src="/assets/img/project_photos/cap/jac_struct_mswell3d.png" width="100%" class="left" />
  <h5><em> Fig.4: Jacobian matrix for a small 3D structured reservoir and Multi-Segmented well with blocks corresponding to conservation and momentum equations in reservoir and well segments.</em> </h5></p>
  
  <p text-align="justify"> Our simulation model is based on the the general unstructured grid framework following the general decoupled velocity formulation. We segment any wells into nodes and connections similar to finite-volume discretization of reservoir flow. Total velocity serves as additional nonlinear unknown and constrained with the momentum equation. The resulting Jacobian structure contains two parts corresponding to conservation and momentum equations as shown in Fig.4. Decoupled velocity formulation based on general unstructured mesh allows us to model complex geometry and take into account arbitrary flow direction, whereby the flow direction is determined dynamically during the nonlinear iterations. Moreover, transforming both reservoir and well nonlinear governing equations into operator form benefits from OBL techniques and reduce further the computational cost related to linearization. Our MS-well model is fully coupled with various physics incorporated in DARTS including chemical reactions with precipitation and dissolution of solid (mineral) phases.</p>
  
  </div>

<!--  <h3>Advanced nonlinear solvers</h3>
  <div>
  <p> Simulation of multiphase multicomponent flow and transport in reservoirs with complex heterogeneous structure requires adopting stable numerical methods that rely on an implicit treatment of the flux term in conservation equations. The discrete approximation of convection term is usually highly nonlinear due to the complex properties complemented with a multiphase flash solution. Consequently, robust and efficient techniques are needed to solve the governing non-linear system of equations. The solution of the transport problem often requires the propagation of the displacement front to multiple control volumes at each time step. Coping with this issue is particularly challenging in the presence of highly heterogeneous systems such as fractured reservoirs. One example of such solution is shown in Fig.5.

  <img src="/assets/img/project_photos/cap/DFM_testmodelD.gif" width="60%" class="left" />
  <h5><em> Fig.5 Saturation propagation in naturally fractured reservoir.</em> </h5></p>
  
  <p> We present a robust nonlinear solver based on a generalization of the trust-region  technique  to compositional  multiphase  flows<sup>8</sup>. The approach is designed to embed a newly introduced Operator-Based Linearization approach and is grounded on the analysis of multi-dimensional tables related to parameterized convection operators in governing equations. The delineation of this trust regions is dictated by the inflection points in parameter space which is determined based on the analysis of the Hessian matrix of the convex operators. However, computation of full hessian matrix is expensive. Therefore, we approximate these trust regions in the solution process by detecting the boundary of convex regions via analysis of the directional derivative. This analysis is performed adaptively while tracking the nonlinear update trajectory in the parameter-space. The proposed nonlinear solver locally constraints the updating of the overall compositions across the boundaries of these regions.</p>

  
  </div>
-->

  <h3>Advanced processing of fractured networks</h3>
  <div>
  
  <p>Current Discrete Fracture Model (DFM) implementation in DARTS relies on a Two-Point Flux Approximation (TPFA) scheme where fractures are represented explicitly in the numerical model <sup>5</sup>. However, explicit representation of the fractures contains complex fracture intersection which in turn might pose meshing difficulties. The resulting mesh, therefore, can contain abundant artefacts which negatively impact the performance of the reservoir simulator. Performance issues mainly manifest as numerical inaccuracies due to non-orthogonality of the control-volume intersections. Secondly, it also manifests in terms of convergence problems due to the extremely large contrast between control volumes sizes as shown in Fig.5 for the realistic outcrop data. All these problems are solved by using a pre-processing method<sup>6</sup> in which we sequentially process each fracture, using the desired meshing accuracy (predefined size of the fracture segment). 
  
		<img src="{{ site.baseurl }}/assets/img/project_photos/appl/outcrop.png" width="80%" class="left">

		<h5><em>Fig.5: Original version of Brejoes outcrop characterization (a) and processed version (b) with corresponding statistics of control volume sizes for both of them (c). </em></h5></p>
	

	<p>The sequential algorithm adds each fracture line split on segments and resolves all conflicts when segments are close to each other by merging them. The computational time of the pre-processing step is insignificant to simulation time while still greatly improving the simulation results (both accuracy and performance). The result of such pre-processing is shown in Fig.5,b. With this approach, it is possible to construct a discrete fracture network at any desired resolution while maintaining the main characteristics of the original fracture characterization.
        As can be observed in the Fig.6 for a realistic outcrop data<sup>7</sup>, minimal information on the fracture network is lost in the processing at a coarser level while the number of degrees of freedom in the model is reduced by several orders of magnitude. </p>
		<p>  
		<img src="{{ site.baseurl }}/assets/img/project_photos/appl/ensemble.png" width="90%" class="left">
		<h5><em>Fig.6: Processing of realistic outcrop at different meshing resolution with corresponding degrees of freedom. </em></h5>	
	</p>
  </div>


  <h3>Adjoint gradients with OBL</h3>
  <div>
  
		<p> This study focuses on adjoint-based gradient optimization<sup>9</sup> using operator-based linearization (OBL) method. The objective function is augmented
		by being linearly combined with reservoir state equations. This objective function shares the same extrema with the original objective function as the residual of reservoir state equation is equal to zero. In the course of calculating the gradient of objective function, several derivatives with respect to state variables and control variables at each time step are provided by OBL technique. OBL method largely reduces the amount of property-related computations by interpolating the state-based terms of governing equations and their derivatives with respect to governing unknowns in physical space. </p>
		
		<p>
		As an example, a history matching problem of gas injection problem<sup>10</sup> using adjoint gradient with OBL is investigated. The proposed method helps to efficiently calculated the gradient of objective function, especially for the case with large amounts of elements in control variables and for many components. For a visualization purposes, we investigate 1D reservoir with only two permebaility values <i>u<sub>1</sub></i> and <i>u<sub>2</sub></i> in the vector of control variables. The surface plots of objective function values are shown in the Fig.7. </p>

		<p>
		<img src="{{ site.baseurl }}/assets/img/project_photos/cap/image001.jpg" width="45%" class="left">
		<img src="{{ site.baseurl }}/assets/img/project_photos/cap/image002.jpg" width="45%" class="right">

		<h5><em>Fig.7: The plots of objective function values in 3D (left) and 2D projection (right).</em></h5></p>

		<p> As it can be seen in the above figures, there is a clear band area which corresonds to the global minumum the objective function. Besides, there is also a bunch of local extrenums near the global minimum. In the Fig.8 we show the solution trajectories based on numerical and adjoint gradients. Both methods behave almost identical and require most of the computational efforts in this band area with many local extrenums before finding the global optimum.</p>
		
		<p>
		<img src="{{ site.baseurl }}/assets/img/project_photos/cap/0.06-0.08-v1.gif" width="90%" class="left">
		<h5><em>Fig.8: Optimization trajectories with black and orange lines corresponds to numerical and adjoint-based gradients respectively (left) and objective function reduction with iterations (right). </em></h5></p>

  </div>

  <h3>Fully-coupled geomechanics</h3>
  <div>
	<p>
	Seismic activity caused by field development has become a reason for public concern in the Netherlands, Germany and United States that resulted in cut or even stop of  energy production projects. The nature of such events is a stick-slip frictional instability of pre-existed fractures and faults. Field development causes the redistribution of stresses over the reservoir and surrounding formations which may trigger seismic rupture at critically stressed discontinuities.</p>
	<p>
	We are developing the approach based on the poromechanical simulation that incorporates contact mechanics for fractures. Finite Volume Method with multi-point discretization is used for both mass and momentum balance equations<sup>11</sup> . Such approach allows to obtain solution using collocated grid and subsequently to use effective preconditioning strategies for linear system. Discrete Fracture Model is employed to accurately resolve prescribed fractures in unstructured grid. Fully implicit coupling is used to obtain unconditionally stable solution and to create the basis for the investigation of applicability and performance of sequential coupling techniques for this particular problem. Incorporated nonlinearities resulted from inelastic response of the rock, fault weakening or multiphase multicomponent flow is handled using OBL approach. </p>
	<p>
	The main goal of the project is to use this modelling framework to perform simulation of ongoing experimental investigations of soil compaction and frictional response at core-scale. Model adaptation on experimental results will allow to estimate the contribution of different factors causing fault reactivation and to approach to the upscaling of constitutive laws for field-scale predictive modelling of induced seismicity. An example of mechanical displacement for a simple problem when material is pushed from left boundary at different types of unstructured meshes is shown in Fig.9. Fixed top and bottom boundaries cause high shear stresses near left corners and vertical expansion deeper in the body. </p>

		<p>
		<img src="{{ site.baseurl }}/assets/img/project_photos/cap/stresses.gif" width="120%" class="left"> </p>
		
		<p>
		<h5><em>Fig.9: Numerical solution of mechanical problem at three different types of finite volume mesh. </em></h5></p>

  </div>

</div>

<br>


<h1><a id="References">References: </a></h1>
<h5>
	<ol>
	

	
	  <li> Voskov, D.V, 2017. Operator-based linearization approach for modeling of multiphase multi-component flow in porous media, Journal of Computational Physics, 337, 275-288. 
		<a href = "https://doi.org/10.1016/j.jcp.2017.02.041" target="_blank">doi:10.1016/j.jcp.2017.02.041</a>
	  </li>
	  <li> Khait, M., D. Voskov, 2018. Adaptive parameterization for solving of thermal/compositional nonlinear flow and transport with buoyancy, SPE Journal, 23 (2), pp. 522-534. 
		<a href = "https://doi.org/10.2118/182685-PA" target="_blank">doi:10.2118/182685-PA</a>
	  </li>
	  <li> Khait, M., D. Voskov, 2017. GPU-offloaded general-purpose simulator for multiphase flow in porous media, SPE Reservoir Simulation Conference, pp. 1293-1302. 
		<a href = "https://doi.org/10.2118/182663-MS" target="_blank">doi:10.2118/182663-MS</a>
	  </li>
	  <li> Khait M., D. Voskov, 2018. Operator-based linearization for efficient modeling of geothermal processes, Geothermics, 74, 7-18. 
		<a href = "https://doi.org/10.1016/j.geothermics.2018.01.012" target="_blank">doi:10.1016/j.geothermics.2018.01.012</a>
	  </li>
<!--	  <li> Kala, K., D. Voskov, 2018. Parameterization of element balance formulation in reactive compositional flow and transport, 16th European Conference on the Mathematics of Oil Recovery, ECMOR. 
		<a href = "https://doi.org/10.3997/2214-4609.201802113" target="_blank">doi:10.3997/2214-4609.201802113</a>
	  </li>
	  -->
	  <li> Karimi-Fard, M., Durlofsky, L.J., 2016. A general gridding, discretization, and coarsening methodology for modeling flow in porous formations with discrete geological features, Advances in Water Resources, 96, pp. 354-372. 
	  <a href = "https://doi.org/10.1016/j.advwatres.2016.07.019" target="_blank">doi:10.1016/j.advwatres.2016.07.019</a>
	  </li>
	  <li> Johns, E., 2019. Applications of unstructured multi-level grid to thermal-reactive flow and transport in porous media, MSc thesis, Delft University of Technology. 
	  <a href = "http://resolver.tudelft.nl/uuid:47db1b85-3b49-4c23-a398-4f3ccb8a50bc" target="_blank">TU Delft MSc thesis repository</a>
	  </li>  	  
	  <li> Livescu, S., Durlofsky, L.J., Aziz, K., Ginestra, J.C., 2010. A fully-coupled thermal multiphase wellbore flow model for use in reservoir simulation,Journal of Petroleum Science and Engineering, 71 (3-4), pp. 138-146. 
	  <a href = "https://doi.org/10.1016/j.petrol.2009.11.022" target="_blank">doi:10.1016/j.petrol.2009.11.022</a>
	  </li>	  
	  <li> Voskov, D.V., and H.A. Tchelepi, 2011. Compositional nonlinear solver based on trust regions of the flux function along key tie-lines. Proceedings, SPE Reservoir Simulation Symposium, 2, 799-809. 
	  <a href = "https://doi.org/10.2118/141743-MS" target="_blank">doi:10.2118/141743-MS</a>
	  </li>	  
	  <li> Jansen, J.D., 2011. Adjoint-based optimisation of multiphase flow through porous media – a review. Computers and Fluids 46 (1) 40-51. 	  
	  <a href = "https://doi.org/10.1016/j.compfluid.2010.09.039  " target="_blank">doi:10.1016/j.compfluid.2010.09.039</a>
	  </li>	  
	  <li>
	  Chen, Y. and Voskov, D., 2019. Optimization of CO2 injection using multi-scale reconstruction of composition transport, Computational Geosciences.
	  <a href = "https://doi.org/10.1007/s10596-019-09841-8" target="_blank">doi:10.1007/s10596-019-09841-8</a>
	  </li>
	  <li> Terekhov, K.M., 2020. Cell-centered finite-volume method for heterogeneous anisotropic poromechanics problem, Journal of Computational and Applied Mathematics, 365, art. no. 112357. 
		<a href = "https://doi.org/10.1016/j.cam.2019.112357" target="_blank">doi:10.1016/j.cam.2019.112357</a>
	  </li>
  
	  
	</ol>
</h5>

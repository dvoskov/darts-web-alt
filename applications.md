---
layout: page
title: Applications
permalink: /applications/
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
  <h3>Geothermal benchmarking</h3>
  <div>
  
    <p> Accurate prediction of temperature and pressure distribution is essential for geothermal reservoir exploitation with cold water re-injection. Depending on our knowledge about the heterogeneous structure of the subsurface, the reservoir development scheme can be optimized and the overall lifetime of the geothermal field can be extended. In DARTS, the molar formulation with pressure and enthalpy as primary variables is selected to solve the governing system describing the geothermal model. Besides, the fully-coupled fully-implicit two-point flux approximation (TPFA) on unstructured grids is implemented to solve the mass and energy conservation equations. For the nonlinear solution, we employ the recently developed Operator-Based Linearization (OBL) approach. The solutions of DARTS is compared with the state-of-the-art simulation frameworks using a set of benchmark tests<sup>1</sup>. 
    </p>
    <p>
        <img src="{{ site.baseurl }}/assets/img/project_photos/appl/benchmark2D.jpg" width="100%" class="center" />

		<h5><em>Fig.1: 2D results comparison between DARTS and TOUGH2<sup>2</sup> for high-enthalpy test case<sup>1</sup> </em></h5> </p>
		
		<p>
		DARTS achieves a good match for both low- and high-enthalpy conditions in comparison to TOUGH2<sup>2</sup>, see Fig.1 for example. Similar accuracy DARTS demonstrated in comparison with AD-GPRS<sup>3</sup> with an example shown in Fig.2 for elongated in z-direction example of the 3D geothermal reservoir. At the same time, DARTS provides high performance and flexibility of the code due to the OBL approach, which makes it particularly useful for uncertainty quantification in processes involving complex physics.</p>
        
		<p>
       	<img src="{{ site.baseurl }}/assets/img/project_photos/appl/Geothermal_full.gif" width="90%" class="center" />
		<h5><em>Fig.2: Cold water plum propagation (a) and layer-wise error in comparison with AD-GPRS<sup>3</sup> (b). </em></h5>
        </p> 	

  </div>
  <h3>Sensitivity analysis of geothermal projects</h3>
  <div>
  
  <p> A low-enthalpy geothermal reservoir with complicated realistic sedimentary distribution located in the West Netherlands Basin is utilized to perform sensitivity analysis<sup>4</sup>. A porosity distribution of the model is displayed in Fig.3. The model mainly consists of Berkel and Delft sandstone (around 0.8 million grid blocks) and shale layers (approximately 2.4 million grid blocks) with several faults. One of the major outcomes from the analysis is the shale layers, which are generally ignored in numerical simulation of hydrocarbon reservoirs, can significantly extend the lifetime (time before thermal breakthrough) of geothermal reservoirs. The results demonstrate the sensitivity of doublet lifetime to these parameters varies from years to decades.
  </p>
  <p>
        <img src="{{ site.baseurl }}/assets/img/project_photos/appl/CRECCIT.gif" width="100%" class="left" />

		<h5><em>Fig.3: Porosity distribution and thermal front propagation of realistic geothermal reservoir. </em></h5>

	<p>
	 The high numerical performance of DARTS makes it possible to run a large ensemble of models at high geological resolution for uncertainty quantification. Besides, the influence of various production regimes (well placement, production rate, etc.) and geological parameters (overburden, permeability-porosity correlation, etc.) to the heat production and doublet lifetime are shown in Fig.4. In overall, spatial heterogeneity of facies in geothermal reservoirs introduces large variability in energy production and demand uncertainty quantification for an accurate prediction of technologic and economic parameters of the process.
	</p>  

        <img src="{{ site.baseurl }}/assets/img/project_photos/appl/creccit_factors.png" width="100%" class="left" />

		<h5><em>Fig.4: Variation of the double lifetime with three factors: facies (a), well placement (b) and flow rate (c). </em></h5>
        </p>

  </div>

  
   <h3>Geothermal flow in fractured systems </h3>
  <div>
  
  <p>Multi-phase mass and heat transfers are ubiquitous for modelling of the most energy-related subsurface applications. The presence of complicated fractures may significantly impact, or even determine, the dynamic transport process. Here, the multi-phase flow in a fractured high-enthalpy geothermal reservoir is numerically investigated. The utilized fracture network is sketched and scaled up from digital maps of an outcrop at Whitby Mudstone Formation. The discrete fracture model (DFM) is used to describe the fractured system. Complicate nonlinear physics is adopted to describe the phase transition process (i.e., steam condensation) initiated with cold water injection. The existence of the fracture network magnifies the uncertainty of heat transfer in the reservoir because of a wide range of fracture scales and the complex fracture geometry. To fulfil both accuracy and efficiency in the computation, the resolution of the grid is optimized through results and runtime comparison combined with detailed convergence analysis among different sets of grids. The results of energy depletion in typical carbonate reservoir is shown in Fig.7 for high-enthalpy (super-saturated steam) initial conditions. 

        <img src="{{ site.baseurl }}/assets/img/project_photos/appl/Geothermal_frac.gif" width="100%" class="left" />
		<h5><em>Fig.7: Energy depletion in a carbonate fractured reservoir: pressure (a), temperature (b) and liquid saturation (c). </em></h5>   </p>
  
    <p>
        With the optimal mesh resolution, we investigated the influence of flow rate and thermal parameters on thermal propagation, which are found to be sensitive to the flow rate, rock heat conductivity and heat capacity<sup>8</sup> as shown in Fig.8. The findings provide insights for the multi-phase mass and heat transport in the fractured high-enthalpy geothermal reservoirs, which can be taken as guidance for the real geothermal developments with uncertainties.
        
        <img src="{{ site.baseurl }}/assets/img/project_photos/appl/fracture_factors.png" width="100%" class="left" />
		<h5><em>Fig.8: Variation of the double lifetime with three factors: heat capacity (a), heat conductivity (b) and flow rate (c). </em></h5></p>
  </div>
  
  <h3>Uncertainty quantification for fractured reservoirs</h3>
  <div>
  <p>Performing uncertainty quantification on a large (high-fidelity) ensemble of Discrete Fracture Models (DFM) can become computationally unfeasible. With an advanced coarsening strategy for fractured reservoirs, the numerical solution can be evaluated as a different coarse level with a certain gain in simulation performance. In terms of main flow patterns, it is therefore expected that the resulting coarser representations are still very much suitable as a diagnostic tool for classifying the full ensemble of models. In Fig.9, the temperature distribution for geothermal application in typical carbonate reservoir is shown for four ensemble members at coarse and fine scales. 
	
		<img src="{{ site.baseurl }}/assets/img/project_photos/appl/fractures_ensemble.gif" width="100%" class="left">

		<h5><em>Fig.9: Temperature distribution for four members of ensemble at fine (upper row) and corse (lower row) scales. </em></h5></p>
	
	<p>Using the well rates, pressure, and field-scale production data from the coarse simulation results, a clustering algorithm can be performed to select ensemble representatives based on continuous Multi-Dimensional Scaling<sup>9</sup>. Once the ensemble representatives are determined at a certain coarse scale (relative fast procedure), the full stochastic response can be reconstructed for fine-scale. In Fig.10, this procedure is illustrated for full ensemble with members shown in Fig.9. 

		<img src="{{ site.baseurl }}/assets/img/project_photos/appl/reconstruction.png" width="90%" class="left">

		<h5><em>Fig.10: Clustering of MDS distances for coarse (a) and reconstruction of stochastic response at fine scales (b). </em></h5></p>
	
  </div>

  <h3>Supercritical CO2-brine interactions </h3>
  <div>
  <p> Geological storage of CO2 is a crucial and upcoming technology to reduce anthropogenic greenhouse gas emissions. Due to the buoyant characteristic of injected gas and the complex geology of subsurface reservoirs, the security of underground storage is a major concern. To assess the security of CO2 storage, an accurate prediction of the CO2 plume migration is essential. In this study, an accurate thermodynamic model is developed to describe realistic gas behaviour in a saline aquifer and to understand the factors affecting CO2 storage. A recently developed thermodynamic model is based on a combination of Peng-Robinson<sup>10</sup> and Kritchevsky-Illiinskaya<sup>11</sup>  equations of state. This model combines classic fugacity-based formulation for the supercritical gas phase and activity model combined with Henry's constants for the aqueous brine. </p>
  
  <p>
	<img src="/assets/img/project_photos/appl/CO2_dissol.gif" width="100%" class="left" />
	<h5><em>Fig.11: Supercritical CO2 dissolution in realistic 3D model of aqueous aquifer. </em></h5>	
  </p>
    
  
  <p>
  The phase behaviour based on this thermodynamic model and a consistent set of physical properties has been implemented in DARTS. An example of an enhanced dissolution of supercritical CO2 in a geologic aquifer is illustrated by an unstructured 3D model shown in Fig.11. The model can accurately capture a phase behaviour in supercritical CO2-brine-impurity system and predict an enhanced dissolution rate for the variety of changing parameters including pressure, temperature and salinity of brine. The enhanced dissolution rate in realistic 3D conditions is different from its 2D analogue. This model can be fully coupled with chemical reaction relevant to CO2 sequestration<sup>12</sup> for longer time-scale predictions.
   </p> 
  </div>

  <h3>Multiphase flow and reactive transport </h3>
  <div>
  <p>
  We introduce an efficient element based reduction technique for molar formulation. The chemical equilibrium constraints are included into the multiphase multi-component flash calculation which solves the thermodynamic and chemical phase equilibrium simultaneously<sup>13</sup>. This provides a generic treatment of chemical and thermodynamic equilibrium within the successive substitution loop of multiphase flash to accommodate chemical precipitation and dissolution. Using the Equilibrium Rate Annihilation matrix allows us to reduce the governing unknowns to the element conservation equations while the coupling between chemical and thermodynamic equilibrium is captured by modified multiphase flash equations. </p>
   
   <p> A finite-volume unstructured discretization in space is applied together with a fully-implicit approximation in time. The resulting complex nonlinear system is parameterized using the OBL approach. In OBL, the time-consuming phase and chemical equilibrium computations are significantly decreased which reduce linearization time and the number of nonlinear iterations. Besides, equilibrium reactions are fully coupled with kinetic reactions in DARTS. Fig.12 presents several examples where equilibrium reactions describing the dissolution in carbonates are compared with the kinetic reactions at different kinetic rates. </p>

   <p>
	<img src="/assets/img/project_photos/appl/dissolution.gif" width="70%" class="center" />
	<h5><em>Fig.12: Dissolution with equilibrium (a), high-rate (Da~10) kinetic (b) and lower rate (Da~0.001) kinetic reactions. </em></h5>	
  </p>
  
    <p> Another example in Fig.13 presents kinetic dissolution in the complex fractured system at different aperture distribution decreasing from (a) to (c). In Fig.13,a, the acidic fluid is propagated by fracture system to the right border while in Fig.13,c, fractured system is almost closed and plays the role of permeability perturbation. </p> 
  
   <p>
	<img src="/assets/img/project_photos/appl/dissolution_frac.png" width="80%" class="center" />
	<h5><em>Fig.13: Kinetic dissolution in fractured reservoir with fractures apperture changing from 1 mm (a) to 0.5 mm (b) and finally to a fully closed system (c). </em></h5>	
  </p>
  
  </div>


  <h3>Modeling of dissolution in core </h3>
  <div>

	<p>Acidizing is a widely used technique for intensification of wells. At certain conditions, acid injection results in a formation of highly conductive channels, e.g. wormholes. The associated rock matrix dissolution is highly nonlinear and may influence the fluid flow as well as rock properties. Wormhole patterns and breakthrough time are mainly controlled by acid strength and injection rate. We developed a fully implicit method (FIM) to numerically solve the reactive flow and transport problem coupled with equilibrium and kinetic reactions associated with the acid injection. The developed framework is aimed to predict a pattern of dissolution as well as wormhole breakthrough time. For an accurate description of species interactions, we directly connect PHREEQC equilibrium computation with FIM framework for kinetic dissolution using an element balance approach<sup>13</sup>. This coupling was achieved with an application of an Operator-Based Linearization scheme<sup>14</sup> utilized within DARTS.</p>

	<p>The developed solution is validated against experimental study<sup>14</sup>, which also includes the full physics numerical model. Results are given in Fig.14. Two numerical results obtained starting from the same porosity distribution but processed by very different technique demonstrate similar wormhole formation. </p>
	

	<p>	<img src="{{ site.baseurl }}/assets/img/project_photos/appl/shell_2d.jpg" width="35%" class="left">
		<img src="{{ site.baseurl }}/assets/img/project_photos/appl/darts_2d.png" width="35%" class="right">

	<h5><em>Fig.14: Simulation of wormholes starting from the same initial porosity distribution with (a) sequential coupling<sup>15</sup> and (b) fully implicit method (DARTS). </em></h5>	
  </p>	
	
	    <p>
Full 3D model for dissolution in the core is shown in Fig.15. Main criteria for validation are wormhole breakthrough time and amount of rock matrix dissolved. A qualitative comparison shows a reasonable match in terms of break-through time and competing wormholes spatial distribution. The wormhole formation and propagation are accurately captured in high-resolution 3D geometry.
  

	<img src="/assets/img/project_photos/appl/core_wormholes_.gif" width="90%" class="left" />
	<h5><em>Fig.15: 3D simulation of wormholes (a) and results of experiments (b). </em></h5>	
  </p>	 
  
  

  </div>

  <h3>Modeling of foam experiments</h3>
  <div>
  <p> Foam improves significantly the sweep efficiency of gas injection. Foam-oil displacement in reservoirs involves strongly nonlinear physics, e.g. multiphase flow and transport with oil-foam interactions. The nonlinearity of this process challenges conventional simulation, which often translates into a high computational cost. To address this problem, we extend an Operator-Based Linearization (OBL) approach for simulation of foam EOR processes. Foam in porous media is described using an implicit-texture model with two flow regimes. The OBL approach is applied to reduce the nonlinearity of the foam problem. We validate the numerical-simulation results using three-phase fractional-flow theory for foam-oil flow. We conduct a series of numerical validation studies to investigate the accuracy and efficiency of the proposed approach. The OBL foam model shows good agreement with analytical solutions at different conditions and foam parameters as shown in Fig.16. </p>
  
  <p>
  <img src="/assets/img/project_photos/appl/Comparison.bmp" width="90%" class="left" />
  <h5><em>Fig.16: Comparison between analytical solution and simulation results. The upper figures are composition path (fmoil=0.3) in ternary diagram, and the lower row are saturation profile at given PVI. </em></h5></p>

  <p> The validated foam model was used for predictive modelling of foam core experiments. The porosity of core was reconstructed based on the difference between wet and dry scans<sup>16</sup>. Next, simulation of oil displacement by foam was modelled and compared with experimental results<sup>17</sup>. As shown in Fig.17, foam creates oil banks which prevent gas from escaping. In overall, both simulation and experimental results have a reasonably good match.
  
<!--  <img src="/assets/img/project_photos/appl/porosity_3D.png" width="60%" class="center" />
  <h5><em>Fig.16: Discretization scheme based on CT image and porosity distribution of the Bentheimer core. </em></h5>
-->
	</p>
  <p> 
  <img src="/assets/img/project_photos/appl/Sg.bmp" width="85%" class="left" />
  <img src="/assets/img/project_photos/appl/gas saturation.gif" width="85%" class="left" />
  <img src="/assets/img/project_photos/appl/So.bmp" width="85%" class="left" />
  <img src="/assets/img/project_photos/appl/oil saturation.gif" width="85%" class="left" />
  <h5><em>Fig.17: Gas saturation and oil saturation profile at the given PVI. </em></h5></p>
  </div>


  <h3>Physics-based data-driven models </h3>
  <div>
  
 <p> We propose a novel approach where a proxy model combines limited information about a spatial configuration of the hydrocarbon field and a simplified description of the governing physics. The approach contains several stages: in the first, the spatial connectivity graph is generated based on positions of wells and a limited log interpretation. Next, unstructured gridding is applied for the construction of spatial connectivity graph. The governing physical description is integrated using Operator-Based Linearization (OBL) approach. The parameters of this proxy model are regressed to the observation data using gradient optimization assisted by machine learning. </p>
 
	<p> The proposed approach is validated based on high-resolution Brugge-field model<sup>18</sup>. The synthetic production data for the training period was generated based on high-fidelity model run with varying BHP controls following the original Brugge model schedule with a 5% white noise imposed to resulting oil and water rates. The discretized model for high-fidelity Brugge-field and proxy model is shown in Fig.18. Here, the number of control volumes decreased by more than two orders of magnitude.
	
		<img src="/assets/img/project_photos/appl/Brugge.png" width="80%" class="center" />
	<h5><em>Fig.18: High fidelity Brugge model, used to generate truth model response (139x48x9 grid blocks) (a) and unstructured proxy model with 283 elements only (b).</em></h5>	
	</p>
	
	<p>	The resulting proxy model performs three orders of magnitude faster when applied in production optimization in comparison to the high-fidelity model (0.03 vs. 97.3 sec). Fig.19 illustrates a two-year production forecast for high-fidelity and trained proxy model which indicate relatively accurate rate prediction for all 20 production wells. Notice that in the case of data-driven models, underlying geological information was never used. </p>

   <p>
	<img src="/assets/img/project_photos/appl/data_driven.png" width="80%" class="center" />
	<h5><em>Fig.19: Oil rates for all 20 production wells in Brugge field: grey lines represent oil production rates from prior ensemble, black line – true response, and red line – proxy response </em></h5>	
  </p>	
 

  </div>
  

</div>

<br>

<h1><a id="References">References: </a></h1>
<h5>
	<ol>
      <li>
	  Wang, Y., Voskov, D., Khait, M., Bruhn, D. (2020). An efficient numerical simulator for geothermal simulation:  A benchmark study. Applied Energy, 264.
		<a href="https://doi.org/10.1016/j.apenergy.2020.114693" target="_blank">doi:10.1016/j.apenergy.2020.114693</a>
	  </li>
	  
      <li>
	  O'Sullivan, M.J., Pruess, K., Lippmann, M.J., (2001). State of the art geothermal reservoir simulation, Geothermics, 30 (4), pp. 395-429. 
	 	<a href="https://doi.org/10.1016/S0375-6505(01)00005-0" target="_blank">doi:10.1016/S0375-6505(01)00005-0</a>
	  </li>	  
      <li>
	  Garipov, T.T., Tomin, P., Rin, R., Voskov, D.V., Tchelepi, H.A., (2018). Unified thermo-compositional-mechanical framework for reservoir simulation, Computational Geosciences, 22 (4), pp. 1039-1057. 
	 	<a href="https://doi.org/10.1007/s10596-018-9737-5" target="_blank">doi:10.1007/s10596-018-9737-5</a>
	  </li>
      <li>
		Saeid, S., Wang, Y., Daniilidis, A., Khait, M., Voskov, D. and Bruhn, D. (2020). Lifetime and Energy Prediction of Geothermal Systems: Uncertainty Analysis in Highly Heterogeneous 	Geothermal Reservoirs (Netherlands), World Geothermal Congress. 
		<a href="https://pangea.stanford.edu/ERE/db/WGC/papers/WGC/2020/22157.pdf" target="_blank">World Geothermal Congress 2020.</a>
	  </li>		
	
	  <li> Karimi-Fard, M., Durlofsky, L. J., & Aziz, K. (2003). An efficient discrete fracture model applicable for general purpose reservoir simulators. In SPE Reservoir Simulation Symposium. Society of Petroleum Engineers. 
		<a href = "https://doi.org/10.2118/79699-MS" target="_blank">doi:10.2118/79699-MS</a>
	  </li>
<!--	  <li> 
	  Karimi-Fard, M., Durlofsky, L.J., (2016). A general gridding, discretization, and coarsening methodology for modeling flow in porous formations with discrete geological features, Advances in Water Resources, 96, pp. 354-372. 
	  <a href = "https://doi.org/10.1016/j.advwatres.2016.07.019" target="_blank">doi:10.1016/j.advwatres.2016.07.019</a>
	  </li> 
-->	  
	  <li> 
	  de Hoop, S., Voskov, D. and Bertotti, G. (2019). Uncertainty quantification and history matching for naturally fractured carbonate reservoirs. Third EAGE WIPIC Workshop: Reservoir Management in Carbonates, Qatar.
	  <a href = "https://www.earthdoc.org/content/papers/10.3997/2214-4609.201903106" target="_blank">Reservoir Management in Carbonates</a>
	  </li>
	  <li>
	  Bisdom, K., Bertotti, G. and Nick, H.M. (2016) The impact of different aperture distribution models and critical stress criteria on equivalent permeability in fractured rocks. Journal of Geophysical Research: Solid Earth, 121(5), pp.4045-4063.
	  <a href = "https://doi.org/10.1002/2015JB012657" target="_blank">doi:10.1002/2015JB012657</a>	  
	  </li>
  
      <li>
		Wang Y., de Hoop S., Voskov D., Bruhn D., Bertotti G. (2020). Modeling of High-Enthalpy Geothermal Projects in Fractured Reservoirs, World Geothermal Congress. 
		<a href="https://pangea.stanford.edu/ERE/db/WGC/papers/WGC/2020/33021.pdf" target="_blank">World Geothermal Congress 2020.</a>
	  </li>		   
	  
	  
	  <li>
	  de Hoop, S., Voskov, D.V., Vossepoel, and F.C. and Jung, A. (2018) Quantification Of Coarsening Effect On Response Uncertainty In Reservoir Simulation. In ECMOR XVI-16th European Conference on the Mathematics of Oil Recovery.
		<a href = "https://doi.org/10.3997/2214-4609.201802223" target="_blank">doi:10.3997/2214-4609.201802223</a>
	  </li>
	  <li>
			Peng, D.-Y. and Robinson, D.B. (1976). A New Two-Constant Equation of State, Industrial and Engineering Chemistry Fundamentals, 15 (1), pp. 59-64.  
			<a href = "https://doi.org/10.1021/i160057a011" target="_blank">doi:10.1021/i160057a011</a>
	  </li>
	  <li>
			Kritchevsky, I. and Illiinskaya, A. (1945). Partial molal volumes of gases dissolved in liquids. Acta Physicochimica (URSS). 
			<a href = "https://doi.org/10.1016/0378-3812(82)80033-2" target="_blank">doi:10.1016/0378-3812(82)80033-2</a>
	  </li>

	  <li>
			Voskov, D.V., Henley, H., Lucia, A., 2017. Fully compositional multi-scale reservoir simulation of various CO2 sequestration mechanisms, Computers and Chemical Engineering, 96, pp. 183-195. 
			<a href = "https://doi.org/10.1016/j.compchemeng.2016.09.021" target="_blank">doi:10.1016/j.compchemeng.2016.09.021</a>
	  </li>	  

	  <li>
			Kala, K. and Voskov, D. (2019). Element balance formulation in reactive compositional flow and transport with parameterization technique, Computational Geosciences.
			<a href = "https://doi.org/10.1007/s10596-019-9828-y" target="_blank">doi:10.1007/s10596-019-9828-y</a>
	  </li>	  

	  <li>
			de Hoop, S., Voskov, D. (2019). Parametrization Technique for Reactive Multiphase Flow and Transport, In. SIAM Geosciences.
			<a href = "https://www.pathlms.com/siam/courses/11267/sections/14643/video_presentations/128804" target="_blank">Video Presentation at SIAM GS19</a>
	  </li>	   

	  <li>
			Snippe, J., Berg, S., Ganga, K., Brussee, N., Gdanski, R. (2020) Experimental and numerical investigation of wormholing during CO2 storage and water alternating gas injection, International Journal of Greenhouse Gas Control, 94, art. no. 102901 . 
			<a href = "https://doi.org/10.1016/j.ijggc.2019.102901" target="_blank">doi:10.1016/j.ijggc.2019.102901</a>
	  </li>	  	  
	  
<!--	  <li> Margert, A. (2019). Dissolution Patterns Prediction in Carbonate System. MSc thesis, Delft University of Technology.
	  <a href = "" target="_blank">TU Delft MSc thesis repository</a>
	  </li> 	  
-->	  
	  <li> Gong J., Vincent-Bonnieu S., Kamarul Bahrim R., Groenenboom J., Farajzadeh R., Rossen W. (2018)
		Modelling of liquid injectivity in surfactant-alternating-gas foam enhanced oil recovery. In SPE EOR
		Conference at Oil and Gas West Asia. Society of Petroleum Engineers, 2018.
		<a href = "https://doi.org/10.2118/190435-MS" target="_blank">doi:10.2118/190435-MS</a>
	  </li>
  
    <li>
	  Tang, J., Vincent-Bonnieu, S., Rossen, W.R. (2019) CT coreflood study of foam flow for enhanced oil recovery: The effect of oil type and saturation. Energy, 188, art. no. 116022.
		<a href="https://doi.org/10.1016/j.energy.2019.116022" target="_blank">doi:10.1016/j.energy.2019.116022</a>
	  </li>
	  
    <li>	  
		Peters, E., Arts, R.J., Brouwer, G.K., Geel, C.R., Cullick, S., Lorentzen, R.J., Chen, Y., Dunlop, K.N.B., Vossepoel, F.C., Xu, R., Sarma, P., Alhutali, A.H., Reynolds, A.C. (2010). Results of the brugge benchmark study for flooding optimization and history matching, SPE Reservoir Evaluation and Engineering, 13 (3), pp. 391-405. 	  
		<a href="https://doi.org/10.2118/119094-PA" target="_blank">doi:10.2118/119094-PA</a>
	  </li>


	  
	</ol>
</h5>
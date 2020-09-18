+++
title = "Visualize This! in 2016-2019"
aliases = ["visualizeThis"]
author = "WestGrid"
+++

Select the year: &nbsp; [2019](#2019) &nbsp; [2018](#2018) &nbsp; [2017](#2017) &nbsp; [2016](#2016)




<!-- localhost:1313 -->
<!-- https://scivis2021.netlify.app -->




# 2019
### Incompressible transitional air flow over a wind turbine section

The theme of the 2019 challenge was distributed rendering, i.e. visualization of very large datasets that require
parallel rendering on a cluster. Participants could use either their own data or the supplied dataset kindly provided
for this competition by Joshua Brinkerhoff (UBC Okanagan). This dataset came from an OpenFOAM numerical simulation of
incompressible transitional air flow over a wind turbine section.

### First place

The first place was taken by Thierry Villeneuve, a Ph.D. student from the Department of Mechanical Engineering at
Université Laval, for his time-dependent 3D volume rendering of the vorticity magnitude in a turbulent turbine wake. The
dataset was taken from Thierry's own CFD model using a DDES (Delayed Detached-Eddy simulation) approach with a domain
composed of approximately 10<sup>8</sup> cells. The simulation has been performed on Compute Canada's Niagara cluster
using 10 nodes (400 cores) and took about two months. The output with the three components of the vorticity vector was
saved every 20 time steps, resulting in ~2200 frames. The blue / green semi-opaque regions represent low-vorticity
zones, while the red regions show high-vorticity zones.

{{< vimeo 380107780 >}}
<sup>(Or click <a href="https://vimeo.com/380107780" target="_blank">here</a> to watch this video directly on
Vimeo.)</sup>

### Second place

The second place went to Yohai Meiron, a Postdoctoral Fellow from the Department of Astronomy & Astrophysics at the
University of Toronto, for his demonstration of VTK-m filters and rendering using the competition's "default"
dataset. <a href="http://m.vtk.org" target="_blank">VTK-m</a> is a scientific visualization toolkit for multi-core
processor architectures (both CPUs and GPUs). With an interface currently only in C++, VTK-m is a complete rewrite of
the serial VTK algorithms and functions. Some functionality of VTK-m could be used through ParaView and VisIt.

While VTK-m supports MPI through a class called `PartitionedDataSet`, many if not most of its built-in algorithms do not
know how to handle this class. The solution was to use another library called <a
href="https://github.com/Alpine-DAV/vtk-h" target="_blank">VTK-h</a> that is basically a wrapper around VTK-m to enable
hybrid parallelism.

The video below use four different rendering techniques. Of these the most interesting visually is the last part showing
volumetric rendering of the z-component of the vorticity vector with nice coherent structures above and below the
airfoil, and a gap between the lower structure and the airfoil itself.

{{< vimeo 380126028 >}}
<sup>(Or click <a href="https://vimeo.com/380126028" target="_blank">here</a> to watch this video directly on
Vimeo.)</sup>

### Third place

The third place was taken by Joshua Ludwig, a Ph.D. Student in Plasma Physics from the University of Alberta. His video
(below) was rendered using Joshua's own parallel ray tracing rendering code on 5 nodes (160 cores) on Compute Canada's
Graham cluster.

The video shows plasma electron density (low in blue and high in red). The camera is moving at the speed of light to
follow a short high intensity laser pulse (not shown). This laser pulse is so intense that it expels all the plasma
electrons from its path and creates a bubble-like feature in the plasma. This bubble feature still contains positively
charged ions due to their large mass and hence has strong electric fields that pull electrons into the bubble and
accelerate them as they ride along with the laser pulse. This mechanism is called Relativistic Laser Wakefield
Acceleration.

The simulation was performed on 32 nodes (1280 cores) of Compute Canada's Niagara cluster using OSIRIS, a 3D fully
relativistic Particle-in-Cell plasma modelling code. It solved Maxwell's equations for the electric and magnetic fields
on a 3600x1800x1800 grid covering the domain 160x120x120&micro;m with ~23 billion electron particles. The output used
specifically to make this video was about 20TB.

{{< vimeo 380129427 >}}
<sup>(Or click <a href="https://vimeo.com/380129427" target="_blank">here</a> to watch this video directly on
Vimeo.)</sup>













# 2018

In the third annual *Visualize This!* competition participants could select their dataset: a
bio-molecular dynamics simulation or a rich set of linked humanities data.

### Interaction of a large protein structure with a cell's membrane

The bio-molecular dynamics dataset was taken from a coarse-grained Gromacs simulation of interaction of a large protein
structure with a cell's membrane. A cell's membrane is typically composed of two leaflets (single molecular layers),
comprised in this model of pure phosphatidylcholine (POPC) lipid molecules. The protein structure is a P-glycoprotein
(P-gp) embedded into the cell's membrane. Such proteins are responsible for the translocation of a wide range of
compounds across membranes.

A simple visualization with <a href="https://www.ks.uiuc.edu/Research/vmd" target="_blank">VMD</a> (below) shows the
horizontal cell membrane along with the embedded vertical protein. To further differentiate the two, we rendered the
protein beads as larger spheres.

![cell membrane with embedded protein](../images/both.png "cell membrane with embedded protein")

This simulation shows that the P-gp molecule acts as a lipid transporter protein, flipping membrane’s lipids from the
inner to the outer leaflet. We asked participants to visualize this process, finding those lipids that bind to the
protein.

### Linked humanities data

The Orlando British Women's Writing Dataset (Release 1: Biography and Bibliography) provided a rich set of linked open
data representing women's literary history from the beginnings to the present, concentrated on writing in English in the
British Isles but with tentacles out to other languages, literary traditions, and parts of the world. The competition
dataset contained 3,321,746 triples stored in the Resource Description Framework (RDF) format which is a standard format
for storing linked data called graphs.

To get an idea of the type of information in the dataset, you can browse the <a href="https://beta.cwrc.ca"
target="_blank">Canadian Writing Research Collaboratory</a> (CWRC) ontology's <a
href="http://sparql.cwrc.ca/ontologies/cwrc-preamble-EN.html#competency" target="_blank">competency questions</a>. For
the purpose of this competition, we suggested to address some more focused questions in the provided dataset.

### First place

The first place was taken by Philippe Nazair, a Data Visualization Developer at Université du Québec à Rimouski and part
of <a href="https://meridian.cs.dal.ca" target="_blank">the MERIDIAN consortium</a>. Philippe's visualization is
implemented as a static website with two layers: a graph viewer using the <a
href="https://github.com/vasturiano/3d-force-graph" target="_blank">3d-force-graph web component</a>, and a map viewer
implemented with <a href="https://leafletjs.com" target="_blank">Leaflet</a> to display markers on the map and written
biographies from <a href="http://orlando.cambridge.org" target="_blank">Cambridge's Orlando</a> author's page found in
the dataset. Below you can see a screen-capture video showing different interactions on this site. All JSON files for
the visualization were created with a Python backend. We especially appreciated sample graphs for radical and liberal
ideologies and other groups, as well as the ability to build more complex graphs by selecting a predicate and setting it
to a certain value, e.g. `hasActiveInvolvementIn = socialism`, or multiple values; each graph is limited to one
predicate. Individual graph nodes can be displayed as either text or draggable spheres.

{{< vimeo 306261749 >}}
<sup>(Or click <a href="https://vimeo.com/306261749" target="_blank">here</a> to watch this video directly on
Vimeo.)</sup>

### Second place

The second prize went to Usman Alim and Roberta Cabral Ramos Mota from the Department of Computer Science at the
University of Calgary. Below you can watch one of their visualizations (rendered with OSPRay in ParaView) showing the
protein cavity and two *highly-interacting* PO4 beads with the colour representing time step. This work was selected for
their skillful use of Python scripting for the bulk of the analysis: using <a href="https://www.mdanalysis.org"
target="_blank">MDAnalysis</a> library for identifying closely interacting membrane beads, and writing bead positions in
VTK to be rendered in ParaView. You can download an edited version of their Python analysis script [here](../analysis.py).

{{< vimeo 306277152 >}}
<sup>(Or click <a href="https://vimeo.com/306277152" target="_blank">here</a> to watch this video directly on
Vimeo.)</sup>

### Third place

The third place was taken by Catherine Winters from the <a href="https://www.lib.sfu.ca/help/publish/dh/dhil"
target="_blank">Digital Humanities Innovation Lab</a> at Simon Fraser University. This visualization is powered by <a
href="https://d3js.org" target="_blank">D3.js</a> and <a href="https://threejs.org" target="_blank">Three.js</a>, with
all JSON data files produced with Python scripting. Not all features of this visualization are complete, so we are not
showing it here, but it is likely to remain a side project in the lab over the next few months, with the promise to show
clustering based on ideology, religion, or geographic proximity.

<!-- https://westgrid.github.io/visualizeThis -->
<!-- https://www.computecanada.ca/research-portal/national-services/visualization -->
<!-- <a href="link" target="_blank">text</a> -->









# 2017
### Airflow around counter-rotating wind turbines

<!-- https://www.westgrid.ca/visualizethis_challenge -->

The second annual *Visualize This!* Challenge asked participants to visualize a 3D fluid flow around two
counter-rotating wind turbines. The provided dataset contained only one time step from the simulation, so participants
had to create a dynamic visualization from the static data. We received many good submissions, with three most
outstanding visualizations shown below.

### First place

The first place was taken by Jarno van der Kolk, a postdoctoral researcher from the University of Ottawa. Jarno's
visualization (shown below) was selected for its overall presentation, with a very informative voice-over. We especially
appreciated the toy conceptual animation rendered entirely in ParaView and the use of programmable sources for rendering
grass, the house, and the roof in the same scene with the turbine blades. The colour scheme for showing the wind speed
was very nice, with red/blue indicating the flow which is faster/slower than the incoming air. Jarno's visualization
provided a clear explanation of what forces exactly drive the blades.

{{< vimeo 246859562 >}}
<sup>(Or click <a href="https://vimeo.com/246859562" target="_blank">here</a> to watch this video directly on
Vimeo.)</sup>

### Second place

The second prize went to Nadya Moisseeva, a PhD student in the Department of Earth, Ocean and Atmospheric Sciences at
UBC. Nadya's work (shown below) was selected for its use of several innovative techniques in her visualization:

- use of the Stream Tracer With Custom Source filter through a grid of seed points in a vertical
  cross-section (forcing the streamlines to be redrawn at each height),
- animating the position of multiple integration time contours,
- nice colour selection in the volumetric plots of regions of high/low pressure around the blades,
- semi-transparent vorticity surfaces,
- final multi-layer animation combining seven properties in a single timeline,
- smooth continuous transitions between all animations,
- informative burned-in captions, and
- nice use of several rotation and displacement motions.

{{< vimeo 246879618 >}}
<sup>(Or click <a href="https://vimeo.com/246879618" target="_blank">here</a> to watch this video directly on
Vimeo.)</sup>

### Third place

The third place was taken by Dan MacDonald, Thangam Natarajan, Richard Windeyer, Peter Coppin, and David Steinman, a
joint team from the <a href="https://bsl.mie.utoronto.ca" target="_blank">Biomedical Simulation Laboratory</a> of the
University of Toronto and the <a href="https://www2.ocadu.ca/research/connection/perceptual-artifacts-lab"
target="_blank">Perceptual Artifacts Laboratory</a> of OCAD University. Their visualization (shown below) was selected
for its unique use of Blender's game engine to let a user walk through the ParaView-created scene, toggle the visibility
of the various physical components, and for coupling the visual scene with the SuperCollider server to produce
on-the-fly audio from selected Q-criterion under the microphone in Blender's game engine.

{{< vimeo 246882338 >}}
<sup>(Or click <a href="https://vimeo.com/246882338" target="_blank">here</a> to watch this video directly on
Vimeo.)</sup>













# 2016
### Visualizing multiple variables in a global ocean model

The inaugural *Visualize This!* Challenge received 125 expressions of interest from researchers across Canada and the
United States. Participants had 31 days to create a visualization solution for an oceanography model contributed by an
Earth Sciences researcher. The main challenge in the data was to visualize multiple 3D variables at the same time.

A University of Calgary (UofC) research team comprised of Allan Rocha, Usman Alim and Julio Daniel Silva has won first
prize for their creative approach to using layering, animation, and elements of interactivity in their submission. A
video of their submission can be viewed below:

{{< vimeo 193016949 >}}
<sup>(Or click <a href="https://vimeo.com/193016949" target="_blank">here</a> to watch this video directly on
Vimeo.)</sup>

"We started this project with a dream of being able to create layered visualizations on arbitrary surfaces to visualize
multiple attributes, such as we can see commonly in 2D," said Rocha, at the time a PhD Candidate and member of the <a
href="http://visagg.cpsc.ucalgary.ca" target="_blank">Visualization and Graphics Group (VISAGG)</a> and the <a
href="http://ires.cpsc.ucalgary.ca/" target="_blank"> Interactive Modeling, Visualization and Visual Analytics Research
Group</a> at the UofC. "These visualizations are inspired by concepts of painting and other aspects from art and
information visualization. From this thinking process, the decal-maps emerged."

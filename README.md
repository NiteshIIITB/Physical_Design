<h1>Day 1</h1>
<details>
  <summary><strong>Introduction to OpenLane</strong></summary>
  <h2>Introduction</h2>
  <p>The advent of open-source technology for chip development has brought about significant advancements, particularly with the availability of RTL designs and EDA (Electronic Design Automation) Tools at no cost. One notable contribution in this arena is the <a href="https://skywater-pdk.readthedocs.io/en/latest/rules.html" target="_blank">SKY130 PDK</a> collaboration between Skywater Technologies and Google. This development has effectively bridged gaps in open-source chip development.<br><br>

Initially, the landscape of open-source chip design presented some challenges. There was a lack of clarity in the design flow, and the SKY130 PDK was primarily compatible with industrial-grade equipment. These issues were skillfully addressed through the creation of <a href="https://github.com/The-OpenROAD-Project/OpenLane" target="_blank">OpenLane</a>, a comprehensive solution that offers a fully automated and streamlined RTL-to-GDSII (Register Transfer Level to Graphic Design System II) design flow.<br><br>

OpenLane stands out as an exceptional achievement in open-source chip development. It's important to note that OpenLane is not a standalone product; rather, it is a meticulously crafted workflow comprised of various EDA tools, automation scripts, and the SKY130 PDK. These components have been optimized to seamlessly integrate with open-source EDA tools, making chip development accessible to a wider audience and enhancing the efficiency of the entire process.</p>

<h2>Advantages of OpenLane</h2>
<p>The introduction of OpenLane has been a game-changer in the field of open-source chip development. This innovative solution goes beyond mere software; it represents a holistic approach to RTL-to-GDSII design flow. Here are some key aspects of OpenLane to highlight:<br>

<b>Automation and Integration:</b> OpenLane is designed to automate the entire chip design process, from RTL synthesis to physical design, and it seamlessly integrates various EDA tools into a unified workflow. This automation greatly reduces the need for manual intervention, saving time and effort for designers.<br>

<b>Accessibility:</b> OpenLane is accessible to a wide range of chip developers, including hobbyists, researchers, and small companies, who may not have access to costly commercial EDA tools. Its open-source nature fosters collaboration and knowledge sharing within the chip design community.<br>

<b>Customization:</b>OpenLane is highly customizable, allowing users to tailor the design flow to their specific project requirements. This flexibility empowers designers to experiment with different configurations and optimizations, ultimately leading to better chip designs.<br>

<b>Community Support:</b>OpenLane benefits from a vibrant and engaged user community. Developers and enthusiasts contribute to its continuous improvement, share best practices, and offer support to newcomers. This collaborative ecosystem accelerates the development of open-source chip design methodologies.<br>

<b>Cost Efficiency:</b> By leveraging open-source tools and resources, OpenLane significantly reduces the cost barriers associated with chip development. This affordability enables smaller organizations and individuals to participate in chip design projects that were previously financially prohibitive.<br>

<b>Integration with SKY130 PDK:</b> OpenLane's compatibility with the SKY130 PDK is a crucial component of its success. It ensures that designers can utilize the open-source PDK and take advantage of the latest manufacturing technologies, enabling them to create cutting-edge chips.

</p>
</details>

<details>
  <summary><b>RTL to GDS using Openlane</b></summary>
 The RTL to GDS (Register Transfer Level to Graphic Design System) flow in OpenLane is a multi-stage, automated process used to design and manufacture integrated circuits (ICs). This flow takes a high-level description of the chip's functionality in RTL (Register Transfer Level) and transforms it into a physical layout that can be manufactured.

Here's a step-by-step explanation of the RTL to GDS flow in OpenLane:

1. **Design Entry (RTL):**
   - The process begins with the creation of the RTL design, which represents the functionality of the digital logic circuit using a hardware description language (HDL) like Verilog or VHDL.
   - Designers define the behavior of the circuit, specifying how data flows and registers are updated.

2. **Synthesis:**
   - The RTL code is synthesized into a gate-level representation. This step involves mapping the high-level RTL constructs to a library of standard cells (AND, OR, Flip-Flops, etc.).
   - The synthesized design is optimized for area, power, and timing.

3. **Floorplanning:**
   - In this stage, the physical area of the chip is divided into blocks and areas for specific functions like logic, memory, and I/O.
   - Placement of standard cells and macros is determined, taking into account factors like signal timing and power distribution.

4. **Placement:**
   - The synthesized gates are placed within the designated floorplan areas.
   - The placement aims to minimize wirelengths, reduce congestion, and meet timing constraints.

5. **Clock Tree Synthesis (CTS):**
   - The clock tree is a network of buffers and wires that distribute clock signals to all sequential elements (flip-flops) in a chip.
   - CTS optimizes clock distribution, ensuring that clock signals reach all parts of the chip with minimal skew and power consumption.

6. **Routing:**
   - Routing connects the inputs and outputs of gates to create the physical connections necessary for the chip's functionality.
   - Global and detailed routing steps are performed to establish the complete routing fabric.

7. **DRC (Design Rule Check) and LVS (Layout vs. Schematic):**
   - DRC checks the physical layout against manufacturing design rules to ensure that the chip can be manufactured without errors.
   - LVS compares the physical layout to the expected behavior of the synthesized netlist to ensure correctness.

8. **GDS Generation:**
   - Once the design passes DRC and LVS, a GDSII (Graphic Data System) file is generated. This file contains the final layout information that can be used for chip fabrication.

9. **Tape-out:**
   - The GDSII file is submitted to a semiconductor foundry for manufacturing. This step involves finalizing the design for production.

10. **Post-Tapeout Steps:**
    - After tape-out, the chip goes through a series of steps, including wafer fabrication, testing, and packaging, to prepare it for market release.

OpenLane automates and streamlines this entire RTL to GDS flow, making it accessible to a broader audience and significantly reducing the time and effort required for chip design. It achieves this by integrating various EDA tools, optimizing parameters, and offering customization options to meet specific project requirements.

<br>
<div align="center">
  <img src = "https://github.com/NiteshIIITB/Physical_Design/assets/140998787/31ab9d94-f28b-4900-80d4-ce9bf8cef25e">
</div>
  


</details>
<details>
  <summary><b>RTL and Synthesis using OpenLane</b></summary>
  <h4>Commands Used</h4>

```
docker
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a
```
<div align = "center">
  <img src ="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/f6e044ba-84dd-4925-a111-4787d6110b1e">
</div>

<h3>Synthesis</h3>

<h4>Command Used</h4>

```
run_synthesis
```
<h4>Synthesis Results<h4>
<div align = "center">
  <img src ="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/6efd023c-edc1-4a91-bc91-b32793a35c62">
</div>

<h4>Flop Ratio</h4>

```
Flop ratio = Number of D Flip flops 
             ______________________
             Total Number of cells
```

From Synthesis Stats Flop ratio = 1512/10104 = 0.1496(14.96%)
</details>

<h1>Day 2 : Floorplanning and Introduction to Library Cells</h1>
<details>
  <summary><b>Chip Floorplanning considerations</b></summary>
  <h3>Floorplanning</h3>
  <p>Floorplanning is a crucial early-stage step in the physical design process, where the initial layout of the chip is defined. It involves making high-level decisions about how various components will be arranged on the silicon substrate.</p>
  <h3>Core Area Definition:</h3>
  <p>Determine the overall dimensions of the chip and define the core area where the primary functional blocks and standard cells will be placed. This core area is surrounded by peripheral regions that may contain I/O pads and other necessary structures.</p>
  <h4>Utilization Factor</h4>
  <p>The Utilization Factor is calculated as the area occupied by the netlist divided by the total core area. A Utilization Factor of 1 indicates full utilization with no extra space, but in practice, it's typically around 0.5-0.6.</p>
  
```
  Utilization factor = Area occupied by Netlist/Total core Area
```

  <h4>Aspect ratio</h4>
  <p>The Aspect Ratio is the ratio of the chip's height to its width. A value of 1 signifies a square chip, while other values represent a rectangular shape.</p>
  
```
Aspect ratio = Chip Height/Chip Width
```  
  
  

  <h3>Preplaced cells</h3>
  <p>Pre-placed cells are fixed-position Intellectual Properties (IPs) with significant combinational logic. They're positioned before automated placement and routing in integrated circuit design, hence the term "pre-placed."</p>
  <p>Preplaced cells are generally placed at the location from where it is nearest to all the other circuit blocks accessing it. Once placed they are not modified in terms of location thereafter.</p>

  <h3>Decoupling Capacitor</h3>
  <p>
    Pre-placed cells are often accompanied by decoupling capacitors (decaps) in integrated circuit (IC) design. Long wire lengths introduce resistive and capacitive effects that can result in substantial power supply voltage drops before reaching the logic circuits. This can push signal values into undefined regions, beyond the noise margin. Decaps are substantial capacitors charged to the power supply voltage and strategically positioned near the logic circuits. Their primary purpose is to decouple the circuit from the power supply, ensuring a stable voltage and supplying instantaneous current when needed. Decaps also mitigate crosstalk and facilitate efficient local communication.
  </p>
<h3>The problem of unstable ground</h3>
<div align ="center">
  <img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/fc5b5efb-0477-460e-8c4b-cc877733fc59">
  <br>
  <img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/a93a048f-4a54-40c6-b2a6-38ff5284fac8">
  <br>
  
</div> 
<p>Due to this it may happen that some of logic values may break Noise Margin producing errorneous results.</p>
<h3>Power Planning(Solution)</h3>
<p>While each block on the chip cannot have individual decoupling capacitors (decaps) like pre-placed macros, effective power planning ensures that each block is equipped with its dedicated VDD and VSS pads. These pads are strategically connected to the horizontal and vertical power and ground (GND) lines, forming a comprehensive power mesh.</p>

<h3>Pin Placement</h3>
<p>The netlist specifies the interconnections between logic gates within the design. The region between the core and the chip's periphery is designated for the placement of I/O pins. Information regarding connectivity, often described in VHDL or Verilog, is leveraged to determine the precise locations of I/O pads for various pins. Subsequently, logical placement distinguishes the area allocated for pre-placed macros from the dedicated pin area.</p>

<div align="center">
<img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/d47a9118-5f3d-4b9d-8552-e7f2de7a35de">
  <br>
<img src = "https://github.com/NiteshIIITB/Physical_Design/assets/140998787/9ce61f2a-4d1a-4524-8299-98b528fd4fec">
  
</div>
</details>

<details>
  <summary><b>Floorplan in Openlane</b></summary>
  To perform the floorplanning process for the "picorv32a" design in OpenLANE and visualize the results in Magic, follow these steps, considering the importance files and environment variables:<br>

Important Files (in increasing priority order):<br>

<ul>
 <li>floorplan.tcl - System default environment variables.</li>
<li>config.tcl</li>
<li>sky130A_sky130_fd_sc_hd_config.tcl</li>
</ul>
Floorplan Environment Variables or Switches:
<ul>
<li><b>FP_CORE_UTIL:</b> Specifies floorplan core utilization.</li>
<li><b>FP_ASPECT_RATIO:</b> Sets the floorplan aspect ratio.</li>
<li><b>FP_CORE_MARGIN:</b> Defines the core-to-die margin area.</li>
<li><b>FP_IO_MODE:</b> Determines pin configurations (1 for equidistant, 0 for non-equidistant).</li>
<li><b>FP_CORE_VMETAL:</b> Sets the vertical metal layer.</li>
<li><b>FP_CORE_HMETAL:</b> Sets the horizontal metal layer.<br> 
Typically, these values are one greater than what's specified in the files.</li>
</ul> 

<h4>Command used</h4>

```
run_floorplan
```
<div align="center">

<img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/fc8c72c2-7f3e-455f-93e7-ac3e40e8d4e7">  
</div>

<h4>Post-Floorplan Run and Viewing the Floorplan in Magic:</h4>
<ul>
<li>After running the floorplan step in OpenLANE, a .def file representing the floorplan will be generated within the results/floorplan directory. This file encapsulates the layout and organization of the integrated circuit components.</li>
<li>To visualize the floorplan layout using the Magic VLSI layout tool, follow these steps:<br>

Open a terminal or command prompt.<br>

Navigate to the ```results/floorplan``` directory within your OpenLANE workspace.<br>
Once you're in the ```results/floorplan``` directory, invoke Magic to view the floorplan by running the following command:<br>

```
magic -T /home/OpenLane/sky130A.tech lef read ../../tmp/merged.min.lef def read picorv32.def &
```

</li>  
<div align="center">
  <img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/4ca2fff9-c9f3-469a-a964-2efd81362f34">
</div>  
</ul>  
In Magic layout design software:<br>
To zoom into a specific area of the layout, you can use the following steps:<br>
<ul>
<li>Select an area by clicking the left mouse button and dragging to create a selection box.</li>
<li>Then, hold the right mouse button and press the 'z' key. This action should zoom in on the selected area.</li>
</ul>
 <br> 
To identify various components within the layout, you can use the `what` command within the tkcon window. After making a selection (e.g., clicking on a component), enter the `what` command to get information about the selected component.
<br>
When you zoom in, you can also get a closer view of the decaps (decapacitors) present in the picorv32a chip or any other components.<br>

<br>
The standard cell can typically be found at the bottom left corner of the layout.<br>
<div>
  <img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/8fd3cab0-704d-4cd8-9fce-af8585b5ef6a">
</div>

</details>
<details>
  <summary><b>Placement</b></summary>
  Placement
The placement step in the OpenLANE ASIC flow involves positioning the synthesized netlist onto the floorplan. This process is performed in two stages:

<b>Global Placement:</b> In this stage, an optimal position for all cells is determined. The positions may not initially be legal, and cells may overlap. Optimization is carried out with the goal of reducing half-parameter wire length.

<b>Detailed Placement:</b> Following global placement, the positions of cells are adjusted to make them legal within the design. Legalizing cells is crucial from a timing perspective, ensuring that the chip meets its performance requirements.

Running the placement step in OpenLANE and visualizing the placement results in Magic can be accomplished with the following command:


```
run_placement
```


<div align="center">
<img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/6c12819c-2d9a-44a7-90e1-7ae7eef8db9f">
  
</div>

After running the placement step, you can use Magic to inspect and analyze the placement of cells, ensuring that they are positioned optimally and legally within the floorplan.


To view the design in magic 

```
magic -T /home/OpenLane/sky130A.tech lef read ../../tmp/merged.max.lef def read picorv32.def &


```
<div align="center">
<img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/1fb5d2a6-9ce8-48de-a3c7-6edc1bb3c4ad">
<img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/0c54e4a8-5b59-4cbb-8610-67e59155808b">
  
</div>

</details>
<details>
  <summary><b>Cell Design</b></summary>
  
 # Standard Cell Design Flow

**Inputs:**
- PDKs (Process Design Kits)
- DRC & LVS rules (Design Rule Check & Layout vs. Schematic rules)
- SPICE models
- Libraries
- User-defined specifications

**Design Steps:**
1. Circuit design
2. Layout design (Art of layout, Euler's path, and stick diagram)
3. Extraction of parasitics
4. Characterization (timing, noise, power)

**Outputs:**
- CDL (Circuit Description Language)
- LEF (Library Exchange Format)
- GDSII (Graphic Data System II)
- Extracted SPICE netlist (.cir)
- Timing, noise, and power .lib files

## Standard Cell Characterization Flow

A typical standard cell characterization flow includes the following steps:

1. Read in the models and tech files.
2. Read the extracted SPICE netlist.
3. Recognize the behavior of the cell.
4. Read the subcircuits.
5. Attach power sources.
6. Apply stimulus to the characterization setup.
7. Provide necessary output capacitance loads.
8. Provide necessary simulation commands.

The open-source software called GUNA can be used for characterization. Steps 1-8 are fed into the GUNA software, which generates timing, noise, and power models.

## Timing Parameter Definitions

| Timing Definition       | Value                  |
|------------------------|------------------------|
| slew_low_rise_thr      | 20% value              |
| slew_high_rise_thr     | 80% value              |
| slew_low_fall_thr      | 20% value              |
| slew_high_fall_thr     | 80% value              |
| in_rise_thr            | 50% value              |
| in_fall_thr            | 50% value              |
| out_rise_thr           | 50% value              |
| out_fall_thr           | 50% value              |
| rise delay             | time(out_fall_thr) - time(in_rise_thr)       |
| Fall transition time   | time(slew_high_fall_thr) - time(slew_low_fall_thr) |
| Rise transition time   | time(slew_high_rise_thr) - time(slew_low_rise_thr) |

A poor choice of threshold points can lead to a negative delay value. Therefore, a correct choice of thresholds is crucial in timing characterization.

</details>

<h1>Day 3:Library Cell Design using Magic Layout and ngspice Characterization</h1>
<details>
  <summary><b>CMOS Inverter ngspice simulations</b></summary>
  <h2>SPICE deck</h2>
  <p>A Spice deck, often referred to as a Spice netlist or simply Spice file, is a text-based input file used in electronic circuit simulation. Spice stands for "Simulation Program with Integrated Circuit Emphasis," and it is a widely used tool for simulating and analyzing electronic circuits.<br>

A Spice deck contains a description of the components and connections within an electronic circuit, including resistors, capacitors, inductors, transistors, voltage sources, current sources, and more. It specifies the values of these components, their models (which define their behavior), and the interconnections between them. The Spice deck also defines the simulation settings and analysis directives.</p>

<h4>Sample Spice Deck</h4>

```
* Spice Deck Example
* Comments start with an asterisk

* Circuit components
R1  N1  N2  10k   ; Resistor R1 from node N1 to N2 with a value of 10k ohms
C1  N2  N3  1n    ; Capacitor C1 from node N2 to N3 with a value of 1 nanofarad
V1  N1  0   DC 5V ; DC voltage source V1 from node N1 to ground (0) with 5 volts

* Transistors and other components can also be defined here

* Simulation settings
.TRAN  0.1ms  10ms ; Transient analysis from 0.1ms to 10ms
.DC    V1  0V  10V  1V ; DC sweep of voltage source V1 from 0V to 10V in 1V steps
.AC    DEC  100  1Hz  1MHz ; AC analysis from 1Hz to 1MHz with 100 points per decade

* Analysis directives
.PRINT  TRAN  V(N1) V(N2) ; Print the transient simulation results for nodes N1 and N2
.MEASURE  DC  V(N3) WHEN V(N2)=3V ; Measure voltage at node N3 when V(N2) reaches 3V

```
<h4>CMOS SPICE deck steps</h4>
<div align = "center">
  <img src = "https://github.com/NiteshIIITB/Physical_Design/assets/140998787/28c828ad-348c-4fd5-96e3-2d10a7cd30bb">
</div>

<p><b>In above figure we have taken size of NMOS and PMOS as equal which is not the case in real cmos circuits.</b></p>

</details>

<h1>References</h1>
<ul>
  <li><a href ="https://github.com/kunalg123/">Kunal Ghosh Github(Mentor)</a></li>
</ul>

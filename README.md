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

<h1>References</h1>
<ul>
  <li><a href ="https://github.com/kunalg123/">Kunal Ghosh Github(Mentor)</a></li>
</ul>

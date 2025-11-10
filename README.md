Factory Automation Production Line - README
Project Overview
This project demonstrates a comprehensive automated production line simulation using Factory I/O connected to Siemens TIA Portal. The system simulates a complete manufacturing process with multiple stations that work together to produce finished products through coordinated automation and PLC logic.
Project Details
Course: Automation – Major Task (MTC 313)  
Team: 8 members  
Primary Technologies: Factory I/O, Siemens TIA Portal, Ladder Diagram Programming, PLC (S7-314C)
System Architecture
The production line consists of four main operational stations working in sequence:
1. Feeding Unit
The entry point of the production line where raw materials are generated and distributed. Features include random material generation with color differentiation (green and blue) and a pick-and-place robot that feeds materials into the system.
2. Sorting Station
Materials are identified and classified based on color using a vision sensor. The system detects green materials and routes them to their designated machining center, while blue materials are transferred via pick-and-place mechanisms to their respective conveyors.
3. Machining Center
A CNC-based manufacturing station where lids and bases are produced from raw materials. Processing times vary by product type (lids: 6 seconds, bases: 3 seconds). An articulated robot manages material loading and unloading.
4. Assembly Unit
The final production stage where processed components are assembled. The station uses two pick-and-place machines and three clamps to ensure proper alignment and assembly of bases and lids into finished products.
Technical Components
Sensors Used:
⦁	Vision sensor (color detection)
⦁	Infrared (IR) sensors (material detection)
⦁	Limit switches (position feedback)
Actuators:
⦁	Pick-and-place robots
⦁	Conveyors (multiple sections)
⦁	CNC machines
⦁	Clamps and grippers
Control System:
⦁	PLC: Siemens S7-314C PN/DP
⦁	Programming Language: Ladder Diagram
⦁	HMI Device: TP_700 touchscreen for monitoring and control
Key Features
⦁	Modular Design: Four independent yet coordinated stations
⦁	Color-Based Routing: Automatic sorting and processing of different product types
⦁	Real-time Monitoring: HMI displays production status, component activity, and product counts for both green and blue product lines
⦁	Safety Controls: Start, Stop, and Emergency Stop buttons for operator control
⦁	Production Tracking: Counters for finished products by color type
Implementation Highlights
The system includes comprehensive PLC tagging with over 100+ defined tags managing sensor inputs, actuator outputs, and internal logic states. The ladder diagram logic orchestrates all station activities to ensure smooth workflow and minimal downtime.
The HMI window provides visual feedback on:
⦁	Station operational status (Feeding, Sorting, Machining, Assembly)
⦁	Product counts for green and blue production lines
⦁	Machine busy states
Results & Conclusion
⦁	Simulation tools significantly reduce design complexity and prototyping risks
⦁	Multiple logic solutions can achieve similar results; optimization depends on requirements
⦁	Proper coordination between stations ensures efficient material flow and product completion
⦁	The project demonstrates the effectiveness of PLC-based automation in managing complex production workflows
Team Members
⦁	Ahmed Ossama El-Sayed (18P8506)
⦁	Haidy Emad Samir Abouelnasr (18P4188)
⦁	Tasneem Mohamed Mansour (18P5892)
⦁	Arwa Ashraf Mahmoud Farag (1805479)
⦁	Mahmoud Magdy El-Asmar (18P8983)

# Shaft Split-Collar Design with NX and Simceneter Nastran
Let's design a 2 piece split-collar shaft clamp based on some input parameters to practice performing **Nonlinear Analysis** in Simcenter Nastran.

<img width="242" height="189" alt="image" src="https://github.com/user-attachments/assets/60c856c7-ac17-4c30-ad3e-7a4b04786d34" />
<img width="324" height="321" alt="image" src="https://github.com/user-attachments/assets/f6bfb7a1-2cc0-4591-b1a7-e16ddffffc84" />

Design inputs:
- shaft OD = 20mm  
- axial load = 9kN

# Preliminary Manual Calculations
We select materials for the bolts and collar halves and manually calculate the required **Bolt Size** and **Thread Engagement Length** based on the axial force to be resisted

<img width="957" height="1027" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/hand_calc.jpg" />

# 3D Design
Using the manual calculations as a basis for the design process in NX we create a geometry optimized for minimum weight, size and robustness. The design process is iterative and guided by simplified FEA

<img width="401" height="442" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/3d.jpg" />
<img width="610" height="742" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/prelim_fea.jpg" />

# FEA Verification of the Design
There are complex interactions present between the components of the assembly that are beyond (at least beyond mine 😅) capacity to calculate manually. Complex bending where the shaft gradually loses contact with the clamp (whose ID is larger due to tolerances, etc.),
change in the clamp geometry as the halves deformed due to applied bolt forces and more.
Perfect usecase for FEA! 

## Preload Application testing
Before we perform the actual analysis we'll test several ways of applying preload to bolts in Simcenter and choose the one that gives the best results for our case

<img width="1499" height="820" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/preloads0.gif" />

Out of the cases tested, using **1D Beam** elements with an **RBE2 spider** connection yielded results that most resemble the situation I'd expect from real-world parts

## Analysis Setup
The analysis will be performed using a Nonlinear Solution. First the bolts will be tightened to the calculated preload value and then the axial load will be applied to verify whether the collar can successfully resist the force

<img width="959" height="579" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/fea_setup0.jpg" />
<img width="851" height="593" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/fea_setup1.jpg" />
<img width="746" height="509" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/fea_setup2.jpg" />

## Results
We can observe the complex interactions between the RBE2 rigid elements and the simplified FEM. Guided by FEA textbooks information (best I could find!) we're able to extract only credible results and conclude that the created geometry meets the design criteria!

### Two steps of the analysis
<img width="1499" height="820" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/displacement0.gif" />

### Stress results
<img width="1499" height="820" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/stress0.jpg" />

# Parts Optimization
Looking at the results it's clear that it can be made much better. Let's optimize it (this is gonna be fun!).
We will design a collar, manufactured by Die Forging. The geometry will be optimized in terms of conformity to the manufacturing process requirements and we'll try to minimize the weight of the clamp.

## 3D Design
Collar components were designed according to best die forging process practices. Draft angles, generous radii, wall thickness and part thickness uniformity were optimized and subsequently validated through various tools available in NX ❤

<img width="972" height="396" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/forged_process_valid.jpg" />

The parts will be forged first and then CNC machined. I think this manufacturing process makes sense given the likely mass production character of the parts.

<img width="1087" height="746" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/forged3d_0.jpg" />
<img width="450" height="457" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/forged3d_1.jpg" />

A **reduction in total mass of ~35%** was achieved! ⚖

## FEA Analysis
An FEA akin to the initial one was performed. The geometry was simplified according to recommendation from FEA textbooks (also my PC is let's say...vintage 😥)

<img width="894" height="576" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/forged_fea0.jpg" />
<img width="745" height="586" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/forged_fea1.jpg" />
<img width="689" height="570" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/forged_fea2.jpg" />

## Results
The results indicate similar strength despite the significant mass reduction! 🏆

<img width="684" height="766" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/forged_displacement.jpg" />
<img width="1499" height="820" alt="image" src="https://github.com/mgrzb451/Project-Shaft_Split_Collar_Design/blob/main/assets/forged_displacements.gif" />

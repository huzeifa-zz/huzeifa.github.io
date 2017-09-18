---
layout: post
title:  "Simulating a Constant Current Source Circuit using Qucs"
date: 2017-08-27
categories: circuits
---

Circuit simulation is a very important skill to acquire since it aids in verifying circuit designs and helps you to master ciruit analysis.

In this post, I will show you how to use Qucs to perform a circuit simulation of a simple current source circuit employing a bipolar junction transistor (BJT) and diodes.
This guide, however, doesn't attempt to explain how the circuit works, but rather it is aimed at demonstrating how to simulate it using Qucs. The objective of the simulation is to measure the current supplied by the current source and to verify that the current supplied is constant over a given voltage range.

## What is Qucs?
Qucs is an opensource circuit simulation software with a graphical user interface. It can be used to perform several types of simulations such as DC, AC, S-parameter, Harmonic Balance analysis, noise analysis and transient analysis. Qucs provides all the standard lumped components together with many semiconductor based devices and models such as opamps, diodes, MOSFETs, PMOSFETs and many more. In addition, digital simulation can also be performed in Qucs.

## Installing Qucs
Qucs is fairly easy to install and is available on all major Linux based operating systems such as Fedora, Ubuntu, Arch Linux, etc. Qucs is also available on Windows and Mac OS. Please visit the link below to learn more about obtaining Qucs for your preferred Linux based OS.

[Download Qucs](http://qucs.sourceforge.net/download.html) 

Ubuntu users should do a simple ```sudo apt-get install qucs```, and Fedora users should punch in ```sudo dnf install qucs```.

Once Qucs has been successfully installed on your machine, launch it using the OS program menu or simply type qucs in the terminal and hit Enter.

## Exploring the Qucs Environment
Qucs is easy to use once you have a firm grasp of its interface. I suggest you take a few minutes to explore the interface in order to familiarize yourself with the program. You can obtain a description of an icon or menu by simply hovering the mouse pointer over it.

![Screenshot of Qucs main window](/images/constant-current source/2017-08-28-081520_1366x768_scrot.jpg) 

For this tutorial, I have briefly outlined the key things you need to know about the interface.

1. The dotted off-white area on the right is the work area. This is where the circuits to be simulated are constructed and diagrams such as graphs and tables are placed.

2. The `Dock Window` on the left, consisting of vertical tabs helps you to easily access your projects, see the contents of your simulation and select components for placing in the work area.

3. The toolbar on top is useful, as it readily provides you with the function of wiring, manipulating components and executing simulations.

4. To add a component in the work area, click on the `Components` tab availabe in the dock window. Choose the category of the component you require from the dropdown box. Resistors, capacitors and inductors are located under lumped components, semiconductor devices are available under non-linear devices etc. Select the desired component from the list and drag the pointer to the work area. At this point you will notice that the component symbol is accompanied with your mouse pointer. The orientation of the component can be altered by right clicking. Finally, left click to place the component in the work area. You will observe that the component symbol is still attached to the pointer implying that you can place another one. Press `ESC` or click the pointer icon in the toolbar to deactivate the placing of the component.

5. To change the properties of the component, select it, right click and choose `Edit Properties` from the menu. A dialog box pops up, from which you can edit the name and parameters of the component. You can also decide which parameters of the component to display in the schematic. This is achieved by selecting the parameter from the properties section and checking or un-checking the `display in schematic` option.

6. A Wire is used to connect one component to the other. It can be added from the `Insert` menu or the toolbar. A useful tip when wiring: to make a corner, simply right click.

7. It is important to make sure that your circuit is grounded properly or otherwise the simulation will not work as intended. The `Ground` port is availabe in the toolbar or from the `Insert` menu.

8. To perform the simulation, it is imperative to have a simulation block placed in your schematic. It is available in the `Components` tab under the `simulations` category.
For this tutorial we will be using the `dc simulation` block.

9. It is also a good idea to know the keyboard shortcuts for performing various tasks as they save time. The shortcut to each task is available from the menubar; it is indicated beside the menu item for that particular task.

That's it folks, and you are ready to make your first simulation.

## Constructing the Circuit
The end result of the constructed circuit is shown below.

![Final circuit](/images/constant-current source/final-circuit.png)

The assembly of the circuit is an exercise left to perform on your own using the descriptions given above. I have included some notes incase if you get stuck.

* As indicated previusly, the resistor is found under the `lumped components` category. To change its value, refer to point no. 5 of the above section. Alternatively, you can change it directly from the work area by double-clicking on the predefined value and replacing it with your desired value. It is okay to omit the units. 

* The npn transistor and the diode are located under `non-linear components`.

* The voltage source is obtained from the `sources` category.

* The ammeter measures the current flowing between the positive terminal of the voltage source and the collector of the transistor. This is where the load is supposed to be placed. It is found under `probes` as `Current Probe`. Ensure that the ammeter is positioned correctly, that is, the arrow should be pointing away from the voltage source. This can be achieved by simply right-clicking prior to placing it, or by using the rotate tool from the toolbar.

* Lastly, don't forget to place the `dc simulation` block. And of-course **save** your work

Once you have completed the circuit construction, press `F2` to execute the simulation.

## Performing the Simulation
Nothing happens at this point except a new data display page opens up. This is because we haven't yet configured the simulation to provide us with data.

One of the main aim of the simulation is to measure the current flowing between the collector of the transistor and the positive terminal of the voltage source. That is why we have placed a current probe between them.

For us to obtain the value of this current we need to add a `diagram` in the new data display page (You can also place it in the schematics page). There are several types of diagrams available such as Cartesian, Polar, Tabular, Smith Chart, etc.  Since we only need one discrete reading, the diagram of choice will be `Tabular`. In the `Components` tab, from the dropdown box, select `diagrams` and from the list choose `Tabular`. Drag the pointer to the page, and left click. Automatically a dialog box will popup prompting you to select the reading you would like to display. Illustrated below is the `Edit Diagram Properties` dialog box.

![Edit Diagram Properties Box](/images/constant-current source/2017-08-31-113153_627x537_scrot.png) 

Our main area of concern is the Dataset section. It consists of a dropdown box, for selecting the dataset from which you want to display the values and, a table listing the available readings to display. In our case, we will be having `V1.I` and `Pr1.I`. Notice the naming pattern. The characters before the dot represent the name of the component from which we want to extract data;  in our case the `V1` for voltage source and `Pr1` for current probe. The letter after the dot determines whether it is a voltage reading (V) or a current reading (I). Since we require the reading from the currrent probe, double-click on the `Pr1.I` entry. Consequently, the Graph section will be populated with `Pr1.I` entry. Click on `Apply` followed by `OK`. There you go! A table with the reading from the current probe will be displayed under the column heading `Pr1.I`. The current is measured in Amps. A screenshot of the table is shown below.

![Screenshot of table with current reading](/images/constant-current source/2017-08-31-113802_369x257_scrot.png) 

This circuit was designed to drive an LED, therefore a current of 22.2mA is registered. You can experiment with the circuit by changing the value of the `R2` resistor and re-simulating to observe the new value of the current reading.

Another cool thing you can do is calculating the `DC bias`. This will display the potential at each node in the circuit and the current reading on the probes. This is achieved by either pressing `F8` or selecting the `Simulation` menu from the menu bar and choosing `Calculate DC bias`.
The outcome is illustrated below.

![Calculate DC bias](/images/constant-current source/2017-08-31-121407_345x430_scrot.png) 

Congratulations! You can now obtain meaningful data from the simulation exercise.

## Going a Step Further
We also need to verify whether the current flowing is constant regardless of the voltage source value, that is, there shouldn't be a significant variation in current when we alter the voltage source value from, let's say, 5V to 15V. To accomplish this, we need to employ the `Parameter sweep` simulation. We will measure the current flowing for the following voltage range: 5 - 15V. Kindly follow the steps below to perfom the parameter sweep simulation.

1. Insert the `Parameter sweep` simulation block in the schematics page.

2. Double-click on the block to activate the properties dialog box.

3. Edit the properties as follows:

	+ **Simulation**: DC1
	+ **Sweep Parameter**: Vs
	+ **Type**: linear
	+ **Start**: 5V
	+ **Stop**: 15V
	+ **Step**: 1
	
	Click on `Apply`, then select `OK`. The above configuration is illustrated below:
	
	![Parameter sweep configuration](/images/constant-current source/2017-09-04-212716_442x379_scrot.png)

4. Double-click on the voltage source and replace the existing value of the voltage source to Vs. This makes a reference to the Sweep Parameter defined earlier. Click on Apply and OK. This is shown in the image below:

	![Edit voltage source value to Vs](/images/constant-current source/2017-09-04-212851_410x348_scrot.png)
 
5. We will represent the data graphically on a Cartesian diagram and we will be expecting a horizontal line, implying that current is constant over the voltage range specified. To construct the graph, follow the steps outlined below:

	* In the data display page, insert the `Cartesian` diagram and embrace yourself for the properties box.
	* In the `Data` tab, from the `Dataset` area, double-click on the `Pr1.I` entry. This activates the `Graph Input` section that gives you the option to choose the line color, style, thickness and position of y-axis (left or right). Make the selections as you wish and proceed to the `Properties` tab.
	* In the `Properties` tab, give appropriate labels to the x-axis and the left/right axis (this depends on the selection you made in the `Data` tab). At the bottom, you can also choose to show or not to show the grid, choose grid color, style and type (logarithmic). Switch to the `Limits` tab for the final configuration. 
	* Our area of concern will be the `left Axis` (or right). In that section, check the `manual` checkbox and edit the start, step and stop values as follows:	
		+ **start**: 0.01
		+ **step**: 0.01
		+ **stop**: 0.04
		
	* Click on `Apply` and `OK`. 
	
	The above series of steps are illustrated below:
	
	*Data tab*
	
	![Cartesian diagram properties, Data tab](/images/constant-current source/2017-09-04-212925_687x537_scrot.png)

	*Properties tab*
	
	![Cartesian diagram properties, Properties tab](/images/constant-current source/2017-09-04-213024_687x537_scrot.png)

	*Limits Tab*
	
	![Cartesian diagram properties, Limits tab](/images/constant-current source/2017-09-04-213052_687x537_scrot.png)

The graph and the final schematic (notice the addition of a LED as load) are shown below:

*The graph*

![Current against voltage graph](/images/constant-current source/2017-09-04-213125_741x510_scrot.png)

*The final schematic*

![The final schematic](/images/constant-current source/2017-09-04-213207_505x361_scrot.png)

The graph illustrates the change in current over the specified voltage range. It is fairly horizontal, and there is a minute change of 2mA between 5 and 15 volts. Although, for some applications, this change may be significant and thus a circuit with an improved accuracy is needed.

Bravo! You have successfully performed a parameter sweep simulation and displayed the results graphically on a cartesian diagram.

## Conclusion
This post was aimed at giving you a brief overview of the Qucs interface, showing you how to conduct circuit simulations in order to obtain measurements and, use them to verify the intended purpose of the circuit.

## References
+ [Qucs project](http://qucs.sourceforge.net/index.html)  
+ [Simple Led Driver/Constant-current Source 20 MA](http://www.instructables.com/id/Simple-Led-driverConstant-current-source-20-mA/) 
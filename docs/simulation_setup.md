## General setup

The 24h simulation currently contains routes for passenger vehicles, heavy-vehicle traffic as well as bicycles. Both vehicle demand as well as traffic light settings are created from data for Wednesday the 16.09.2020 to create a weekday traffic situation mostly uninfluenced by covid-restrictions. All traffic demand is based on origin-destination matrices created from mobility data from the city of Ingolstadt and Germany. Motorized traffic demand is further enhanced based on induction loop counts at all traffic lights in the city. The traffic counts provided by the city of Ingolstadt can be obtained upon request via the [open data portal](https://www.ingolstadt.de/Service/Weitere-Themen/Open-Data/).

More details on the simulation setup is provided in the publications listed in the README.


## Defined parameters

The simulation step length is set to 0.25s. The re-routing probability is set to 0.2 to allow re-routing of vehicles in dense traffic. The ignore-junction-blocker value was set to 15s to prevent unrealistic junction blocking in dense traffic. Furthermore, passenger vehicles will drive up to 1.8s after a traffic light turns yellow. This value was calculated from real-world vehicle trajectories in Ingolstadt. The traffic lights in the simulation are controlled by fixed-time programs. Since the real-world traffic lights in Ingolstadt are traffic acutated, the simulated traffic light programs are created for each hour of the simualtion individually. The average green time assigned to each maneuver in the simulation results from the average green time recorded in reality which again is influenced by the traffic demand. While this means the traffic lights will not react to the individual traffic in the simulation, the length of the green phases will vary throughout the day dependent on the real-world traffic demand.

Details on the calibration procedure were published at the 2021 SUMO Conference.


## Next steps:

* Include public transport
* Improvement of bicycle simulation based on cycling trajectory data

Feel free to contact us e.g. by creating an [issue](https://github.com/TUM-VT/sumo_ingolstadt/issues) in the repository regarding questions or improvements to the simulation.


## Known issues:

* The sumo-gui will warn you that traffic light phases are unused or missing - this currently does not affect simulation performance. 
* Vehicles will sometimes block each other on parking lots, but this resolves eventually.
* Traffic light programs must be added to the .net.xml simulation map in order to work with the WAUT (Wochenschaltautomatik) file. Because of this, there might be multiple simulation networks files provided with equal geometric properties for different simulated days.
* 4 green phases had to be extended manually in comparison to the real-world data to deal with the traffic demand.
* The simulation could not be validated with other data except for the inputs used for calibration. A comparison of the simulation to real-world vehicle data was presented at IEEE ITSC 2021.

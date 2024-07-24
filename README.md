This is just a repository that documents my learning and findings/work on the topic of car hacking. The findings/work/notes have been copied and pasted into here from my desktop.

Mid-semester 1 break project: Custom guage interface for my 1994 Toyota Celica

Motivation: Wanting to create modifications for my car involving custom guages, potentially a digital interface that flips between oil temp, coolant temp, oil pressure, etc. Studying the car ECU seemed like the first step in communication with the ECU to gather the relevant information.

I started with reading relevant chapters from "The Car Hacker's Handbook" and documented my notes in: handbook_notes.md

Link to handbook:
- https://archive.org/details/thecarhackershandbook/page/n27/mode/2up

I then found a 3 part article on exploiting CAN-Bus using linux-based tools, to which I followed along and experimented with on my own.

Link to articles:
- https://medium.com/@yogeshojha/car-hacking-101-practical-guide-to-exploiting-can-bus-using-instrument-cluster-simulator-part-i-cd88d3eb4a53
- https://medium.com/@yogeshojha/car-hacking-101-practical-guide-to-exploiting-can-bus-using-instrument-cluster-simulator-part-ee998570758
- https://medium.com/@yogeshojha/car-hacking-101-practical-guide-to-exploiting-can-bus-using-instrument-cluster-simulator-part-ea40c05c49cd

Progress/observations Log:
- Setting up the environment was simple despite ubuntu taking a while to download.
- The amount of CAN packages being commuincated on the bus was unbelievable even if it was just a simulation, no wonder that it was mentioned that bluetooth obd2 scanners will miss packages. 
- 



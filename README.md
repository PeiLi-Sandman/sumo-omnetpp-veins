One of the hard parts for this project is the installation of omnetpp and sumo. 

# SUMO

Since veins requires a quitely old sumo version, we cannot directly use 'sudo apt-get sumo' to install it. I have checked this [Youtube video](https://www.youtube.com/watch?v=yVEthJz9hLc) for the installation of any versions sumo. 

Specifically, the installation for sumo (Ubuntu System) has following steps:

  * Download sumo from this [Link](https://sourceforge.net/projects/sumo/files/sumo/). For example, I use 'sumo-src-0.32.0.tar.gz' here
  * Extract the sumo installation file.
  * CD to the extracted file.
  * In the command line, type:
      * sudo apt install build-essential autoconf automake libxmu-dev libfox-1.6-dev libproj-dev libxerces-c-dev libxerces-c3.2 libgdal-dev default-jdk 
      * ./configure
      * make
      * sudo make install

Now you can test whether you have installed sumo successfully, just type 'sumo-gui' in the command line.

Moreover, remember to add sumo in you path, in the command line:
  * Type 'gedit ~/.barshc'
  * Add ' export SUMO_HOME="/Yourpath/sumo-0.32.0" ' to the end of the file. DO NOT change any other things of this file!
  * reboot or type 'source ~/.barshc'

How to create a simulation map and generate vehicles:
* Download a OSM file of the selected area from openstreetmap.org
* Open your terminal
* Convert the OSM file to a sumo network file (XXX.net.xml) using this command:
  * netconvert --osm-files XXX.osm -o XXX.net.xml --junctions.join --tls.guess-signals --tls.discard-simple --tls.join
* Import polygons from OSM data and produce a sumo-polygon file using this command:
  * polyconvert --net-file XXX.net.xml --osm-files XXX.osm --type-file typemap.xml -o XXX.poly.xml
* Generate vehicle traffic demand using this command, 'randomeTrips.py' can be found on 'sumo/tools' 
  * python XXX/sumo/tools/randomTrips.py --n XXX.net.xml -r cars.rou.xml -t "type=\"car\" departSpeed=\"max\" departLane=\"best\" -c passenger --additional-files car.add.xml -p 1.4 e 1000 -l

# OMNETPP

Although there are many videos or blogs about the installation of it, I strongly suggest you take a look at the [official mannual](https://doc.omnetpp.org/omnetpp/InstallGuide.pdf) of omnetpp, it will make you life become much more easier.

# VEINS

The installation of veins is quite simple, just download it from its officail [site](https://veins.car2x.org/tutorial/).

# BUILD CONNECTION

After you got sumo, omnetpp and veins, you can try fisrt to run the example provided by veins. Take a look at this [Youtube video](https://www.youtube.com/watch?v=a6te888H7IM&t=431s), it is really helpful

# Try you own project

Another exciting thing is to build a network for your own, the process is quite simple. Please check this [Youtube video](https://www.youtube.com/watch?v=Mh4WnY4KY4Y&list=WL&index=24&t=0s).

By the way, all the information I provided here are built based on other people's efforts. I just summarize them together based on my understanding.

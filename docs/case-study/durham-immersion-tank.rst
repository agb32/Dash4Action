Durham Immersion Tank case study
=====
.. _abstract:

Abstract
------------
Immersion tank cooling offers a more efficient alternative to traditional air-cooling or direct-to-chip liquid cooling, but requires a new approach to server installation and maintenance.  In order to test and gain experience with immersion cooling systems, Durham University installed a single immersion tank in the COSMA supercomputer datacentre.  Part of the internal COSMA5 cluster, and the Durham Hardware Lab, were installed in the tank.

Introduction
------------
Cooling accounts for a significant portion of the power usage of an HPC facility, often quoted at 30-50% of total energy consumption.  Given the method of cooling generally has no impact on computational output, any reduction in cooling energy expenditure can be considered an increase in overall datacentre efficiency.
Immersion cooling, in which an entire rack of servers is immersed in a dielectric liquid, greatly reduces the amount of heat lost to the surrounding environment compared with air cooling, by keeping the cooling medium in a closed system.  Moreover, every component in the server is directly cooled, unlike in a direct-to-chip cooling system, where only the processors are targeted.

Method
------------

In May 2025, a 50U MIDAS immersion cooling tank was installed in the COSMA datacentre.
COSMA5, a small 8-node cluster used internally by Durham University, was split such that 3 nodes remained in a traditional air-cooled rack, and 5 nodes were placed inside the immersion tank.  The existing hardware was retrofitted for use inside the tank, as any fans or moving parts had to be removed.
Specialised immersion-approved infiniband cables were used to connect the nodes to the main network, and regular ethernet cables were used for the management network.
In 2026, purpose-built compute nodes were loaned to Durham University by Vespertec to test in the immersion tank.

Result
------------

In the time that the immersion tank has been operational, no overheating incidents have taken place, and node temperatures have remained stable.

Hardware failure rates do not appear to have increased, however the plastic casing around cables has notably degraded.

Lessons Learned
------------

Purpose-built hardware proved to be much more easily manoeuvred and serviced than retrofitted hardware.  
Some vendors, nVidia in particular, don’t officially offer warranties for immersed hardware.  In these cases a 3rd party must be involved in order to ensure hardware failures are covered.
Immersion tanks must be lain horizontally, taking up more space on the datacentre floor than a traditional vertial rack.  For sites with limited floor space this may be challenging, and would require significant planning.

Sustainability Impacts
------------

Immersion cooling increases the overall efficiency of a datacentre cooling system, thus reducing the total power requirement of the datacentre.  For sites in regions where grid carbon intensity is high, any reduction in overall power draw would result in a decreased carbon production.

Servers designed for immersion cooling require fewer parts, such as fans and cooling pipes, which reduces the overall embodied carbon in manufacturing such servers.  However, it would be best to avoid producing brand new hardware when retrofitting is an option.  This means teams must balance overall practicality with sustainability.

As immersion tanks naturally heat the liquid to around 40 degrees celcius, waste heat re-use may be a viable option for sites with the necessary infrastructure.

Conclusions
------------

Immersion cooling offers promising energy efficiency improvements over air cooling and direct-to-chip cooling, but requires a radical change in how datacentres are managed.  Datacentre layouts must change to accomodate the larger footprint of tanks, and employees must learn to carry out maintenance in a new way.
Additional time must be factored in for maintenance tasks, accounting for hoisting the servers out of the tank, and cleaning any spilt oil afterwards.
As the technology becomes more widely adopted, it is likely new tools and techniques will be developed in order to better streamline this process.

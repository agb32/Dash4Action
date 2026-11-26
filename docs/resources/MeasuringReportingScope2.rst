Measuring and Reporting Scope 2
===============================

Having produced an estimated baseline carbon assessment a system for
regular carbon reporting will be needed. Automating this will reduce the
time needed to compile reports and enable staff time to be employed more
productively on other carbon reduction tasks!

Energy Monitoring
----

To calculate the Scope 2 emissions attributable to your facility you
will need to know the electricity usage. When we measure electricity
usage there are two things people measure: power and energy. Power is
the rate of flow of energy typically measured as kW, while energy is
typically measured in kWh, but sometimes the more scientific unit of
joules (J) is used.

Within a DRI facility it is often possible to measure energy usage at
different levels. Each level will have a different level of granularity
and accuracy.

Facility Level
~~~~

This is the least granular level measuring energy usage for the whole
facility. The electricity meters used for billing purposes and their
sub-meters are likely already monitored by Estates departments and can
give Facility level readings. These meters are accurate enough for
billing purposes and can be considered to be highly accurate.

Circuit Level/Room Level/Cooling Level
~~~~

These are more granular, more specific, sub-meters which can track
electricity usage of specific circuits for example computer rooms and
cooling plant circuits. These are likely already monitored by Estates
departments and again can be considered to be highly accurate.

Rack Level
~~~~

This is the level where dRTP’s might traditionally start to take
readings. Smart UPS’s and intelligent PDU’s are often used at the rack
level to monitor energy usage and power draw. These are typically less
accurate than the Facility and Circuit level readings but can still be
considered to have good accuracy, perhaps reading around 5% lower than
at the more accurate circuit level.

Server Level
~~~~

Some iPDU’s have per-port monitoring and so can be used to monitor
individual servers’ energy usage to good accuracy. However more
typically servers will have a Baseboard Management controller (BMC)
which can monitor energy and power usage with fair accuracy. The
measurements by the BMC can typically be read out with the IPMI and
redfish protocols. BMC energy measurements seem to be model and
manufacturer specific: readings can be from 5% to 20% below those at the
rack level possibly as a result of losses in the power supplies and
other model specific design choices.

User Level
~~~~

CPU’s such as Intel and AMD have *Running Average Power Limit* (RAPL)
counters. These RAPL counters/registers can be read out to give
estimates of power and energy used by the CPU and sometimes the RAM of a
system. Clearly this ignores a number of major components of a system
but the readings have been shown to broadly correlate with system power
usage[1] but with a significant offset. This gives some rough level
energy measurement which is more easily accessible to the operating
system and thus to the end user.

Recommendations for Energy Monitoring
~~~~

As has been shown, accurate measurements of energy usage can be made at
the facility and circuit level, and with good accuracy at rack level
also[2,3]. Moving to finer granularity than rack level energy readings
requires correction factors to improve accuracy[3].

Rather than relying on uncalibrated server-level telemetry for absolute
energy figures, and given the declining accuracy from circuit level and
rack-level down to server and user levels[1,3], then a more robust
approach is to treat facility or circuit level totals as the
authoritative figure and apportion that energy across nodes using the
finer-grained readings as relative weights[2,4].

Power Usage Effectiveness (PUE) is a derived value not a fundamental constant
~~~~

It may be tempting to sum up your Server Level or Rack Level
measurements and multiply by PUE to obtain your total facility energy
usage. However we must remember that PUE is a derived measurement. A
more accurate facility energy measurement may be directly available.
Likewise circuit level measurements of energy into the IT equipment and
energy into the cooling equipment may be directly available. This will
allow calculation of PUE as a derived measurement, and will also allow
this derided PUE to be tracked across time showing temporal variations
of PUE with weather, season and in some cases night at day.

Conversion to Scope 2 Carbon
----

To calculate Scope 2 carbon you will need to know the energy in kWh and
multiply that by the Carbon Intensity conversion factor. There are
basically three carbon intensities you could choose to use: National,
Regional and Market. It is recommended to report using all three as they
show different things.

UK National Carbon Intensity
~~~~

The UK government Department for Energy Security and Net Zero (DESNZ)
publishes an annual average carbon intensity for the UK Grid [5] which
should be used for statutory carbon reporting and forms a good initial
basis for informal reporting. This avoids a “postcode lottery” and
treats different geographical locations the same.

Under the international Greenhouse Gas Protocol using this UK National
Average Carbon intensity yields a Location-Based Scope 2 footprint. In
international terms our location is the UK, and this should not be
confused with the UK electricity regions discussed next.

Although the UK has one synchronised national grid for electricity that
grid comprises regions which are interconnected with power limited
links.

UK Regional Carbon Intensity
~~~~

As links between UK electricity grid regions have maximum power transfer
capacities, then it is possible to calculate a different carbon
intensity for each region.

These regional carbon intensities take account of the carbon intensity
from generators supplying the regional electricity network and the
carbon intensity of any imported electricity from a neighboring region.
Regions of the country with more wind and solar generation have a lower
carbon intensity than those with more fossil fuel generation.

Using this regional carbon intensity to calculate carbon foot print,
after accounting for any on-site generation, is arguably the best
measure of true scope 2 carbon emissions due to your electricity use.

Regional carbon intensities can be obtained from the National Energy
System Operator (NESO). NESO publishes real-time and forecast data 6] as
well as historical data [7].

For UK collaborations using pan-european computing resources, WattNet
calculates regional carbon intensities and water usage factors across
many countries in Europe [8]. However the methodologies may differ from
the other data sources listed here and so should be used with care where
non-statutory pan-european analysis is needed.

Market Based Carbon Intensity
~~~~

When agreeing your electricity supply contract it is possible to
purchase electricity that is backed by RIGO certificates (Renewable
Energy Guarantees of Origin) certifying 1MW of renewable energy per
RIGO. Your supplier will provide you with a zero or near-zero carbon
intensity to use based on the exact nature of the contract

Using this supplier provided carbon intensity yields a market based
scope 2 footprint which is internationally recognised but should be
reported alongside the internationally recognised location-based
footprint.

We would recommend you also report the regional based footprint for
completeness as this is arguably the most representative of reality.

Energy Supply Contracts
~~~~~~~~~~~~~~~~~~~~~~~

Negotiating energy supply contracts often falls to Estates and
Purchasing departments. Computing/HPC departments should approach their
Estates and Purchasing departments to get details of their electricity
tariff and any associated market based carbon intensity. Directly
contacting suppliers or purchasing consortia is strongly discouraged:
find out who in your Estates or Purchasing department can help instead.

| Estates and Procurement are probably leveraging national agreements
  negotiated by University and Government purchasing consortia.
| The UK Government and UKRI can leverage Government Commercial Agency
  (GCA) frameworks RM6251 and RM6390.
| UK Universities can leverage The Energy Consortium(TEC)’s frameworks
  agreements.

Conclusions
----

Where only RAPL and BMC/IPMI/redfish energy measurements are available
some effort to implement rack or circuit level measurement would avoid
under-reporting energy usage and thus scope 2 carbon.

Calculating a time varying PUE, if is it needed, from circuit level
measurements is preferred to using a constant design document PUE.

The Greenhouse Gas protocol says you must report National level
“Location based” footprint alongside “Market based” footprint. We would
also recommend reporting Regional based footprint using NESO regional
carbon intensities, correcting for on-site generation where required.

Contact your Estates and Purchasing departments to obtain information
from Energy suppliers in the first instance.

References
----

| [1] “RAPL in Action: Experiences in Using RAPL for Power Measurements”
  K.N. Khan, M. Hirki, T. Niemi, J.K. Nurminen, Z. Ou, March 2018. ACM
  (TOMPECS), Volume 3, Issue 2, Article 9, Pages 1 - 26.
| https://doi.org/10.1145/3177754

[2] “IRIS-CMP Final Report” Owen, R. A., & Li, D. (2024). IRIS Carbon
Mapping Project: Final Report and Outline Delivery Roadmap.Zenodo.
https://doi.org/10.5281/zenodo.10966001

[3] “Measuring Carbon NetZero and the IRISCAST Project.” Owen, R. A., &
Hays, J. (2024). EPJ Web of Conferences, 295, 07029.
https://doi.org/10.1051/epjconf/202429507029

[4] “Allocating Carbon Costs to Computing Payloads across Heterogeneous
Infrastructures.” Owen, R. A., Li, D., Traynor, D., et al. (2025). EPJ
Web of Conferences, 337, 01202.
https://doi.org/10.1051/epjconf/202533701202

[5] “Greenhouse gas reporting: conversion factors 2025,” Department for
Energy Security and Net Zero (DESNZ), UK Government, July. 2026.
https://www.gov.uk/government/collections/government-conversion-factors-for-company-reporting

[6] NESO Realtime Data: https://carbonintensity.org.uk/

[7] NESO Data Archive: https://www.neso.energy/data-portal

[8] Wattnet: https://wattnet.eu/

Baseline Assessment
===================

The Baseline assessment is not intended to be a highly accurate measure
but simply an initial estimate to see the scale of the problem and focus
future work.

This document introduces the concept of carbon emission scopes and how
using official/respected conversion factors we can estimate carbon
emissions at all three scopes from other values we can measure/obtain
directly.

Carbon Emission Frameworks
==========================

| Carbon emissions can be classified into a number of categories.
| Simplistically Operational Carbon and Embodied Carbon.

In the Digital Research Infrastructure (DRI) context embodied carbon
emissions are those due to the raw material extraction, fabrication,
manufacturing, delivery, and eventual disposal or decommissioning of
DRI. Essentially the emissions due to the DRI existing before it is
switched on. The operational carbon emissions in contrast are the
emissions that are due to the DRI being operated and maintained in its
active life which is primarily the emissions due to the electricity
powering the DRI.

| A more sophisticated and universally recognised classification
  framework is provided by the Greenhouse Gas Protocol (GHG Protocol)
  [1]:
| Scope 1 emissions are direct GHG emissions: in the DRI context
  emissions from gas boilers to heat DRI staff office space, any
  emergency diesel or gas generators’ emissions. Any fugitive emissions
  such as coolant leaks from air conditioning systems.

Scope 2 emissions are indirect emissions from purchased energy. In the
DRI context these are emissions due purchased electricity. With a
knowledge of the Grid Carbon Intensity factor you can simply multiply
this factor by your electricity usage to get your scope 2 emissions.
Grid Carbon Intensity is discussed in more detail below.

| Scope 3 emissions are indirect value chain emissions. These indirect
  emissions are split into 15 categories grouped as follows:
| **Upstream:** Purchased Goods & Services; Capital Goods;Fuel- &
  Energy-Related Activities; Upstream Transportation & Distribution;
  Waste Generated in Operations; Business Travel; Employee Commuting;
  Upstream Leased Assets.

**Downstream:** Downstream Transportation & Distribution; Processing of
Sold Products; Use Phase of Sold Products; End-of-Life Treatment of Sold
Products; Downstream Leased Assets; Franchises; Investments.

Not all of these are relevant in a DRI context but more are than you
might expect!

UK Government GHG Conversion Factors for Company Reporting
==========================================================

The UK Government Department for Energy Security and Net Zero (DESNZ)
publishes a spreadsheet of conversion factors[2] which should be used
for statutory carbon reporting and more broadly as a useful reference of
conversion factors within the UK.

Grid Carbon Intensity factors
=============================

| The Grid Carbon Intensity is a conversion factor between kWh and
  kgCO2e. For the baseline assessment it is sufficient to use DESNZ
  published factor [2] which gives a national annual average carbon
  intensity.
| The National Energy System Operator (NESO) provides historical and
  forecast carbon intensities at national and regional level via
  dashboards[3] and documented[4] api’s [5] which may be useful when
  moving beyond the baseline assessment.

Higher Education Supply Chain Emission Tool (HESCET)
====================================================

The British Universities Finance Directors Group (BUFDG) has created a
tool in the form of a spreadsheet that estimates scope 3 carbon
emissions based on the cost of equipment purchased[6][7]. There may well
be more accurate ways to estimate scope 3 emissions but for a baseline
estimate this tool is probably sufficient.

HESCET download is access controlled so for most UK university staff
contacting your finance team and asking for a copy of the latest HESCET
spreadsheet is probably the easiest way to obtain the tool. Direct
access can be gained by registering as a member of BUFDG.

Baseline Framework
==================

For the baseline assessment it is probably sufficient to calculate
operational carbon emissions and embodied carbon emissions as rough
proxies for Scope 2 and Scope 3 emissions. If your site has gas or
diesel generators then you may also want to calculate Scope 1 emissions.

Scope 1 Estimate
----------------

For the baseline assessment for a DRI we should focus on fossil fuel
backup generators.

We can estimate the scope 1 emissions from either the litres of fuel
burned (most accurate) or the kWh of electricity generated (less
accurate)

Obtain the litres of fuel burned in the reporting period directly from
gauges or purchase receipts or estimated from generator run hours and
generator datasheet fuel consumption figures. Then lookup the correct
conversion factor in the DENEZ spreadsheet [2] which will likely be the
“Diesel (average biofuel blend)” on the Fuel sheet. In 2026 the
conversion factor tabulated was 2.58354 kg CO2e per litre of Diesel
(average biofuel blend). The product of this factor and the litres of
Diesel used will give your scope 1 generator emissions.

If you are unable to obtain litres of fuel used but do know how much
electricity was generated then the “kWh (Net CV)” conversion factor for
Diesel (average biofuel blend) can be used in a similar way to calculate
your scope 1 generator emissions.

Scope 2 Estimate
----------------

The DENEZ spreadsheet [2] also has a Grid Carbon intensity factor for
statutory reporting. Thus to obtain your scope 2 emissions you can
simply multiply this DENEZ carbon intensity by the total electricity
usage of your DRI.

If you can obtain the relevant electricity meter readings for all
aspects of your DRI then it is simple. If you can only get readings for
your direct computer electricity usage then you will need to calculate
the total electricity usage using your data centres Power Usage
Effectiveness (PUE) figure.

If you cannot obtain figures from your Estates Department electricity
metres then consider what equipment in your rack wiring can supply power
or energy readings. Consider equipment like uninterruptible power
supplies (UPS’s) and intelligent Power Distribution Units (PDU’s) as
they can likely measure power/energy usage within 5% of the Estates
readings. Remember to apply PUE to obtain total electricity used.

If UPS/PDU readings are unavailable then consider readings from a
server’s Baseboard Management Controller (BMC) which can typically be
read out using SNMP, IPMI or Redfish protocols. However note that BMC
readings accuracy can vary between models and often do not account for
power supply losses etc, so can read ~20% below electricity meter
readings. If BMC data is all that is available consider adding a
correction factor as well as accounting for the PUE before applying the
carbon intensity.

Scope 3 Estimate
----------------

A proper analysis of scope 3 carbon emissions will require an inventory
of equipment within the DRI that records the embodied carbon of each
component and the planned component lifetime. This comprehensive
approach will be discussed later but for an initial baseline a simpler
approach is to use the HESCET tool to estimate Scope 3 emissions based
on financial cost. At the simplest level you can estimate the cost of
all your IT equipment as one figure and enter that into the HESCET tool
to obtain a Scope 3 estimate.

A more fine grained approach would involve preparing an inventory of kit
in your facility recording the cost of each component. The total cost
can then be used in the HESCET tool.

It is readily recognised that the accurate way to determine the scope 3
emissions of an item is to perform a Life Cycle Assessment (LCA).
Manufacturers are in a better position to conduct these than end
operators and so obtaining LCA data from manufacturers on scope 3
emissions is advisable as you purchase new kit. Any inventory you curate
for this initial baseline estimate can then be extended with LCA data
which can be used for better future scope 3 emissions estimates. This
will be discussed later.

Conclusion
==========

| This document sets out a basic introduction to categorisation of
  carbon emissions into scopes 1,2&3. It also sets out how to access the
  relevant tools and recognised conversion factors needed to estimate
  carbon emissions from figures that are measurable/obtainable.
| It is hoped that this will allow the reader to make scope 1,2&3
  emissions estimates for their own datacenter/DRI.

References
==========

[1] World Resources Institute and World Business Council for Sustainable
Development, “The Greenhouse Gas Protocol: A Corporate Accounting and
Reporting Standard,” rev. ed., WRI and WBCSD, Washington, DC, 2004.
[Online]. Available: https://ghgprotocol.org/corporate-standard

[2] Department for Energy Security and Net Zero (DESNZ), “Greenhouse gas
reporting: conversion factors 2025,” UK Government, London, UK, Tech.
Rep., July. 2026. [Online]. Available:
https://www.gov.uk/government/collections/government-conversion-factors-for-company-reporting

[3] https://dashboard.neso.energy/

[4]
https://carbon-intensity.github.io/api-definitions/#carbon-intensity-api-v2-0-0

[5] https://carbonintensity.org.uk/

[6] https://www.bufdg.ac.uk/search?search-control=HESCET

[7]
https://www.bufdg.ac.uk/resources/news/view?g=d2e49004-d155-46f7-a036-a5692846a965

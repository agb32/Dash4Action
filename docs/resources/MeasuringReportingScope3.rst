Measuring and Reporting Scope 3
===============================

In the Digital Research Infrastructure (DRI) context, Scope 3 emissions
are dominated by the embodied carbon of the infrastructure: the carbon
costs of manufacturing, transport, and end-of-life footprint of IT
hardware alongside the data centre building and mechanical/electrical
plant.

Under the GHG Protocol Corporate Accounting and Reporting Standard[1],
embodied emissions associated with purchased capital goods are normally
reported within organisational Scope 3 inventories in the reporting
period in which the goods are acquired. For organisational reporting
purposes these emissions are therefore typically recognised at or near
the point of purchase.

However, for user-facing DRI carbon accounting an alternative
amortisation approach is more useful to drive behavioural change.
Amortised embodied carbon allocations are a management accounting
approach and should not be confused with and cannot replace
organisational Scope 3 reporting under the GHG Protocol.

Gathering Embodied Carbon Data
----

Obtaining reliable embodied carbon figures for DRI hardware remains
challenging.

Firstly one can try to obtain Vendor Product Carbon Footprints (PCFs)
and Life Cycle Assessments (LCAs). Major OEMs such as Dell, HPE, and
Lenovo publish these for standard server configurations. These figures
have fairly large uncertainties [2, 3] and are based on particular
assumptions which should be understood, but remain the preferred source
of embodied carbon data.

An alternative approach, which may be used when PCF’s are not available,
is a component-level bottom-up LCA model: This can help to account for
non-standard server configurations. Component-based databases and tools
such as Boavizta [4] and the Architectural Carbon Modeling Tool (ACT)
[5] estimate total node embodied carbon by summing individual silicon
die areas (CPUs, GPUs), memory (DRAM), storage (NVMe/HDD), power
supplies, and chassis materials.

If neither of the above methods are possible then a spend-based emission
factor can be used as a fallback estimate. Converting capital
expenditure into kgCO2e using DESNZ/DEFRA EEIO factors [6] or HEPA /
UKUPC HESCET tool [7].

Apportionment and Job-Level Scope 3 Accounting
----

| While organisational GHG inventories record Scope 3 emissions in the
  year of purchase, we can take a more nuanced approach for DRI
  reporting to users.
| The apportioning of Scope 3 footprints to DRI services and individual
  jobs requires amortising embodied emissions over the expected
  operational lifetime of the assets. A server may have a 7 year life
  time while a building infrastructure may have >20 year lifetime while
  the building shell may last for over 50 years[2].

Thus it is essential to build an inventory of the component parts of the
DRI facility focusing on the significant items to start.

For each asset the inventory should include the purchase date, the best
estimate of embodied (Scope 3) carbon, the method used to derive that
estimate, and the intended operational lifetime. The carbon amortisation
rate for each component can then be calculated and summed to give the
facility’s total embodied carbon amortisation rate.

This facility-wide amortised embodied carbon can then be allocated to
user jobs based on reserved or allocated resource share and elapsed jobs
time. This reflects the fact that equipment ages over time. Facilities
should use the allocation basis most consistent with local scheduling
and charging models, provided the chosen method is applied consistently
and reconciles back to the facility-level amortised embodied carbon
total.

Alternative methods
----

There are of course slightly differing methods that can be used.

Bottom-up approaches such as Boavizta[4] and ACT[5] estimate embodied
carbon from the characteristics and composition of individual hardware
assets. These methods do not necessarily reconcile allocated emissions
against a facility-wide asset inventory. Conversely, IRIS-CMP enforces
top-down reconciliation against total facility assets, keeping embodied
carbon associated with idle or unallocated capacity transparently
visible rather than inflating active user figures [3].

The IRIS-CMP approach makes everything add up, but it is only as
accurate as the embodied carbon estimates that go into the inventory, be
they from vendor PCF’s or from component-level LCA models, as discussed
earlier.

Conclusions
----

Organisational Scope 3 reporting under the GHG Protocol records these
emissions at or near the point of purchase: which reflects the real
emission of carbon into the atmosphere during manufacture. However
management reporting to users on their share of the scope 3 emissions
may be amortised over the lifetime of the facility.

An inventory of all components in the facility, from buildings to
computers will be needed. The inventory must record the embodied carbon
and the component lifetime of each component from which the facility
embodied carbon amortisation rate can be calculated.

Reporting to users of their share of scope 3 emissions should be done by
apportionment based on reserved or allocated resource share and elapsed
time of a job and the facility embodied carbon amortisation rate. The
share of scope 3 not allocated to users can be allocated to the facility
operators such that idle infrastructure remains visible and motivates
operator behavior change.

References
----

[1] World Resources Institute (WRI) & World Business Council for
Sustainable Development (WBCSD). GHG Protocol Corporate Accounting and
Reporting Standard. Available at:
https://ghgprotocol.org/corporate-standard

[2] Juckes, M., et al. (2023). Sustainability in Digital Research
Infrastructure: UKRI Net Zero DRI Scoping Project Final Technical
Report. Zenodo. https://doi.org/10.5281/zenodo.8199984

[3] Owen, R. A., & Li, D. (2024). IRIS Carbon Mapping Project: Final
Report and Outline Delivery Roadmap. Zenodo.
https://doi.org/10.5281/zenodo.10966001

| [4] Thibault, S., et al. / Boavizta. (2023). BoaviztAPI: A Bottom-Up
  Model to Assess the Environmental Impacts of Cloud and On-Premise IT
  Infrastructure. Boavizta.
| https://boavizta.org/en

[5] Gupta, U., et al. (2022). ACT: Designing Sustainable Computer
Systems With An Architectural Carbon Modeling Tool. In Proceedings of
the 49th Annual International Symposium on Computer Architecture (ISCA
’22) (pp. 784–799). https://doi.org/10.1145/3470496.3527408

[6] DEFRA / DESNZ — UK Spend-Based & Activity Conversion Factors:For
spend-based supply chain multipliers (kgCO2e per £ spent): Department
for Environment,Food & Rural Affairs (Defra). (2026). UK and England’s
Carbon Footprint to 2023 (Table 13: Indirect Greenhouse Gas Conversion
Factors by Standard Industrial Classification).
https://www.gov.uk/government/statistics/uks-carbon-footprint

[7] HEPA / UKUPC — HESCET (Higher Education Supply Chain Emissions
Tool): Higher Education Procurement Association (HEPA) & UK Universities
Purchasing Consortia (UKUPC). (2025). Higher Education Supply Chain
Emissions Tool (HESCET) v3.13. British Universities Finance Directors
Group (BUFDG) / HEPA. https://hepa.ac.uk/

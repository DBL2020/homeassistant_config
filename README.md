# HA_config
homeassistant config repository

## simple automation to optimize EV charging with Photovoltaics power (PV Überschussladen)
I was looking for a simple way to maximize EV charging with unused PV power. I tried some dedicated software, but finally a very simple homeassistant automation does it well.

6 A = 4 kW
8 A = 6 kW
10 A = 7 kW
12 A = 8 kW
14 A = 10 kW
16 A = 11 kW

### Prerequisites
1. Integration PV smartmeter with PV power surplus, example Fronius smartmeter, variable pvueb showing kW unused.
2. Integration Wallbox: here keba P30, common model DE440 

### Automation
- sonne_tanken_ein: 
When enabled, the automation is scheduled for every 10 minutes to either enable wallbox and set initial ampere setting (initial_ampere) or to change ampere setting when already in charging mode (change_ampere). Only starts if sun is above horizon of course.

### scripts
- intial_ampere: if not charging, sets the initial ampere setting and enables wallbox
- change_ampere: if charging, changes ampere setting or disables charging depending on PV power surplus

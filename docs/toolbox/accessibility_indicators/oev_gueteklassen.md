---
sidebar_position: 5
---
import thematicIcon from "/img/indicators/join/toolbox.webp";

# Public Transport Quality Classes (ÖV Güteklassen)


The Public Transport Quality Classes <i>(German: ÖV Güteklassen)</i> show the **attractiveness of public transport services**. This indicator helps to understand how public transport supply varies across a city or region. 


## 1. Explanation

Public Transport Quality Classes, also known as **ÖV-Güteklassen**, are a classification system used to evaluate and categorise the **quality of public transport** services in a given area. The concept is used to plan and evaluate public transport services to ensure that they meet certain standards and effectively serve the needs of the population. The **quality classes** thereby range from **<span style={{color: "#199741"}}>A</span>** (very good offer) to **<span style={{color: "#E4696A"}}>F</span>** (very poor offer).

![ÖV-Güteklassen in GOAT](/img/indicators/public_transport/gueteklassen/example.png "ÖV-Güteklassen in GOAT")


## 2. Example use cases

- How good is public transport supply in different parts of the city?
- How many people are underserved by public transport? Where is the need for further supply?
- How does the quality of public transport services differ at different times of the week and day?

## 3. How to use the indicator?

<div class="step">
  <div class="step-number">1</div>
  <div class="content">Click on <code>Toolbox</code> <img src={thematicIcon} alt="toolbox" style={{width: "25px"}}/>. </div>
</div>

<div class="step">
  <div class="step-number">2</div>
  <div class="content">Under the <code>Accessibility Indicators</code> menu, click on <code>Public Transport Quality Classses (ÖV Güteklassen)</code>. This opens the setting menu.</div>
</div>

![Menu Overview for ÖV-Güteklassen](/img/indicators/public_transport/gueteklassen/overview.png "Menu Overview for ÖV-Güteklassen")

<div class="step">
  <div class="step-number">3</div>
  <div class="content">Define the <code>Calculation Time</code> (the day and the time).</div>
</div>

<div class="step">
  <div class="step-number">4</div>
  <div class="content">Select the <code>Reference Area Layer</code> for which you like to calculate the indicator. This can be any polygon feature layer.</div>
</div>

![Reference Area Selection](/img/indicators/public_transport/gueteklassen/reference_area.png "Reference Area Selection")


<div class="step">
  <div class="step-number">5</div>
  <div class="content">Click on <code>Run</code>. This starts the calculation of the Public Transport Quality Classes for the selected area.</div>
</div>

:::tip Hint

Depending on the size of the selected area, the calculation might take some minutes. The [status bar](../../workspace/home#status-bar) shows the current progress.

:::

<div class="step">
  <div class="step-number">6</div>
  <div class="content">As soon as the calculation process is finished, the resulting layers will be added to the map. The results consist of one layer called <b>"ÖV-Güteklassen"</b>, showing the Public Transport Quality Classes, and one layer called <b>"ÖV-Güteklassen Stations"</b> which provides all stations that were used for the calculation of this indicator. The station points that are visualized in grey have a too low service frequency and thus do not contribute to any Public Transport Quality Class.</div>
</div>

![Result - Public Transport Quality Classes](/img/indicators/public_transport/gueteklassen/result.png "Result - Public Transport Quality Classes")


## 4. Technical details

### Scientific Background

The quality and frequency of transit services is a **decisive indicator in public transport and spatial planning**. It can be used to highlight deficits in the public transport offer and to identify well-serviced locations as attractive areas for development. The approach of Public Transport Quality Classes <i>(German: ÖV Güteklassen)</i> is **methodologically superior** compared to common catchment areas. In 2011, the [Swiss Federal Office for Spatial Development (ARE)](https://www.are.admin.ch/are/de/home.html) started to use the indicator of <i>ÖV Güteklassen</i> in order to include the **attractiveness of public transport services** in the assessment of development quality; since then, these have been considered an important instrument in formal planning processes in Switzerland. In addition, the Swiss model served as an inspiration for application in Austria (e.g. Voralberg) and finds first application in Germany (e.g. by [KCW](https://plan4better.de/en/references/g%C3%BCteklassen-deutschland/) and [Agora Verkehrswende](https://plan4better.de/en/references/agora/)).  

The institutionalization of the indicator in German-speaking countries, as well as the comprehensible and at the same time differentiated calculation methodology, are important advantages of the <i>ÖV Güteklassen</i>. 

### Calculation

In the Swiss version of the indicator, the calculation of the quality classes is usually carried out for departures on weekdays between 6 AM and 8 PM. For the use in GOAT, the **calculation period** was made more flexible so that the indicator can be calculated **for any day of the week and time of day**. Furthermore, the indicator was adapted to the conditions in Germany. 

The calculations are carried out on the basis of **GTFS data** (see [Data Basis](../../data/data_basis)). First, the number of departures per public transport mode (train, metro, tram and bus) is dynamically calculated for each station. The sum of the departures is divided by two to calculate the frequency, in order to eliminate the outward and return directions. In the next step, the **average frequency** for the selected time interval is calculated. The higher-value service is selected as the **station type** in the case of service by several means of transport. For example, in the case of bus and train, this is the train. With the help of the table below, as well as the station type and the frequency, the station category can now be determined. 

![Classification of transport stops](/img/indicators/public_transport/gueteklassen/classification_stations_en.webp "Classification of transport stops")

Subsequently, **buffers** of the size shown are calculated for the corresponding station categories. This creates several buffers that are merged. For overlapping buffers, the higher quality class is used. 

![Determination of Public Transport Quality Classes](/img/indicators/public_transport/gueteklassen/determination_oev_gueteklasse_en.webp "Determination of Public Transport Quality Classes")

### Visualization

The created buffers are visualized around the stations in the corresponding colours to highlight the **quality class** (<span style={{color: "#199741"}}>A</span>-<span style={{color: "#E4696A"}}>F</span>).

![Visualization of the ÖV-Güteklassen](/img/indicators/public_transport/gueteklassen/visualization.png "Visualization of the ÖV-Güteklassen")


## 5. Further readings

Sample projects where ÖV-Güteklassen were used:
- [Accessibility analyses for the "Mobility Guarantee" and "Public Transport Atlas" projects](https://plan4better.de/en/references/agora/) 
- [Calculation of public transport quality classes in Austria](https://plan4better.de/en/references/g%C3%BCteklassen-%C3%B6sterreich/)
- [Calculation of public transport quality classes in Germany](https://plan4better.de/en/references/g%C3%BCteklassen-deutschland/)

## 6. References

Bundesamt für Raumentwicklung ARE, 2022. [ÖV-Güteklassen Berechnungsmethodik ARE (Grundlagenbericht)](https://www.are.admin.ch/are/de/home/medien-und-publikationen/publikationen/verkehr/ov-guteklassen-berechnungsmethodik-are.html "Open Reference").

Hiess, H., 2017. [Entwicklung eines Umsetzungskonzeptes für österreichweite ÖV-Güteklassen](https://www.oerok.gv.at/fileadmin/user_upload/Bilder/2.Reiter-Raum_u._Region/1.OEREK/OEREK_2011/PS_RO_Verkehr/OeV-G%C3%BCteklassen_Bericht_Final_2017-04-12.pdf "Open Reference").

metron, 2017. [Bedienungsqualität und Erschließungsgüte im Öffentlichen Verkehr](https://vorarlberg.at/documents/302033/472144/1-+Schlussbericht.pdf/81c5f0d7-a0f0-54c7-e951-462cd5cf2831?t=1616147848364 "Open Reference").

Shkurti, Majk, 2022. "Spatio-temporal public transport accessibility analysis and benchmarking in an interactive WebGIS". url: https://www.researchgate.net/publication/365790691_Spatio-temporal_public_transport_accessibility_analysis_and_benchmarking_in_an_interactive_WebGIS 


# Example Data

This page explains how the route/trajectory example from the FF-ICE/R1 Implementation Guidance Manual (Appendix E-3.7) is concretely encoded in FIXM. 
The FPL Item 15c reads `DCT HGR V268 EMI DCT`

![Image](./map.png)

## Content of `<fx:departure>`

`Departure Aerodrome` `KHGR`

`EOBT` `07:00`

```xml
<fx:departure>
   <fx:aerodrome>
      <fb:locationIndicator>KHGR</fb:locationIndicator>
   </fx:aerodrome>
   <fx:estimatedOffBlockTime>2021-03-04T07:00:00.000Z</fx:estimatedOffBlockTime>
</fx:departure>
```

Encoding Rules:
* Rules for [`<fx:aerodrome>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-aerodromes)
* Rules for [`<fx:estimatedOffBlockTime>`](https://docs.fixm.aero/#/general-guidance/date-time-specification)


## Content of `<fx:arrival>`

`Destination Aerodrome` `KBWI`

```xml
<fx:arrival>
   <fx:destinationAerodrome>
      <fb:locationIndicator>KBWI</fb:locationIndicator>
   </fx:destinationAerodrome>
</fx:arrival>
```

Encoding Rules:
* Rules for [`<fx:aerodrome>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-aerodromes)


## Content of `<fx:routeInformation>`

`Total EET` `00:27:15`

`Cruising Level` `5000 ft`

`Cruising Speed` `160 kts`

```xml
<fx:routeInformation>
   <fx:cruisingLevel>
      <fb:altitude uom="FT">5000</fb:altitude>
   </fx:cruisingLevel>
   <fx:cruisingSpeed uom="KT">160</fx:cruisingSpeed>
   <fx:totalEstimatedElapsedTime>P0Y0M0DT0H27M15.000S</fx:totalEstimatedElapsedTime>
</fx:routeInformation>
```

Encoding Rules:
* Rules for [`<fb:altitude>`](https://docs.fixm.aero/#/general-guidance/vertical-distances)


## Content of `<fx:routeTrajectoryGroup>` - FF-ICE Basic Route

<table>
<thead>
<tr class="header">
<th>#</th>
<th>RE Start Point<br>& Geographic Position (optional)  </th>
<th>Along route Distance (optional)</th>
<th>Route to Next Element</th>
</tr>
</thead>
<tbody>

<tr>
<td><p>

`1`

```xml
<fx:element 
 seqNum="0">
```

</p></td>
<td><p>

`KHGR` `N39:42:31 W007:43:35`

```xml
<fx:elementStartPoint>
 <fb:aerodromeReferencePoint>
  <fb:locationIndicator>KHGR</...>
  <fb:referencePoint srsName="...:EPSG::4326">
   <fb:pos>39.70861111 -77.72638889</fb:pos>
```

</p></td>
<td><p>

`0.00 NM`

```xml
<fx:alongRouteDistance
 uom="NM">0</...>
```

</p></td>
<td><p>

`Direct`

```xml
<fx:routeDesignatorToNextElement>
 <fx:otherRouteDesignator>DIRECT</...>
```

</p></td>
</tr>

<tr>
<td><p>

`2`

```xml
<fx:element 
 seqNum="1">
```

</p></td>
<td><p>

`HGR` `N39:41:52 W077:51:21`

```xml
<fx:elementStartPoint>
 <fb:navaid>
  <fb:designator>HGR</fb:...>
  <fb:position srsName="...:EPSG::4326">
   <fb:pos>39.69777778 -77.85583333</fb:pos>
```

</p></td>
<td><p>

`6.12 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">6.12</...>
```

</p></td>
<td><p>

`V268`

```xml
<fx:routeDesignatorToNextElement>
 <fx:routeDesignator>V268</...>
```

</p></td>
</tr>

<tr>
<td><p>

`3`

```xml
<fx:element 
 seqNum="2">
```

</p></td>
<td><p>

`EMI` `N39:29:42 W076:58:43`

```xml
<fx:elementStartPoint>
 <fb:navaid>
  <fb:designator>EMI</fb:designator>
  <fb:position srsName="...:EPSG::4326">
   <fb:pos>39.495 -76.97861111</fb:pos>
```

</p></td>
<td><p>

`48.67 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">48.67</...>
```

</p></td>
<td><p>

`Direct`

```xml
<fx:routeDesignatorToNextElement>
 <fx:otherRouteDesignator>DIRECT</...>
```

</p></td>
</tr>

<tr>
<td><p>

`4`

```xml
<fx:element 
 seqNum="3">
```

</p></td>
<td><p>

`KBWI` `N39:10:33 W076:40:08`

```xml
<fx:elementStartPoint>
 <fb:aerodromeReferencePoint>
  <fb:locationIndicator>KBWI</...>
  <fb:referencePoint srsName="...:EPSG::4326">
   <fb:pos>39.17583333 -76.66888889</fb:pos>
```

</p></td>
<td><p>

`72.47 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">72.47</...>
```

</p></td>
<td><p>

`n/a`

</p></td>
</tr>

<tr>
<td><p>

Encoding Rules:
* Rules for [`seqNum`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)

</p></td>
<td><p>

Encoding Rules:
* Rules for [` <fb:aerodromeReferencePoint>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-aerodromes) 
* Rules for [`<fb:navaid>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-navaid) 
* Rules for [`<fb:pos>`](https://docs.fixm.aero/#/general-guidance/geographical-positions)

</p></td>
<td><p>


</p></td>
<td><p>


</p></td>
<td><p>


</p></td>
</tr>


</tbody>
</table>

```xml
<fx:Flight xmlns:fx="http://www.fixm.aero/flight/4.2" xmlns:fb="http://www.fixm.aero/base/4.2" xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:schemaLocation="...">
   <fx:arrival>
      <fx:destinationAerodrome>
         <fb:locationIndicator>KBWI</fb:locationIndicator>
      </fx:destinationAerodrome>
   </fx:arrival>
   <fx:departure>
      <fx:aerodrome>
         <fb:locationIndicator>KHGR</fb:locationIndicator>
      </fx:aerodrome>
      <fx:estimatedOffBlockTime>2021-03-04T07:00:00.000Z</fx:estimatedOffBlockTime>
   </fx:departure>
   <fx:routeTrajectoryGroup>
      <fx:desired>
         <fx:element seqNum="0">
            <fx:alongRouteDistance uom="NM">0.0</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:aerodromeReferencePoint>
                  <fb:locationIndicator>KHGR</fb:locationIndicator>
               </fb:aerodromeReferencePoint>
            </fx:elementStartPoint>
            <fx:routeDesignatorToNextElement>
               <fx:otherRouteDesignator>DIRECT</fx:otherRouteDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="1">
            <fx:alongRouteDistance uom="NM">6.12</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:navaid>
                  <fb:designator>HGR</fb:designator>
               </fb:navaid>
            </fx:elementStartPoint>
            <fx:routeDesignatorToNextElement>
               <fx:routeDesignator>V268</fx:routeDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="2">
            <fx:alongRouteDistance uom="NM">48.49</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:navaid>
                  <fb:designator>EMI</fb:designator>
               </fb:navaid>
            </fx:elementStartPoint>
            <fx:routeDesignatorToNextElement>
               <fx:otherRouteDesignator>DIRECT</fx:otherRouteDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="3">
            <fx:alongRouteDistance uom="NM">72.45</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:aerodromeReferencePoint>
                  <fb:locationIndicator>KBWI</fb:locationIndicator>
               </fb:aerodromeReferencePoint>
            </fx:elementStartPoint>
         </fx:element>
         <fx:routeInformation>
            <fx:cruisingLevel>
               <fb:altitude uom="FT">5000</fb:altitude>
            </fx:cruisingLevel>
            <fx:cruisingSpeed uom="KT">160</fx:cruisingSpeed>
            <fx:totalEstimatedElapsedTime>P0Y0M0DT0H27M15.000S</fx:totalEstimatedElapsedTime>
         </fx:routeInformation>
      </fx:desired>
   </fx:routeTrajectoryGroup>
</fx:Flight>

```

## Content of `<fx:routeTrajectoryGroup>` - FF-ICE Expanded Route

<table>
<thead>
<tr class="header">
<th>#</th>
<th>RE Start Point<br>& Geographic Position (optional)  </th>
<th>Along route Distance (optional)</th>
<th>Route to Next Element</th>
</tr>
</thead>
<tbody>

<tr>
<td><p>

`1`

```xml
<fx:element 
 seqNum="0">
```

</p></td>
<td><p>

`KHGR` `N39:42:31 W007:43:35`

```xml
<fx:elementStartPoint>
 <fb:aerodromeReferencePoint>
  <fb:locationIndicator>KHGR</...>
  <fb:referencePoint srsName="...:EPSG::4326">
   <fb:pos>39.70861111 -77.72638889</fb:pos>
```

</p></td>
<td><p>

`0.00 NM`

```xml
<fx:alongRouteDistance
 uom="NM">0</...>
```

</p></td>
<td><p>

`Direct`

```xml
<fx:routeDesignatorToNextElement>
 <fx:otherRouteDesignator>DIRECT</...>
```

</p></td>
</tr>

<tr>
<td><p>

`2`

```xml
<fx:element 
 seqNum="1">
```

</p></td>
<td><p>

`HGR` `N39:41:52 W077:51:21`

```xml
<fx:elementStartPoint>
 <fb:navaid>
  <fb:designator>HGR</fb:...>
  <fb:position srsName="...:EPSG::4326">
   <fb:pos>39.69777778 -77.85583333</fb:pos>
```

</p></td>
<td><p>

`6.12 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">6.12</...>
```

</p></td>
<td><p>

`V268`

```xml
<fx:routeDesignatorToNextElement>
 <fx:routeDesignator>V268</...>
```

</p></td>
</tr>

<tr>
<td><p>

`3`

```xml
<fx:element 
 seqNum="2">
```

</p></td>
<td><p>

`KEMAR` `N39:33:45 W077:16:02`

```xml
<fx:elementStartPoint>
 <fb:designatedPoint>
  <fb:designator>KEMAR</fb:designator>
  <fb:position srsName="...:EPSG::4326">
   <fb:pos>39.5625 -77.26722222</fb:pos>
```

</p></td>
<td><p>

`34.48 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">34.48</...>
```

</p></td>
<td><p>

`V268`

```xml
<fx:routeDesignatorToNextElement>
 <fx:routeDesignator>V268</...>
```

</p></td>
</tr>

<tr>
<td><p>

`4`

```xml
<fx:element 
 seqNum="3">
```

</p></td>
<td><p>

`EMI` `N39:29:42 W076:58:43`

```xml
<fx:elementStartPoint>
 <fb:navaid>
  <fb:designator>EMI</fb:designator>
  <fb:position srsName="...:EPSG::4326">
   <fb:pos>39.495 -76.97861111</fb:pos>
```

</p></td>
<td><p>

`48.67 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">48.67</...>
```

</p></td>
<td><p>

`Direct`

```xml
<fx:routeDesignatorToNextElement>
 <fx:otherRouteDesignator>DIRECT</...>
```

</p></td>
</tr>

<tr>
<td><p>

`5`

```xml
<fx:element 
 seqNum="4">
```

</p></td>
<td><p>

`KBWI` `N39:10:33 W076:40:08`

```xml
<fx:elementStartPoint>
 <fb:aerodromeReferencePoint>
  <fb:locationIndicator>KBWI</...>
  <fb:referencePoint srsName="...:EPSG::4326">
   <fb:pos>39.17583333 -76.66888889</fb:pos>
```

</p></td>
<td><p>

`72.47 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">72.47</...>
```

</p></td>
<td><p>

`n/a`

</p></td>
</tr>

<tr>
<td><p>

Encoding Rules:
* Rules for [`seqNum`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)

</p></td>
<td><p>

Encoding Rules:
* Rules for [` <fb:aerodromeReferencePoint>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-aerodromes) 
* Rules for [`<fb:navaid>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-navaid) 
* Rules for [`<fb:pos>`](https://docs.fixm.aero/#/general-guidance/geographical-positions)

</p></td>
<td><p>


</p></td>
<td><p>


</p></td>
<td><p>


</p></td>
</tr>


</tbody>
</table>

```xml
<fx:Flight xmlns:fx="http://www.fixm.aero/flight/4.2" xmlns:fb="http://www.fixm.aero/base/4.2" xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:schemaLocation="...">
   <fx:arrival>
      <fx:destinationAerodrome>
         <fb:locationIndicator>KBWI</fb:locationIndicator>
      </fx:destinationAerodrome>
   </fx:arrival>
   <fx:departure>
      <fx:aerodrome>
         <fb:locationIndicator>KHGR</fb:locationIndicator>
      </fx:aerodrome>
      <fx:estimatedOffBlockTime>2021-03-04T07:00:00.000Z</fx:estimatedOffBlockTime>
   </fx:departure>
   <fx:routeTrajectoryGroup>
      <fx:desired>
         <fx:element seqNum="0">
            <fx:alongRouteDistance uom="NM">0.0</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:aerodromeReferencePoint>
                  <fb:locationIndicator>KHGR</fb:locationIndicator>
                  <fb:referencePoint srsName="urn:ogc:def:crs:EPSG::4326">
                     <fb:pos>39.70861111 -77.72638889</fb:pos>
                  </fb:referencePoint>
               </fb:aerodromeReferencePoint>
            </fx:elementStartPoint>
            <fx:routeDesignatorToNextElement>
               <fx:otherRouteDesignator>DIRECT</fx:otherRouteDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="1">
            <fx:alongRouteDistance uom="NM">6.12</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:navaid>
                  <fb:designator>HGR</fb:designator>
                  <fb:position srsName="urn:ogc:def:crs:EPSG::4326">
                     <fb:pos>39.69777778 -77.85583333</fb:pos>
                  </fb:position>
               </fb:navaid>
            </fx:elementStartPoint>
            <fx:routeDesignatorToNextElement>
               <fx:routeDesignator>V268</fx:routeDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="2">
            <fx:alongRouteDistance uom="NM">34.48</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:designatedPoint>
                  <fb:designator>KEMAR</fb:designator>
                  <fb:position srsName="urn:ogc:def:crs:EPSG::4326">
                     <fb:pos>39.5625 -77.26722222</fb:pos>
                  </fb:position>
               </fb:designatedPoint>
            </fx:elementStartPoint>
            <fx:routeDesignatorToNextElement>
               <fx:routeDesignator>V268</fx:routeDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="3">
            <fx:alongRouteDistance uom="NM">48.49</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:navaid>
                  <fb:designator>EMI</fb:designator>
                  <fb:position srsName="urn:ogc:def:crs:EPSG::4326">
                     <fb:pos>39.495 -76.97861111</fb:pos>
                  </fb:position>
               </fb:navaid>
            </fx:elementStartPoint>
            <fx:routeDesignatorToNextElement>
               <fx:otherRouteDesignator>DIRECT</fx:otherRouteDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="4">
            <fx:alongRouteDistance uom="NM">72.45</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:aerodromeReferencePoint>
                  <fb:locationIndicator>KBWI</fb:locationIndicator>
                  <fb:referencePoint srsName="urn:ogc:def:crs:EPSG::4326">
                     <fb:pos>39.17583333 -76.66888889</fb:pos>
                  </fb:referencePoint>
               </fb:aerodromeReferencePoint>
            </fx:elementStartPoint>
         </fx:element>
         <fx:routeInformation>
            <fx:cruisingLevel>
               <fb:altitude uom="FT">5000</fb:altitude>
            </fx:cruisingLevel>
            <fx:cruisingSpeed uom="KT">160</fx:cruisingSpeed>
            <fx:totalEstimatedElapsedTime>P0Y0M0DT0H27M15.000S</fx:totalEstimatedElapsedTime>
         </fx:routeInformation>
      </fx:desired>
   </fx:routeTrajectoryGroup>
</fx:Flight>
```

## Content of `<fx:routeTrajectoryGroup>` - FF-ICE Trajectory

<table>
<thead>
<tr class="header">
<th>#</th>
<th>RE Start Point<br>& Geographic Position (optional)<br>& Along Route Distance (optional)<br>& Route to Next Element</th>
<th>Trajectory Point</th>
<th>Route to Next Element</th>
</tr>
</thead>
<tbody>

<tr>
<td><p>

`1`

```xml
<fx:element 
 seqNum="0">
```

</p></td>
<td><p>

`KHGR` `N39:42:31 W007:43:35`

```xml
<fx:elementStartPoint>
 <fb:aerodromeReferencePoint>
  <fb:locationIndicator>KHGR</...>
  <fb:referencePoint srsName="...:EPSG::4326">
   <fb:pos>39.70861111 -77.72638889</fb:pos>
```

`0.00 NM`

```xml
<fx:alongRouteDistance uom="NM">0.0</...>
```

`Direct`

```xml
<fx:routeDesignatorToNextElement>
 <fx:otherRouteDesignator>DIRECT</...>
```


</p></td>
<td><p>

`Geographic Position` `N39:42:31 W077:43:35`

`Point Property` `Airport Reference Loc.` `Initial Prediction Point`

`Altitude` `703 ft`

`Ind. Air Speed` `125 kts`

`Time` `Absolute 07:00:00`

```xml
<fx:point4D>
 <fx:level>
  <fb:altitude uom="FT">703</fb:altitude>
 </fx:level>
 <fx:pointProperty>
  <fx:propertyType>AIRPORT_REFERENCE_LOCATION</...>
 </fx:pointProperty>
 <fx:pointProperty>
  <fx:propertyType>INITIAL_PREDICTION_POINT</...>
 </fx:pointProperty>
 <fx:position srsName="...:EPSG::4326">
  <fb:pos>39.70861111 -77.72638889</fb:pos>
 </fx:position>
 <fx:predictedAirspeed uom="KT">125</...>
 <fx:time>
  <fx:absoluteTime>2021-03-04T07:00:00.000Z</...>
 </fx:time>
</fx:point4D>
```

</p></td>
<td><p>



</p></td>

</tr>

<tr>
<td><p>

`2`

```xml
<fx:element 
 seqNum="1">
```

</p></td>
<td><p>

`HGR` `N39:41:52 W077:51:21`

```xml
<fx:elementStartPoint>
 <fb:navaid>
  <fb:designator>HGR</fb:...>
  <fb:position srsName="...:EPSG::4326">
   <fb:pos>39.69777778 -77.85583333</fb:pos>
```

</p></td>
<td><p>

`6.12 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">6.12</...>
```

</p></td>
<td><p>

`V268`

```xml
<fx:routeDesignatorToNextElement>
 <fx:routeDesignator>V268</...>
```

</p></td>
</tr>

<tr>
<td><p>

`3`

```xml
<fx:element 
 seqNum="2">
```

</p></td>
<td><p>

`KEMAR` `N39:33:45 W077:16:02`

```xml
<fx:elementStartPoint>
 <fb:designatedPoint>
  <fb:designator>KEMAR</fb:designator>
  <fb:position srsName="...:EPSG::4326">
   <fb:pos>39.5625 -77.26722222</fb:pos>
```

</p></td>
<td><p>

`34.48 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">34.48</...>
```

</p></td>
<td><p>

`V268`

```xml
<fx:routeDesignatorToNextElement>
 <fx:routeDesignator>V268</...>
```

</p></td>
</tr>

<tr>
<td><p>

`4`

```xml
<fx:element 
 seqNum="3">
```

</p></td>
<td><p>

`EMI` `N39:29:42 W076:58:43`

```xml
<fx:elementStartPoint>
 <fb:navaid>
  <fb:designator>EMI</fb:designator>
  <fb:position srsName="...:EPSG::4326">
   <fb:pos>39.495 -76.97861111</fb:pos>
```

</p></td>
<td><p>

`48.67 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">48.67</...>
```

</p></td>
<td><p>

`Direct`

```xml
<fx:routeDesignatorToNextElement>
 <fx:otherRouteDesignator>DIRECT</...>
```

</p></td>
</tr>

<tr>
<td><p>

`5`

```xml
<fx:element 
 seqNum="4">
```

</p></td>
<td><p>

`KBWI` `N39:10:33 W076:40:08`

```xml
<fx:elementStartPoint>
 <fb:aerodromeReferencePoint>
  <fb:locationIndicator>KBWI</...>
  <fb:referencePoint srsName="...:EPSG::4326">
   <fb:pos>39.17583333 -76.66888889</fb:pos>
```

</p></td>
<td><p>

`72.47 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">72.47</...>
```

</p></td>
<td><p>

`n/a`

</p></td>

</tr>

<tr>
<td><p>

Encoding Rules:
* Rules for [`seqNum`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)

</p></td>
<td><p>

Encoding Rules:
* Rules for [` <fb:aerodromeReferencePoint>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-aerodromes) 
* Rules for [`<fb:navaid>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-navaid) 
* Rules for [`<fb:pos>`](https://docs.fixm.aero/#/general-guidance/geographical-positions)

</p></td>
<td><p>


</p></td>
<td><p>


</p></td>
<td><p>


</p></td>
<td><p>


</p></td>
</tr>


</tbody>
</table>

|`<fx:element>`|`<fx:elementStartPoint>`|`<fx:routeDesignatorToNextElement>`|`<fx:alongRouteDistance>`|`<fx:point4D>`|
|:-|:-|:-|:-|:-|
|**[`seqNum="0"`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)**|[`<fb:aerodromeReferencePoint>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-aerodromes)<br>`<fb:locationIndicator>` **`KHGR`**<br>[`<fb:pos>`](https://docs.fixm.aero/#/general-guidance/geographical-positions) **`39.70861111 -77.72638889`**|`<fx:otherRouteDesignator>` **`DIRECT`**|**`0.0` `uom="NM"`**|`<fx:pointProperty>` `<fx:propertyType>` **`AIRPORT_REFERENCE_LOCATION`** **`INITIAL_PREDICTION_POINT`**<br><br>`<fx:position>` [`<fb:pos>`](https://docs.fixm.aero/#/general-guidance/geographical-positions) **`39.70861111 -77.72638889`**<br><br>`<fx:level>` [`<fb:altitude>`](https://docs.fixm.aero/#/general-guidance/vertical-distances) **`703` `uom="FT"`**<br><br>`<fx:predictedAirspeed>` **`125` `uom="KT"`**<br><br>`<fx:time>` [`<fx:absoluteTime>`](https://docs.fixm.aero/#/general-guidance/date-time-specification) **`2021-03-04T07:00:00.000Z`**|
|**[`seqNum="1"`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)**|[`<fb:navaid>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-navaid)<br>`fb:designator` **`HGR`**<br>[`<fb:pos>`](https://docs.fixm.aero/#/general-guidance/geographical-positions) **`39.69777778 -77.85583333`**|[`<fx:routeDesignator>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-enroute-ats-routes) **`V268`**|**`6.12` `uom="NM"`**|`<fx:pointProperty>` `<fx:propertyType>` **`TCP_LATERAL`**<br><br>`<fx:position>` [`<fb:pos>`](https://docs.fixm.aero/#/general-guidance/geographical-positions) **`39.70861111 -77.72638889`**<br><br>`<fx:level>` [`<fb:altitude>`](https://docs.fixm.aero/#/general-guidance/vertical-distances) **`2732` `uom="FT"`**<br><br>`<fx:predictedAirspeed>` **`125` `uom="KT"`**<br><br>`<fx:time>` `<fx:relativeTimeFromInitialPredictionPoint>` **`P0Y0M0DT0H2M35.000S`**|
|**[`seqNum="2"`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)**||[`<fx:routeDesignator>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-enroute-ats-routes) **`V268`**|**`10.35` `uom="NM"`**|`<fx:position>` [`<fb:pos>`](https://docs.fixm.aero/#/general-guidance/geographical-positions) **`39.67722222 -77.76583333`**<br><br>`<fx:level>` [`<fb:altitude>`](https://docs.fixm.aero/#/general-guidance/vertical-distances) **`4389` `uom="FT"`**<br><br>`<fx:predictedAirspeed>` **`125` `uom="KT"`**<br><br>`<fx:time>` `<fx:relativeTimeFromInitialPredictionPoint>` **`P0Y0M0DT0H4M43.000S`**|
|**[`seqNum="3"`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)**||[`<fx:routeDesignator>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-enroute-ats-routes) **`V268`**|**`12.18` `uom="NM"`**|`TODO`|
|**[`seqNum="4"`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)**||[`<fx:routeDesignator>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-enroute-ats-routes) **`V268`**|**`13.26` `uom="NM"`**|`TODO`|
|**[`seqNum="5"`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)**|[`fb:designatedPoint`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-waypoints)<br>`fb:designator` **`KEMAR`**<br>[`<fb:pos>`](https://docs.fixm.aero/#/general-guidance/geographical-positions) **`39.5625 -77.26722222`**|[`<fx:routeDesignator>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-enroute-ats-routes) **`V268`**|**`34.48` `uom="NM"`**|`TODO`|
|**[`seqNum="6"`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)**|[`<fb:navaid>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-navaid)<br>`fb:designator` **`EMI`**<br>[`<fb:pos>`](https://docs.fixm.aero/#/general-guidance/geographical-positions) **`39.17583333 -76.66888889`**|`<fx:otherRouteDesignator>` **`DIRECT`**|**`48.49` `uom="NM"`**|`TODO`|
|**[`seqNum="7"`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)**||`<fx:otherRouteDesignator>` **`DIRECT`**|**`51.18` `uom="NM"`**|`TODO`|
|**[`seqNum="8"`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)**||`<fx:otherRouteDesignator>` **`DIRECT`**|**`51.84` `uom="NM"`**|`TODO`|
|**[`seqNum="9"`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)**||`<fx:otherRouteDesignator>` **`DIRECT`**|**`71.52` `uom="NM"`**|`TODO`|
|**[`seqNum="10"`](https://docs.fixm.aero/#/general-guidance/sequence-numbers)**|[`<fb:aerodromeReferencePoint>`](https://docs.fixm.aero/#/general-guidance/references-to-published-aeronautical-information?id=references-to-aerodromes)<br>`<fb:locationIndicator>` **`KBWI`**<br>[`<fb:pos>`](https://docs.fixm.aero/#/general-guidance/geographical-positions) **`39.17583333 -76.66888889`**||**`72.45` `uom="NM"`**|`TODO`|


```xml
<fx:Flight xmlns:fx="http://www.fixm.aero/flight/4.2" xmlns:fb="http://www.fixm.aero/base/4.2" xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:schemaLocation="...">
   <fx:arrival>
      <fx:destinationAerodrome>
         <fb:locationIndicator>KBWI</fb:locationIndicator>
      </fx:destinationAerodrome>
   </fx:arrival>
   <fx:departure>
      <fx:aerodrome>
         <fb:locationIndicator>KHGR</fb:locationIndicator>
      </fx:aerodrome>
      <fx:estimatedOffBlockTime>2021-03-04T07:00:00.000Z</fx:estimatedOffBlockTime>
   </fx:departure>
   <fx:routeTrajectoryGroup>
      <fx:desired>
         <fx:element seqNum="0">
            <fx:alongRouteDistance uom="NM">0.0</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:aerodromeReferencePoint>
                  <fb:locationIndicator>KHGR</fb:locationIndicator>
                  <fb:referencePoint srsName="urn:ogc:def:crs:EPSG::4326">
                     <fb:pos>39.70861111 -77.72638889</fb:pos>
                  </fb:referencePoint>
               </fb:aerodromeReferencePoint>
            </fx:elementStartPoint>
            <fx:point4D>
               <fx:level>
                  <fb:altitude uom="FT">703</fb:altitude>
               </fx:level>
               <fx:pointProperty>
                  <fx:propertyType>AIRPORT_REFERENCE_LOCATION</fx:propertyType>
               </fx:pointProperty>
               <fx:pointProperty>
                  <fx:propertyType>INITIAL_PREDICTION_POINT</fx:propertyType>
               </fx:pointProperty>
               <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
                  <fb:pos>39.70861111 -77.72638889</fb:pos>
               </fx:position>
               <fx:predictedAirspeed uom="KT">125</fx:predictedAirspeed>
               <fx:time>
                  <fx:absoluteTime>2021-03-04T07:00:00.000Z</fx:absoluteTime>
               </fx:time>
            </fx:point4D>
            <fx:routeDesignatorToNextElement>
               <fx:otherRouteDesignator>DIRECT</fx:otherRouteDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="1">
            <fx:alongRouteDistance uom="NM">6.02</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:navaid>
                  <fb:designator>HGR</fb:designator>
                  <fb:position srsName="urn:ogc:def:crs:EPSG::4326">
                     <fb:pos>39.69777778 -77.85583333</fb:pos>
                  </fb:position>
               </fb:navaid>
            </fx:elementStartPoint>
            <fx:point4D>
               <fx:level>
                  <fb:altitude uom="FT">2732</fb:altitude>
               </fx:level>
               <fx:pointProperty>
                  <fx:propertyType>TCP_LATERAL</fx:propertyType>
               </fx:pointProperty>
               <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
                  <fb:pos>39.70861111 -77.72638889</fb:pos>
               </fx:position>
               <fx:predictedAirspeed uom="KT">125</fx:predictedAirspeed>
               <fx:time>
                  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H2M35.000S</fx:relativeTimeFromInitialPredictionPoint>
               </fx:time>
            </fx:point4D>
            <fx:routeDesignatorToNextElement>
               <fx:routeDesignator>V268</fx:routeDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="2">
            <fx:alongRouteDistance uom="NM">10.35</fx:alongRouteDistance>
            <fx:point4D>
               <fx:level>
                  <fb:altitude uom="FT">4389</fb:altitude>
               </fx:level>
               <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
                  <fb:pos>39.67722222 -77.76583333</fb:pos>
               </fx:position>
               <fx:predictedAirspeed uom="KT">125</fx:predictedAirspeed>
               <fx:time>
                  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H4M43.000S</fx:relativeTimeFromInitialPredictionPoint>
               </fx:time>
            </fx:point4D>
            <fx:routeDesignatorToNextElement>
               <fx:routeDesignator>V268</fx:routeDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="3">
            <fx:alongRouteDistance uom="NM">12.18</fx:alongRouteDistance>
            <fx:point4D>
               <fx:level>
                  <fb:altitude uom="FT">5000</fb:altitude>
               </fx:level>
               <fx:pointProperty>
                  <fx:propertyType>TOP_OF_CLIMB</fx:propertyType>
               </fx:pointProperty>
               <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
                  <fb:pos>39.66833333 -77.72666667</fb:pos>
               </fx:position>
               <fx:predictedAirspeed uom="KT">125</fx:predictedAirspeed>
               <fx:time>
                  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H5M35.000S</fx:relativeTimeFromInitialPredictionPoint>
               </fx:time>
            </fx:point4D>
            <fx:routeDesignatorToNextElement>
               <fx:routeDesignator>V268</fx:routeDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="4">
            <fx:alongRouteDistance uom="NM">13.26</fx:alongRouteDistance>
            <fx:point4D>
               <fx:level>
                  <fb:altitude uom="FT">5000</fb:altitude>
               </fx:level>
               <fx:pointProperty>
                  <fx:propertyType>TCP_SPEED</fx:propertyType>
               </fx:pointProperty>
               <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
                  <fb:pos>39.66333333 -77.70416667</fb:pos>
               </fx:position>
               <fx:predictedAirspeed uom="KT">160</fx:predictedAirspeed>
               <fx:time>
                  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H6M2.000S</fx:relativeTimeFromInitialPredictionPoint>
               </fx:time>
            </fx:point4D>
            <fx:routeDesignatorToNextElement>
               <fx:routeDesignator>V268</fx:routeDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="5">
            <fx:alongRouteDistance uom="NM">34.48</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:designatedPoint>
                  <fb:designator>KEMAR</fb:designator>
                  <fb:position srsName="urn:ogc:def:crs:EPSG::4326">
                     <fb:pos>39.5625 -77.26722222</fb:pos>
                  </fb:position>
               </fb:designatedPoint>
            </fx:elementStartPoint>
            <fx:point4D>
               <fx:level>
                  <fb:altitude uom="FT">5000</fb:altitude>
               </fx:level>
               <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
                  <fb:pos>39.5625 -77.26722222</fb:pos>
               </fx:position>
               <fx:predictedAirspeed uom="KT">160</fx:predictedAirspeed>
               <fx:time>
                  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H13M56.000S</fx:relativeTimeFromInitialPredictionPoint>
               </fx:time>
            </fx:point4D>
            <fx:routeDesignatorToNextElement>
               <fx:routeDesignator>V268</fx:routeDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="6">
            <fx:alongRouteDistance uom="NM">48.49</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:navaid>
                  <fb:designator>EMI</fb:designator>
                  <fb:position srsName="urn:ogc:def:crs:EPSG::4326">
                     <fb:pos>39.495 -76.97861111</fb:pos>
                  </fb:position>
               </fb:navaid>
            </fx:elementStartPoint>
            <fx:point4D>
               <fx:level>
                  <fb:altitude uom="FT">5000</fb:altitude>
               </fx:level>
               <fx:pointProperty>
                  <fx:propertyType>TCP_LATERAL</fx:propertyType>
               </fx:pointProperty>
               <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
                  <fb:pos>39.495 -76.97861111</fb:pos>
               </fx:position>
               <fx:predictedAirspeed uom="KT">160</fx:predictedAirspeed>
               <fx:time>
                  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H19M2.000S</fx:relativeTimeFromInitialPredictionPoint>
               </fx:time>
            </fx:point4D>
            <fx:routeDesignatorToNextElement>
               <fx:otherRouteDesignator>DIRECT</fx:otherRouteDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="7">
            <fx:alongRouteDistance uom="NM">51.18</fx:alongRouteDistance>
            <fx:point4D>
               <fx:level>
                  <fb:altitude uom="FT">5000</fb:altitude>
               </fx:level>
               <fx:pointProperty>
                  <fx:propertyType>TOP_OF_DESCENT</fx:propertyType>
               </fx:pointProperty>
               <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
                  <fb:pos>39.45722222 -76.94166667</fb:pos>
               </fx:position>
               <fx:predictedAirspeed uom="KT">160</fx:predictedAirspeed>
               <fx:time>
                  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H20M1.000S</fx:relativeTimeFromInitialPredictionPoint>
               </fx:time>
            </fx:point4D>
            <fx:routeDesignatorToNextElement>
               <fx:otherRouteDesignator>DIRECT</fx:otherRouteDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="8">
            <fx:alongRouteDistance uom="NM">51.84</fx:alongRouteDistance>
            <fx:point4D>
               <fx:level>
                  <fb:altitude uom="FT">4852</fb:altitude>
               </fx:level>
               <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
                  <fb:pos>39.44833333 -76.93305556</fb:pos>
               </fx:position>
               <fx:predictedAirspeed uom="KT">160</fx:predictedAirspeed>
               <fx:time>
                  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H20M15.000S</fx:relativeTimeFromInitialPredictionPoint>
               </fx:time>
            </fx:point4D>
            <fx:routeDesignatorToNextElement>
               <fx:otherRouteDesignator>DIRECT</fx:otherRouteDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="9">
            <fx:alongRouteDistance uom="NM">71.52</fx:alongRouteDistance>
            <fx:point4D>
               <fx:level>
                  <fb:altitude uom="FT">366</fb:altitude>
               </fx:level>
               <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
                  <fb:pos>39.18777778 -76.68055556</fb:pos>
               </fx:position>
               <fx:predictedAirspeed uom="KT">120</fx:predictedAirspeed>
               <fx:time>
                  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H26M55.000S</fx:relativeTimeFromInitialPredictionPoint>
               </fx:time>
            </fx:point4D>
            <fx:routeDesignatorToNextElement>
               <fx:otherRouteDesignator>DIRECT</fx:otherRouteDesignator>
            </fx:routeDesignatorToNextElement>
         </fx:element>
         <fx:element seqNum="10">
            <fx:alongRouteDistance uom="NM">72.45</fx:alongRouteDistance>
            <fx:elementStartPoint>
               <fb:aerodromeReferencePoint>
                  <fb:locationIndicator>KBWI</fb:locationIndicator>
                  <fb:referencePoint srsName="urn:ogc:def:crs:EPSG::4326">
                     <fb:pos>39.17583333 -76.66888889</fb:pos>
                  </fb:referencePoint>
               </fb:aerodromeReferencePoint>
            </fx:elementStartPoint>
            <fx:point4D>
               <fx:level>
                  <fb:altitude uom="FT">143</fb:altitude>
               </fx:level>
               <fx:pointProperty>
                  <fx:propertyType>AIRPORT_REFERENCE_LOCATION</fx:propertyType>
               </fx:pointProperty>
               <fx:pointProperty>
                  <fx:propertyType>END_PREDICTION_POINT</fx:propertyType>
               </fx:pointProperty>
               <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
                  <fb:pos>39.17583333 -76.66888889</fb:pos>
               </fx:position>
               <fx:predictedAirspeed uom="KT">100</fx:predictedAirspeed>
               <fx:time>
                  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H27M15.000S</fx:relativeTimeFromInitialPredictionPoint>
               </fx:time>
            </fx:point4D>
         </fx:element>
         <fx:routeInformation>
            <fx:cruisingLevel>
               <fb:altitude uom="FT">5000</fb:altitude>
            </fx:cruisingLevel>
            <fx:cruisingSpeed uom="KT">160</fx:cruisingSpeed>
            <fx:totalEstimatedElapsedTime>P0Y0M0DT0H27M15.000S</fx:totalEstimatedElapsedTime>
         </fx:routeInformation>
      </fx:desired>
   </fx:routeTrajectoryGroup>
</fx:Flight>
```

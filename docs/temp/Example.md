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
<th>Route Element Start Point<br>& Geographic Position (optional)  </th>
<th>Along Route Distance (optional)</th>
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
<th>Route Element Start Point<br>& Geographic Position (optional)  </th>
<th>Along Route Distance (optional)</th>
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

*This is a route element added by the expanded route, featuring the waypoint KEMAR that is published along route V268.*

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
<th>Route Element<br>- Start Point & Geographic Position <br>- Along Route Distance<br>Route to Next Element</th>
<th>Trajectory Point<br>- Geographic Position / Level / Time<br>- Indicated Air Speed<br>- Point Property</th>
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

`N39:42:31 W077:43:35` `703 ft` `Absolute 07:00:00`

`125 kts`

`Airport Reference Loc.` `Initial Prediction Point`


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
<!--
The example uses the aerodrome reference location 
as the Initial  Prediction Point. However, if known, 
the specific departure runway location should be 
included as precise trajectory start point, using 
the appropriate point property (Wheels_off...).
-->
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

`6.12 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">6.12</...>
```

`V268`

```xml
<fx:routeDesignatorToNextElement>
 <fx:routeDesignator>V268</...>
```

</p></td>
<td><p>

`N39:41:52 W077:51:21` `2732 ft` `Relative 00:02:35`

`125 kts`

`TCP - Lateral`


```xml
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
  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H2M35.000S</...>
 </fx:time>
</fx:point4D>
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

`10.35 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">10.35</...>
<!--
A trajectory point with no associated significant 
point will still show an along route distance. 
This must be the projection of the trajectory point
geographic position onto the relevant route segment.
This projection should be perpendicular to the
trajectory.
-->
```

`V268`

```xml
<fx:routeDesignatorToNextElement>
 <fx:routeDesignator>V268</...>
```

</p></td>
<td><p>

`N39:40:38 W077:45:57` `4389 ft` `Relative 00:04:43`

`125 kts`

```xml
<fx:point4D>
 <fx:level>
  <fb:altitude uom="FT">4389</fb:altitude>
 </fx:level>
 <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
  <fb:pos>39.67722222 -77.76583333</fb:pos>
 </fx:position>
 <fx:predictedAirspeed uom="KT">125</fx:predictedAirspeed>
 <fx:time>
  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H4M43.000S</...>
 </fx:time>
</fx:point4D>
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

`12.18 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">12.18</...>
```

`V268`

```xml
<fx:routeDesignatorToNextElement>
 <fx:routeDesignator>V268</...>
```

</p></td>
<td><p>

`N39:40:06 W077:43:36` `5000 ft` `Relative 00:05:35`

`125 kts`

`Top of Climb`

```xml
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
  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H5M35.000S</fx:...>
 </fx:time>
</fx:point4D>
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

`13.26 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">13.26</...>
```

`V268`

```xml
<fx:routeDesignatorToNextElement>
 <fx:routeDesignator>V268</...>
```

</p></td>
<td><p>

`N39:39:48 W077:42:15` `5000 ft` `Relative 00:06:02`

`160 kts`

`TCP - Speed`

```xml
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
  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H6M2.000S</...>
 </fx:time>
</fx:point4D>
```

</p></td>
</tr>



<tr>


<td><p>

`6`

```xml
<fx:element 
 seqNum="5">
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

`34.48 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">34.48</...>
```

`V268`

```xml
<fx:routeDesignatorToNextElement>
 <fx:routeDesignator>V268</...>
```

</p></td>
<td><p>

`N39:33:45 W077:16:02` `5000 ft` `Relative 00:13:56`

`160 kts`

```xml
<fx:point4D>
 <fx:level>
  <fb:altitude uom="FT">5000</fb:altitude>
 </fx:level>
 <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
  <fb:pos>39.5625 -77.26722222</fb:pos>
 </fx:position>
 <fx:predictedAirspeed uom="KT">160</fx:predictedAirspeed>
 <fx:time>
  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H13M56.000S</...>
 </fx:time>
</fx:point4D>
```

</p></td>

</tr>

<tr>
<td><p>

`7`

```xml
<fx:element 
 seqNum="6">
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

`48.67 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">48.67</...>
```

`Direct`

```xml
<fx:routeDesignatorToNextElement>
 <fx:otherRouteDesignator>DIRECT</...>
```

</p></td>
<td><p>

`N39:29:42 W076:58:43` `5000 ft` `Relative 00:19:02`

`160 kts`

`TCP - Lateral`

```xml
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
  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H19M2.000S</...>
 </fx:time>
</fx:point4D>
```

</p></td>

</tr>


<tr>
<td><p>

`8`

```xml
<fx:element 
 seqNum="7">
```

</p></td>
<td><p>

`51.18 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">51.18</...>
```

`Direct`

```xml
<fx:routeDesignatorToNextElement>
 <fx:otherRouteDesignator>DIRECT</...>
```

</p></td>
<td><p>

`N39:27:26 W076:56:30` `5000 ft` `Relative 00:20:01`

`160 kts`

`Top of Descent`

```xml
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
  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H20M1.000S</...>
 </fx:time>
</fx:point4D>
```

</p></td>
</tr>

<tr>
<td><p>

`9`

```xml
<fx:element 
 seqNum="8">
```

</p></td>
<td><p>

`51.84 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">51.84</...>
```

`Direct`

```xml
<fx:routeDesignatorToNextElement>
 <fx:otherRouteDesignator>DIRECT</...>
```

</p></td>
<td><p>

`N39:26:54 W076:55:59` `4852 ft` `Relative 00:20:15`

`160 kts`

```xml
<fx:point4D>
 <fx:level>
  <fb:altitude uom="FT">4852</fb:altitude>
 </fx:level>
 <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
  <fb:pos>39.44833333 -76.93305556</fb:pos>
 </fx:position>
 <fx:predictedAirspeed uom="KT">160</fx:predictedAirspeed>
 <fx:time>
  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H20M15.000S</...>
 </fx:time>
</fx:point4D>
```

</p></td>
</tr>

<tr>
<td><p>

`10`

```xml
<fx:element 
 seqNum="9">
```

</p></td>
<td><p>

`71.52 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">71.52</...>
```

`Direct`

```xml
<fx:routeDesignatorToNextElement>
 <fx:otherRouteDesignator>DIRECT</...>
```

</p></td>
<td><p>

`N39:11:16 W076:40:50` `366 ft` `Relative 00:26:55`

`120 kts`

```xml
<fx:point4D>
 <fx:level>
  <fb:altitude uom="FT">366</fb:altitude>
 </fx:level>
 <fx:position srsName="urn:ogc:def:crs:EPSG::4326">
  <fb:pos>39.18777778 -76.68055556</fb:pos>
 </fx:position>
 <fx:predictedAirspeed uom="KT">120</fx:predictedAirspeed>
 <fx:time>
  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H26M55.000S</...>
 </fx:time>
</fx:point4D>
```

</p></td>
</tr>

<tr>
<td><p>

`11`

```xml
<fx:element 
 seqNum="10">
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

`72.45 NM`

```xml
<fx:alongRouteDistance 
 uom="NM">72.45</...>
```

`n/a`

</p></td>
<td><p>

`N39:10:33 W076:40:08` `143 ft` `Relative 00:27:15`

`100 kts`

`Airport Reference Loc.` `End Prediction Point`

```xml
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
  <fx:relativeTimeFromInitialPredictionPoint>P0Y0M0DT0H27M15.000S</...>
 </fx:time>
</fx:point4D>
```

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
			<!--
			The example uses the aerodrome reference location 
			as the Initial  Prediction Point. However, if known, 
			the specific departure runway location should be 
			included as precise trajectory start point, using 
			the appropriate point property (Wheels_off...).
			-->			
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

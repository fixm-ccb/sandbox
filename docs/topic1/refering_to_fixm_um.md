# References to the FIXM User Manual

The FIXM User Manual provides encoding guidance for the FIXM Core properties. Implementers of information services or systems that use FIXM 
may decide to integrate references to relevant pieces of encoding guidance from this manual into their own service/system documentation, 
for instance as part of the description of their information service payloads.

This page explains how the URLs for the encoding guidance of the FIXM User Manual are formed, in order to facilitate this type of integration.

## URL structure

The URLs for the encoding guidance of the FIXM User Manual are structured as follows:

```mermaid
flowchart LR
START(( ))
FIXM_UM_URL(<i>FIXM_UM_URL</i>)
SEPARATOR_1([/#/])
GUIDANCE_NAME(<i>GUIDANCE_NAME</i>)
SEPARATOR_2([/])
PACKAGE_NAME(<i>PACKAGE_NAME</i>)
END((( )))
ID([?id=])
MODEL_ELEMENT_NAME(<i>MODEL_ELEMENT_NAME</i>)

START --- FIXM_UM_URL
FIXM_UM_URL --- SEPARATOR_1
SEPARATOR_1 --- GUIDANCE_NAME
GUIDANCE_NAME --- SEPARATOR_2
SEPARATOR_2 --- PACKAGE_NAME
PACKAGE_NAME --- END
PACKAGE_NAME --- ID
ID --- MODEL_ELEMENT_NAME
MODEL_ELEMENT_NAME --- END
```
where

- *`[FIXM_UM_URL]`* shall take one of the following values 
  - `https://docs.fixm.aero`
    - IMPORTANT NOTE: When a new version of FIXM is released, a new version of the FIXM User Manual is deployed. `https://docs.fixm.aero` will always refer to the latest version of the FIXM User Manual. An implementer using URLs with `[FIXM_UM_URL]` = `https://docs.fixm.aero` runs the risk of refering eventually to a version of the FIXM User Manual that no longer matches the version of FIXM being implemented. 
  -   TODO : Should `https://docs-4-3-0.fixm.aero` be supported (and in the future `https://docs-4-4-0.fixm.aero` etc.), to enable the expression of URLs that are stable over time?

- *`[GUIDANCE_NAME]`* shall take the value `general-guidance`

- *`[PACKAGE_NAME]`* shall be the valid name of an official FIXM Core package, preceded by the prefix of the FIXM namespace in which that package exists. The prefix and the package name shall be separated by `_`.
  - Examples:
    - `fx_FlightData` for FIXM Core package `FlightData` that exists in namespace `xmlns:fx="http://www.fixm.aero/flight/4.3"`
    - `fb_Address` for FIXM Core package `Address` that exists in namespace `xmlns:fb="http://www.fixm.aero/base/4.3"`  
  - Practically, the list of valid entries for *`[PACKAGE_NAME]`* are:
    - For the `fx` namespace : `fx_Aircraft`, `fx_Arrival`, `fx_Capability`, `fx_Cargo`, `fx_Departure`, `fx_Emergency`, `fx_EnRoute`, `fx_FlightData`, `fx_RouteChanges`, `fx_RouteTrajectory`, `fx_Constraints`
    - For the `fb` namespace: `fb_Address`, `fb_AeronauticalReference`, `fb_Measures`, `fb_Organization`, `fb_RangesAndChoices`, `fb_Types`


- *`[MODEL_ELEMENT_NAME]`*, if provided, shall be
  - for an `fx_` package, the valid name (as defined in UML) of a FIXM Core property defined in that package, in lower case
    - Example: `aircraftidentification` for FIXM Core property `aircraftIdentification` defined in class `FlightIdentification` inside FIXM Core package `FlightData`
    - IMPORTANT NOTE: the name of the container class does not appear in the URL.
  - for an `fb_` package, the valid name (as defined in UML) of a FIXM Core class defined in that package, in lower case
    - Example: `onlinecontact` for FIXM Core class/type `OnlineContact` defined inside package `Address`

## Examples

Reference to the latest version of the encoding guidance for property `aircraftIdentification` defined in class `FlightIdentification` inside FIXM Core (Flight) package `FlightData`
- URL = `https://docs.fixm.aero/#/general-guidance/fx_FlightData?id=aircraftidentification`
  - *`[FIXM_UM_URL]`* = `https://docs.fixm.aero`
  - *`[GUIDANCE_NAME]`* = `general-guidance`
  - *`[PACKAGE_NAME]`* = `fx_FlightData`
  - *`[MODEL_ELEMENT_NAME]`* = `aircraftidentification`

Reference to the latest version of the encoding guidance for class `OnlineContact` defined inside FIXM Core (Base) package `Address`
- URL = `https://docs.fixm.aero/#/general-guidance/fb_Address?id=onlinecontact`
  - *`[FIXM_UM_URL]`* = `https://docs.fixm.aero`
  - *`[GUIDANCE_NAME]`* = `general-guidance`
  - *`[PACKAGE_NAME]`* = `fb_Address`
  - *`[MODEL_ELEMENT_NAME]`* = `onlinecontact`

Reference to the latest version of the encoding guidance for FIXM Core (Flight) package `Aircraft` as a whole 
- URL = `https://docs.fixm.aero/#/general-guidance/fx_Aircraft`
  - *`[FIXM_UM_URL]`* = `https://docs.fixm.aero`
  - *`[GUIDANCE_NAME]`* = `general-guidance`
  - *`[PACKAGE_NAME]`* = `fx_Aircraft`

Reference to the latest version of the encoding guidance for FIXM Core (Base) package `AeronauticalReference` as a whole 
- URL = `https://docs.fixm.aero/#/general-guidance/fb_AeronauticalReference`
  - *`[FIXM_UM_URL]`* = `https://docs.fixm.aero`
  - *`[GUIDANCE_NAME]`* = `general-guidance`
  - *`[PACKAGE_NAME]`* = `fb_AeronauticalReference`

Reference to the encoding guidance for FIXM Core `4.3.0` (Flight) package `Aircraft` as a whole  (WARNING not resolvable yet)
- URL = `https://docs-4-3-0.fixm.aero/#/general-guidance/fx_Aircraft`
  - *`[FIXM_UM_URL]`* = `https://docs-4-3-0.fixm.aero`
  - *`[GUIDANCE_NAME]`* = `general-guidance`
  - *`[PACKAGE_NAME]`* = `fx_Aircraft`


## Miscellaneous

The objective of the FIXM User Manual is to provide encoding guidance for the entire content of FIXM. Developing this encoding guidance is an iterative process, and it is possible that,
at a given point in time, some FIXM Core model elements do not have yet encoding guidance available in the FIXM User Manual. 

It may therefore happen that a URL is used in a third-party service/system documetation that conforms to the rules above, but that features a *`[MODEL_ELEMENT_NAME]`* for which no encoding guidance is available in the FIXM User Manual. Nevertheless, this URL will **remain resolvable** by mainstream web browsers, which will ignore the part of the URL `?id=...` and will display the top of the encoding guidance corresponding to the *`[PACKAGE_NAME]`*. When the missing piece of guidance becomes available in the FIXM User Manual, the URL will automatically point to the new correct section of the User Manual.



# Changelog
All notable changes to this project will be documented in this file.

## 3.1.1 - 2023-05-22
* Fixed ASP.NET (MVC) compatibility issue

## 3.1.0 - 2023-04-18
* Added a new methods:
    - `ActivateFeature` -> [`IsFeatureActive`](https://developers.kameleoon.com/csharp-sdk.html#isfeatureactive)
    - [`GetEngineTrackingCode`](https://developers.kameleoon.com/csharp-sdk.html#getenginetrackingcode) which can be used to simplify utilization of hybrid mode
* Renaming of methods:
    - `GetExperimentListForVisitorCode` -> [`GetExperimentListForVisitor`](https://developers.kameleoon.com/csharp-sdk.html#GetExperimentListForVisitor)
    - `GetFeatureListForVisitorCode` -> [`GetActiveFeatureListForVisitor`](https://developers.kameleoon.com/csharp-sdk.html#GetActiveFeatureListForVisitor)
    - `RetrieveDataFromRemoteSource` -> [`GetRemoteData`](https://developers.kameleoon.com/csharp-sdk.html#GetRemoteData)
* Fixed an issue that could possibly affect incorrect targeting for methods:
    - [`GetFeatureVariationKey`](https://developers.kameleoon.com/csharp-sdk.html#GetFeatureVariationKey)
    - [`GetFeatureVariable`](https://developers.kameleoon.com/csharp-sdk.html#GetFeatureVariable)

## 3.0.0 - 2022-12-09
* Added support of new feature flag rules:
    - [`GetFeatureVariationKey`](https://developers.kameleoon.com/csharp-sdk.html#GetFeatureVariationKey)
    - [`GetFeatureVariable`](https://developers.kameleoon.com/csharp-sdk.html#GetFeatureVariable)
* These methods returns **int** instead of **Int64** if variable has number type:
    - [`ObtainFeatureVariable`](https://developers.kameleoon.com/csharp-sdk.html#ObtainFeatureVariable)
    - [`GetFeatureAllVariables`](https://developers.kameleoon.com/csharp-sdk.html#GetFeatureAllVariables)
* These methods are synchronized now:
    - [`TriggerExperiment`](https://developers.kameleoon.com/csharp-sdk.html#triggerexperiment)
    - [`ActivateFeature`](https://developers.kameleoon.com/csharp-sdk.html#activatefeature)
* Renaming of methods (old methods marked as deprecated and will be removed later)
    - `ObtainVisitorCode` -> [`GetVisitorCode`](https://developers.kameleoon.com/csharp-sdk.html#GetVisitorCode)
    - `ObtainVariationAssociatedData` -> [`GetVariationAssociatedData`](https://developers.kameleoon.com/csharp-sdk.html#GetVariationAssociatedData),
    - `ObtainFeatureAllVariables` -> [`GetFeatureAllVariables`](https://developers.kameleoon.com/csharp-sdk.html#GetFeatureAllVariables),
    - `ObtainExperimentList` -> [`GetExperimentList`](https://developers.kameleoon.com/csharp-sdk.html#GetExperimentList),
    - `ObtainExperimentListForVisitorCode` -> [`GetExperimentListForVisitorCode`](https://developers.kameleoon.com/csharp-sdk.html#GetExperimentListForVisitorCode)
    - `ObtainFeatureList` -> [`GetFeatureList`](https://developers.kameleoon.com/csharp-sdk.html#GetFeatureList),
    - `ObtainFeatureListForVisitorCode` -> [`GetFeatureListForVisitorCode`](https://developers.kameleoon.com/csharp-sdk.html#GetFeatureListForVisitorCode)

## 2.2.1 - 2022-11-17
* Added possibility to set [`UserAgent`](https://developers.kameleoon.com/csharp-sdk.html#useragent).
* Minor bug improvements

## 2.2.0 - 2022-11-08
* Significantly improved configuration load time
* Added support for **Experiment** & **Exclusive Campaign** conditions. Related to [`triggerExperiment`](https://developers.kameleoon.com/csharp-sdk.html#triggerexperiment)
* Fixed an issue when an user which was already registered with a variation gets new randomly selected variation. Related to [`triggerExperiment`](https://developers.kameleoon.com/csharp-sdk.html#triggerexperiment)
* Added KameleoonData [`Device`](https://developers.kameleoon.com/csharp-sdk.html#device) data. Possible values are: **PHONE**, **TABLET**, **DESKTOP**.
* Removed KameleoonData `Interest`
* Added support of `is among the values` operator for Custom Data

## 2.1.9 - 2022-07-27
* Fixed naming: `ObtainFeatureAllVariable` -> `ObtainFeatureAllVariables`
* Minor bug fixes

## 2.1.8 - 2022-04-28
* Fixed issue where SDK could lose configuration and return exceptions (**Configuration Not Found**) for methods: [`ActivateFeature`](https://developers.kameleoon.com/csharp-sdk.html#activatefeature) and [`TriggerExperiment`](https://developers.kameleoon.com/csharp-sdk.html#triggerexperiment)
* Added [`default_timeout`](https://developers.kameleoon.com/csharp-sdk.html#additional-configuration) option to configuration file. It takes a value in milliseconds.

## 2.1.7 - 2022-04-25
* Added method to obtain a list of feature flags: [`ObtainFeatureList`](https://developers.kameleoon.com/csharp-sdk.html#obtainfeaturelist)
* Added method to obtain a list of feature flags targeted for specified visitor code: [`ObtainFeatureListForVisitorCode`](https://developers.kameleoon.com/csharp-sdk.html#obtainfeaturelistforvisitorcode)
* Added method to obtain a list of experiments: [`ObtainExperimentList`](https://developers.kameleoon.com/csharp-sdk.html#obtainexperimentlist)
* Added method to obtain a list of experiments targeted for specified visitor code: [`ObtainExperimentListForVisitorCode`](https://developers.kameleoon.com/csharp-sdk.html#obtainexperimentlistforvisitorcode)
* Added method to obtain all variables for feature flag: [`ObtainFeatureAllVariables`](https://developers.kameleoon.com/csharp-sdk.html#obtainfeatureallvariables)
* Added an indication of feature flag (Id, Key) when exception happens. Related to [`ActivateFeature`](https://developers.kameleoon.com/csharp-sdk.html#activatefeature), [`obtainFeatureVariable`](https://developers.kameleoon.com/csharp-sdk.html#obtainfeaturevariable)
* Added an indication of experiment (Id) when exception happens. Related to [`TriggerExperiment`](https://developers.kameleoon.com/csharp-sdk.html#triggerexperiment)

## 2.1.6 - 2022-04-12
* Fixed an issue where the experiment configuration and feature flags were not updated after the refresh interval had elapsed.

## 2.1.5 - 2022-04-12
* Added method for retrieving data from remote source: [`RetrieveDataFromRemoteSource`](https://developers.kameleoon.com/csharp-sdk.html#retrievedatafromremotesource)

## 2.1.4 - 2022-02-28
* Added support of multi-environment for feature flags, Related to [`ActivateFeature`](https://developers.kameleoon.com/csharp-sdk.html#activatefeature), [`ObtainFeatureVariable`](https://developers.kameleoon.com/csharp-sdk.html#obtainfeaturevariable)

## 2.1.3 - 2022-02-02
* Added .net framework 4.8 support

## 2.1.2 - 2022-01-27
* Added scheduling functionality for [`ActivateFeature`](https://developers.kameleoon.com/csharp-sdk.html#activatefeature)
* Added checking for status of site_code (Enable / Disable). Related to [`ActivateFeature`](https://developers.kameleoon.com/csharp-sdk.html#activatefeature) and trigger_experiment[`TriggerExperiment`](https://developers.kameleoon.com/csharp-sdk.html#triggerexperiment)

## 2.1.1 - 2021-02-16
* Updated the configuration file path.
* Added obtainFeatureVariable() method.



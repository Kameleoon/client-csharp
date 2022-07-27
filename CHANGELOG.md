# Changelog
All notable changes to this project will be documented in this file.

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



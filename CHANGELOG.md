# Changelog
All notable changes to this project will be documented in this file.

## 4.16.0 - 2025-07-23
### Features
* Added the [`EvaluateAudiences`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#evaluateaudiences) method. This method iterates over all Audiences Explorer segments, evaluates each one, and tracks the segments for which the visitor is targeted using the [`TARGETINGSEGMENT`](https://developers.kameleoon.com/apis/data-api-rest/all-endpoints/post-visit-events/) event.

## 4.15.0 - 2025-06-27
### Features
* Added support for using a Custom Data value for traffic bucketing instead of the default visitor code. [Learn More](https://help.kameleoon.com/create-feature-flag/#Advanced_Flag_Settings).
* Reduced the number of requests to OAuth service if it has outage.

## 4.14.0 - 2025-05-26
### Features
* Added support for **304 (Not Modified)** responses from the SDK config service to avoid redundant updates and reduce traffic when the configuration hasn't changed.
* Added support for a **New**/**Returning** visitor breakdown filter in reports (requires calling [`GetRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getremotevisitordata)).
### Fixed
* Fixed an issue where visitor data fields - [`Browser`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#browser), [`Device`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#device), and [`OperatingSystem`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#operatingsystem) - were all retrieved from the Data API and added to the visitor, even when only a subset of them was requested.

## 4.13.1 - 2025-04-08
### Bug fixes
* Changed the order in which **conversion** and **experiment** events are sent. This may lead to more accurate **visit**-level experiment reporting.

## 4.13.0 - 2025-03-24
### Features
* Added new optional parameters `negative` and `metadata` to the [`TrackConversion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#trackconversion) method.
* Added new optional parameter `metadata` to the [`Conversion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#conversion) data constructor.
* Changed the log level for deprecated methods from **WARNING** to **INFO**.

## 4.12.0 - 2025-03-18
### Features
* Added support for Contextual Bandit evaluations. Calling [`GetRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getremotevisitordata) with the `cbs=true` flag is required for this feature to function correctly. Platform-wide release expected in March 2025.

## 4.11.0 - 2025-02-26
### Features
* Added SDK support for **Mutually Exclusive Groups**. When feature flags are grouped into a **Mutually Exclusive Group**, only one flag in the group will be evaluated at a time. All other flags in the group will automatically return their default variation.
* Added new configuration parameter `networkDomain` (`network_domain`) to [`KameleoonClientConfig`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#additional-configuration) and the [configuration](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#additional-configuration) file. This parameter allows specifying a custom domain for all outgoing network requests.
* Added support for new conditions:
    - Exclusive Campaign
    - Experiment
    - Personalization

## 4.10.0 - 2025-02-10
### Features
* Added SDK support for **holdout experiments**. Visitors assigned to a holdout experiment are excluded from all other rollouts and experiments, and consistently receive the default variation. For visitors not in a holdout experiment, the standard evaluation process applies, allowing them to be evaluated for all feature flags as usual. Platform-wide release expected in February 2025.
### Bug fixes
* Stability and performance improvements.

## 4.9.1 - 2024-12-12
### Bug fixes
* Fixed an issue where simulated variations were not removed for a visitor during their session, causing them to persist until a new session started.

## 4.9.0 - 2024-12-05
### Features
* Added support for **simulated** variations.
* Added the [`SetForcedVariation()`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#setforcedvariation) method. This method allows explicitly setting a forced variation for a visitor, which will be applied during experiment evaluation.
### Bug fixes
* Fixed an issue where random visitor codes were not being generated correctly on the [.NET Framework](https://dotnet.microsoft.com/en-us/download/dotnet-framework).
* Fixed an issue where the [`Variation.IsActive`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#variation) property returned an incorrect value.

## 4.8.1 - 2024-11-20
### Bug fixes
* Resolved an issue where the validation of [top-level domains](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#additional-configuration) for `localhost` resulted in incorrect failures. The SDK now accepts the provided domain without modification if it is deemed invalid and logs an [error](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#log-levels) to notify you of any issues with the specified domain.


## 4.8.0 - 2024-11-14
### Features
* Introduced a new `visitorCode` parameter to [`RemoteVisitorDataFilter`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#using-parameters-in-getremotevisitordata). This parameter determines whether to use the `visitorCode` from the most recent previous visit instead of the current `visitorCode`. When enabled, this feature allows visitor exposure to be based on the retrieved `visitorCode`, facilitating [cross-device reconciliation](https://developers.kameleoon.com/core-concepts/cross-device-experimentation/). Default value of the parameter is `true`.
### Bug fixes
* Fixed an issue with the [`Page URL`](https://developers.kameleoon.com/feature-management-and-experimentation/using-visit-history-in-feature-flags-and-experiments/#benefits-of-calling-getremotevisitordata) and [`Page Title`](https://developers.kameleoon.com/feature-management-and-experimentation/using-visit-history-in-feature-flags-and-experiments/#benefits-of-calling-getremotevisitordata) targeting conditions, where the condition evaluated all previously visited URLs in the session instead of only the current URL, corresponding to the latest added [`PageView`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#pageview).<br/>
**NOTE**: This change may impact your existing targeting. Please review your targeting conditions to ensure accuracy.


## 4.7.0 - 2024-10-04
### Features
* Introduced new evaluation methods for clarity and improved efficiency when working with the SDK:
  - [`GetVariation`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#getvariation)
  - [`GetVariations`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#getvariations)
* These methods replace the deprecated ones:
  - [`GetFeatureVariationKey`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getfeaturevariationkey)
  - [`GetFeatureVariable`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getfeaturevariable)
  - [`GetActiveFeatures`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getactivefeatures)
  - [`GetFeatureVariationVariables`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getfeaturevariationvariables)
* A new version of the [`IsFeatureActive`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#isfeatureactive) method now includes an optional `track` parameter, which controls whether the assigned variation is tracked (default: `true`).
* Enhanced top-level domain validation within the SDK. The implementation now includes automatic trimming of extraneous symbols and provides a [warning](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#log-levels) when an invalid domain is detected.
* Enhanced the [`GetEngineTrackingCode`](https://developers.kameleoon.com/csharp-sdk.html#getenginetrackingcode) method to properly handle `JS` and `CSS` variables.

## 4.6.2 - 2024-08-13
### Bug fixes
* Fixed an issue that caused duplicate entries in feature flag results for both anonymous and authorized/identified visitors during data reconciliation. This problem occurred when custom data of type mapping ID was not consistently sent for all sessions.

## 4.6.1 - 2024-08-02
### Bug fixes
* Resolved an issue where the SDK could become stuck during prolonged Data API outages.

## 4.6.0 - 2024-07-11
### Features
* Enhanced [logging](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#logging):
    - Introduced [log levels](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#log-levels):
        - `None`
        - `Error`
        - `Warning`
        - `Info`
        - `Debug`
    - Added support for [custom logger](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#custom-handling-of-logs) implementations.
* Improved the tracking mechanism to consolidate multiple visitors into a single request. The new approach combines information on all affected visitors into one request, which is sent once per interval.
* Added a new variation of the [`Flush(bool instant, string visitorCode)`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#flush) with `instant` parameter. If the parameter's value is `true` the visitor's data is tracked instantly. Otherwise, the visitor's data will be tracked with next tracking interval. Default value of the parameter is `false`.
* Added new configuration parameter `trackingIntervalMilliseconds` (`tracking_interval_millisecond`) to [`KameleoonClientConfig`](https://developers.kameleoon.com/csharp-sdk.html#additional-configuration) and the [configuration](https://developers.kameleoon.com/csharp-sdk.html#additional-configuration) file, which is used to set interval for tracking requests. Default value is `1000` milliseconds.
* New Kameleoon Data type [`UniqueIdentifier`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#uniqueidentifier) is introduced. It will be used in all methods instead of `isUniqueIdentifier` parameter:
    - [`Flush`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#flush)
    - [`TrackConversion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#trackconversion)
    - [`GetFeatureVariationKey`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getfeaturevariationkey)
    - [`GetFeatureVariable`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getfeaturevariable)
    - [`IsFeatureActive`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#isfeatureactive)
    - [`GetRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getremotevisitordata)
### Bug fixes
* Resolved an issue where the [`Flush(null, isUniqueIdentifier)`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#flush) method was incorrectly sending requests with `isUniqueIdentifier` applied to each visitor. Now, `isUniqueIdentifier` is only considered if `visitorCode` is provided and not null.

## 4.5.1 - 2024-07-08
### Bug fixes
* Resolved an issue on the [.NET Framework](https://dotnet.microsoft.com/en-us/download/dotnet-framework) platform that could generate duplicate visitor codes and tracking calls with a nonce number.

## 4.5.0 - 2024-06-07
### Features
The [Likelihood to convert](https://developers.kameleoon.com/feature-management-and-experimentation/using-visit-history-in-feature-flags-and-experiments) targeting condition is now available. Pre-loading the data is required using [`GetRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getremotevisitordata) with the `kcs` parameter set to `true`.
### Bug fixes
* When using the [`addData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#adddata) method, [`UserAgent`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#useragent) verification is no longer performed.

## 4.4.6 - 2024-05-22
### Bug fixes
* Resolved an issue where the "Kameleoon Segment" condition could occasionally return incorrect targeting results.

## 4.4.5 - 2024-05-06
### Bug fixes
* Stability and performance improvements.

## 4.4.4 - 2024-05-02
### Bug fixes
* The number of concurrent connections per server that you can specify with [MaxConnectionsPerServer](https://learn.microsoft.com/en-us/dotnet/api/system.net.http.httpclienthandler.maxconnectionsperserver?view=netstandard-2.0) for [HttpClientHandler](https://learn.microsoft.com/en-us/dotnet/api/system.net.http.httpclienthandler?view=netstandard-2.0) is now limited to a maximum value of 20.

## 4.4.3 - 2024-04-27
### Bug fixes
* Fixed a problem that occurred when passing an incorrect [User-Agent](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#useragent) value.

## 4.4.2 - 2024-04-25
### Bug fixes
* Disabled logging of failed requests to [Data API](https://developers.kameleoon.com/apis/data-api-rest/all-endpoints/post-visit-events/) flagged due to the user agent being identified as a bot (status code equals 403)

## 4.4.1 - 2024-04-01
### Bug fixes
* Stability and performance improvements.


## 4.4.0 - 2024-03-27
### Features
* Added a new optional parameter `isUniqueIdentifier` that provides additional capabilities with [cross-device experimentation](https://developers.kameleoon.com/core-concepts/cross-device-experimentation) in the following methods:
    - [`Flush`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#flush)
    - [`TrackConversion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#trackconversion)
    - [`GetFeatureVariationKey`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getfeaturevariationkey)
    - [`GetFeatureVariable`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getfeaturevariable)
    - [`IsFeatureActive`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#isfeatureactive)
    - [`GetRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getremotevisitordata)
* New [targeting conditions](https://developers.kameleoon.com/feature-management-and-experimentation/using-visit-history-in-feature-flags-and-experiments) are now available (some of them may require pre-loading the data using [`GetRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#getremotevisitordata)):
    - Browser Cookie
    - Operating System
    - IP Geolocation
    - Kameleoon Segment
    - Target Feature Flag
    - Previous Page
    - Number of Page Views
    - Time since First Visit
    - Time since Last Visit
    - Number of Visits Today
    - Total Number of Visits
    - New or Returning Visitor
* Introduced new Kameleoon Data types:
    - [`Cookie`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#cookie)
    - [`OperatingSystem`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#operatingsystem)
    - [`Geolocation`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#geolocation)
* Changed the parameter `title` in data object [`PageView`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#pageview) to optional.

## 4.3.0 - 2024-02-16
### Features
* Added support for additional Data API servers across the world for even faster network requests.
* Increased limit for requests to Data API: [rate limits](https://developers.kameleoon.com/apis/data-api-rest/overview/#rate-limits)
* Added [`GetVisitorWarehouseAudience`](https://developers.kameleoon.com/csharp-sdk.html#getvisitorwarehouseaudience) method to retrieve all data associated with a visitor's warehouse audiences and adds it to the visitor.
### Bug fixes
* Stability and performance improvements.

## 4.2.3 - 2024-02-12
### Bug fixes
* Fixed issue when improper `Expires` cookie field value of visitor code cookie on .NET Framework.

## 4.2.2 - 2024-01-26
### Bug fixes
* Resolved an issue where the [`GetActiveFeatures`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#getactivefeatures) could throw `NullReferenceException` in certain cases if your project configuration is empty.


## 4.2.1 - 2023-12-21
### Features
* Added new fields to `Variation` in [`GetActiveFeatures`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#getactivefeatures) method:
    - `Id`
    - `ExperimentId`

## 4.2.0 - 2023-12-19
### Features
* Added [`GetActiveFeatures`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#getactivefeatures) method. It retrieves information about the active feature flags that are available for a specific visitor code. This method replaces the deprecated [`GetActiveFeatureListForVisitor`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#getactivefeaturelistforvisitor) method.
### Bug fixes
* Updated vulnerable dependencies `System.Text.Encodings.Web`, `System.Text.RegularExpressions`, `Newtonsoft.Json`.

## 4.1.3 - 2023-12-06
### Bug fixes
* A compatibility issue that prevented the C# SDK from working as intended with the .NET Framework has been fixed. The SDK now ensures compatibility with the .NET framework. The minimum supported .NET Framework version is now [4.6.1](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net461).

## 4.1.2 - 2023-11-21
### Bug fixes
* Stability and performance improvements.

## 4.1.1 - 2023-11-10
### Bug fixes
* Resolved an issue where the [`WaitInit`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#waitinit) method could crash during initialization.

## 4.1.0 - 2023-11-03
### Features
* Added [`WaitInit`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#waitinit) method, which allows you to check if the client has been successfully initialized before proceeding with other operations.

## 4.0.0 - 2023-11-03
### Breaking changes
* Removed all methods and exceptions related to **experiments**:
    - `TriggerExperiment`
    - `GetVariationAssociatedData` (`ObtainVariationAssociatedData`)
    - `ObtainFeatureVariable`
    - `ObtainFeatureAllVariables`
    - `GetExperimentList` (`ObtainExperimentList`)
    - `GetExperimentListForVisitor` (`ObtainExperimentListForVisitorCode`)
    - `ExperimentConfigurationNotFound`
    - `NotTargeted`
    - `NotAllocated`
    - `SiteCodeDisabled`
* Removed methods that were deprecated in 3.x versions:
    - `ActivateFeature`
    - `ObtainFeatureList`
    - `ObtainFeatureListForVisitorCode`
    - `ObtainFeatureVariable`
    - `ObtainVisitorCode`
    - `RetrieveDataFromRemoteSource`
* Renamed classes, methods and exceptions:
    - `GetFeatureAllVariables` to [`GetFeatureVariationVariables`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#getfeaturevariationvariables)
    - `ForgetClient` to `Forget`
    - `FeatureConfigurationNotFound` to `FeatureNotFound`
    - `VariationConfigurationNotFound` to `FeatureVariationNotFound`
    - `VariableConfigurationNotFound` to `FeatureVariableNotFound`
    - `CredentialsNotFound` to `ConfigCredentialsInvalid`
    - `EmptySiteCode` to `SiteCodeIsEmpty`
    - `VisitorCodeNotValid` to `VisitorCodeInvalid`
* Changes in the [configuration](https://developers.kameleoon.com/csharp-sdk.html#additional-configuration) file:
    - removed `visitor_data_maximum_size`
    - renamed `actions_configuration_refresh_interval` to `refresh_interval_minute`
    - renamed `default_timeout` to `default_timeout_millisecond`
* Added new exception `FeatureEnvironmentDisabled` indicating that the feature flag is disabled for certain environments. The following methods can throw the new exception:
    - [`GetFeatureVariationKey`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#getfeaturevariationkey)
    - [`GetFeatureVariable`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#getfeaturevariable)
    - [`GetFeatureVariationVariables`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#getfeaturevariationvariables)
* Changed the field `value` of the [`UserAgent`](https://developers.kameleoon.com/csharp-sdk.html#useragent) data type to the property `Value`.
* Removed parameter `topLevelDomain` from [`GetVisitorCode`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#getvisitorcode). Instead, use the `top_level_domain` parameter in the [configuration](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#additional-configuration)
* Removed parameters `clientId` and `clientSecret` from [`KameleoonClientFactory.Create`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk#create)

### Features
* Added [`SetLegalConsent`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#setlegalconsent) method to determine the types data Kameleoon includes in tracking requests. This helps you adhere to legal and regulatory requirements while responsibly managing visitor data. You can find more information in the [Consent management policy](https://help.kameleoon.com/consent-management-policy/).
* Added **KameleoonClientConfig**, which can be used as parameter during initialization of a client. Related to [`KameleoonClientFactory.Create`](https://developers.kameleoon.com/java-sdk.html#com-kameleoon-kameleoonclientfactory)
* Added new configuration fields to external [configuration](https://developers.kameleoon.com/csharp-sdk.html#additional-configuration) file:
    - `top_level_domain` which is used to set the domain name
    - `session_duration_minute` that designates the predefined time interval that Kameleoon stores the visitor and their associated data in memory.

### Bug fixes
* Stability and performance improvements.

## 3.3.2 - 2023-07-26
* Stability and performance improvements.

## 3.3.1 - 2023-07-24
* Stability and performance improvements.

## 3.3.0 - 2023-06-29
* Added method to fetch remote visitor's data (with an optional capability to add data for a visitor):
    - [`GetRemoteVisitorData`](https://developers.kameleoon.com/csharp-sdk.html#getremotevisitordata)
* Added new conditions for targeting:
    - `Visitor Code`
    - `SDK Language`
    - [`Page Title & Page Url`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#pageview)
    - [`Browser`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#browser)
    - [`Device`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#device)
    - [`Conversion`](https://developers.kameleoon.com/feature-management-and-experimentation/web-sdks/csharp-sdk/#trackconversion)

## 3.2.0 - 2023-06-06
* Added `KameleoonException.InvalidConfigurationData` and `KameleoonException.EmptySiteCode` exceptions
* Added `KameleoonClientFactory.ForgetClient` static method (`KameleoonClientFactory.Forget` is marked as deprecated)
* Removed `KameleoonClientImpl.EnableProxySupport` method

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
* Added possibility for [`CustomData`](https://developers.kameleoon.com/csharp-sdk.html#customdata) to use variable argument list of values

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



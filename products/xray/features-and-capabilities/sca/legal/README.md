# Legal

Open Source Software (OSS) License Compliance is a crucial aspect of software development that demands meticulous attention to various licensing permissions, conditions, and limitations to prevent legal and financial repercussions. The complexity arises from the diverse range of OSS licenses, each associated with specific permissions regarding usage, modification, and distribution, as well as conditions that may impose requirements like attribution or copyleft stipulations. Additionally, limitations can restrict how software may be integrated or redistributed. Organizations must navigate this intricate landscape, ensuring that their use of OSS components aligns with the particular terms of each license while managing software composition that may introduce further compliance risks. JFrog Xray simplifies OSS license compliance by providing comprehensive visibility into the open source components within your software projects. It automatically scans and analyzes your software components, identifying licensing permissions, conditions, and limitations in real time. JFrog Xray empowers organizations to make informed decisions, streamline compliance processes, and maintain adherence to OSS licensing obligations by offering detailed reports and insights that categorize licenses and their implications.

## OSS Licensing Features

### License Detection

* Xray has a state-of-art license detection engine which identifies your software packages' software licenses (both 3rd party and internal)&#x20;
* Xray licenses engine can detect licenses from your  scanned artifact or enrich externally-linked from external sources
* Xray supports custom software licenses for Xray to detect based on the license text and create violations based on it&#x20;

### License Management&#x20;

* Xray supports manual assignment of component licenses, allowing fine-grain control and flexibility with managing your software licenses &#x20;
* Xray Support automatic license conclusion - allowing you to resolve dual licensing packages to the most permissive license available

### License Export&#x20;

* Xray allows you to export a detailed report of all your software licenses&#x20;
* The report includes all component identifiers, component versions, license identifiers, and full license text links.
* Supported formats include PDF, JSON, and CSV

### Attribution Report

An attribution report is a concise document that outlines the open source components used in a software project, detailing their respective licenses and required attributions for compliance. This report is essential for organizations to fulfill obligations mandated by various OSS licenses, which often require proper credit given to original authors when their software is used, modified, or redistributed. Common examples of these licenses include the MIT License, which requires attribution but has minimal restrictions on usage, and the Apache License 2.0, which allows for modifications and redistribution but requires a separate NOTICE file that provides further acknowledgment and clarifies the use of the licensed components, ensuring compliance with attribution requirements.

* Xray Attribution Report will include
  * Component Identifiers
  * Associated Licenses&#x20;
  * Copyright Information
  * Full License Text of License&#x20;
  * Additional Required Notices
* Supported in PDF only


---
layout: "documentation"
category: "voltmx_foundry_linux_install_guide"
---
                          

You are here: Upgrading Volt MX Foundry

Upgrading Volt MX Foundry
========================

This section explains upgrading Volt MX Foundry Components through the installer. For an upgrade to work, the minimum installation version should be Foundry 7.x.GA / 8.4.X.GA.

> **_Important:_** Before you upgrade Foundry, refer to the [Certified and Supported Configurations]({{ site.baseurl }}/docs/documentation/Foundry/voltmxfoundry_supported_devices_os_browsers/Content/Introduction.html), and make sure that you upgrade the underlying software stack. For example, to upgrade to Foundry V9 ServicePack 1, you first need to upgrade MySQL to version 5.7.

> **_Note:_** If you are using Volt MX Foundry 6.5.X you must first upgrade to a 7.X version using the latest 7.X installer available at the [downloads archive](https://community.hclvoltmx.com/downloads/archive) page.

*   [Prerequisites for Upgrade from Foundry 7.x to Foundry 8.x](UpgradePrereqs.html): While upgrading Foundry 7.0/7.1 to Foundry V8.x for any selected database, you must remove the version\_rank column from the schema\_version table in the `idglobaldb` before the upgrade.
*   [Upgrading Volt MX Foundry to V9 or later](Upgrading_VoltMX_Foundry_SP1.html): You can upgrade to Volt MX Foundry V9 by providing the existing Foundry database details.
*   [Upgrading the Custom Metrics](CustomMetrics.html)

---
title: TenantLockdown CSP
description: To lock a device to a tenant to prevent accidental or intentional resets or wipes, use the TenantLockdown configuration service provider.
ms.author: dansimp
ms.topic: article
ms.prod: w10
ms.technology: windows
author: dansimp
ms.date: 08/13/2018
ms.reviewer: 
manager: dansimp
---

# TenantLockdown CSP

> [!WARNING]
> Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here. This CSP was added in Windows 10, version 1809.

The TenantLockdown configuration service provider is used by the IT admin to lock a device to a tenant, which ensures that the device remains bound to the tenant if accidental or intentional resets or wipes occur.

> [!NOTE]
> The forced network connection is only applicable to devices after reset (not new).

The following example shows the TenantLockdown configuration service provider in tree format.
```
./Vendor/MSFT
TenantLockdown
----RequireNetworkInOOBE
```
<a href="" id="tenantlockdown"></a>**./Vendor/MSFT/TenantLockdown**  
The root node.

<a href="" id="requirenetworkinoobe"></a>**RequireNetworkInOOBE**  
Specifies whether to require a network connection during the out-of-box experience (OOBE) at first sign in.

When RequireNetworkInOOBE is true, when the device goes through OOBE at first sign in or after a reset, the user is required to choose a network before proceeding. There's no "skip for now" option.

Value type is bool. Supported operations are Get and Replace.

-  True - Require network in OOBE  
-  False - No network connection requirement in OOBE

Example scenario:  Henry is the IT admin at Contoso. He deploys 1000 devices successfully with RequireNetworkInOOBE set to true. When users accidentally or intentionally reset their device, they're required to connect to a network before they can proceed. Upon successful connection, users see the Contoso branded sign-in experience where they must use their Azure AD credentials. There's no option to skip the network connection and create a local account.

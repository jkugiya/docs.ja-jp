---
description: 詳細については、「<System.servicemodel」を参照してください>
title: <system.serviceModel.activation>
ms.date: 03/30/2017
ms.assetid: c0cae85f-56cb-4030-8807-6f96edff8d2d
ms.openlocfilehash: 4da87248426f5da3c53a03d5f307a174b2b0dfc7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682606"
---
# \<system.serviceModel.activation>

<span data-ttu-id="888aa-103">この構成セクションは、SMSvcHost.exe ツールの構成設定を表します。</span><span class="sxs-lookup"><span data-stu-id="888aa-103">This configuration section represents the configuration settings for the SMSvcHost.exe tool.</span></span> <span data-ttu-id="888aa-104">構成要素は、SMSvcHost.exe.config ファイルで構成できます。</span><span class="sxs-lookup"><span data-stu-id="888aa-104">The configuration elements can be configured in the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="888aa-105">特にここには、構成される必要があるコンピューター全体のすべての設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="888aa-105">Specifically, it includes all machine-wide settings that must be configured.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel.activation>**  
  
## <a name="sample-configuration-file"></a><span data-ttu-id="888aa-106">サンプル構成ファイル</span><span class="sxs-lookup"><span data-stu-id="888aa-106">Sample Configuration File</span></span>  

 <span data-ttu-id="888aa-107">次は、リスナー プロセス SMSvcHost.exe で使用されるサンプル構成ファイル (SMSvcHost.exe.config) です。</span><span class="sxs-lookup"><span data-stu-id="888aa-107">The following is a sample configuration file (SMSvcHost.exe.config), which is used by the listener process SMSvcHost.exe.</span></span>  
  
```xml  
<configuration>
  <runtime>
    <gcConcurrent enabled="false" />
  </runtime>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="10"
             maxPendingAccepts="2"
             maxPendingConnections="100"
             receiveTimeout="00:00:10"
             teredoEnabled="false">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
    <net.pipe maxConnectionsPendingDispatch="100"
              maxPendingAccepts="2"
              receiveTimeout="00:00:10">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
    <diagnostics performanceCountersEnabled="true" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="888aa-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="888aa-108">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration>

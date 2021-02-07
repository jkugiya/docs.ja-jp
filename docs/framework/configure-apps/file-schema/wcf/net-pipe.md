---
description: 詳細については、「net.pipe>」を参照してください <
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: d95aebc62ab92b91c1633a99d8311b55bfaaf0d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684075"
---
# \<net.pipe>

<span data-ttu-id="0ce13-103">名前付きパイプ接続の有効期間を管理し、名前付きパイプを介して到着するアクティベーション要求を処理する名前付きパイプ アクティベーション サービスの構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="0ce13-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**  
  
## <a name="syntax"></a><span data-ttu-id="0ce13-104">構文</span><span class="sxs-lookup"><span data-stu-id="0ce13-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="0ce13-105">Type</span><span class="sxs-lookup"><span data-stu-id="0ce13-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ce13-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0ce13-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0ce13-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0ce13-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ce13-108">属性</span><span class="sxs-lookup"><span data-stu-id="0ce13-108">Attributes</span></span>  
  
|<span data-ttu-id="0ce13-109">属性</span><span class="sxs-lookup"><span data-stu-id="0ce13-109">Attribute</span></span>|<span data-ttu-id="0ce13-110">説明</span><span class="sxs-lookup"><span data-stu-id="0ce13-110">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="0ce13-111">整数は、共有サービスの待機エンドポイントで同時に受け入れる未処理のスレッドの最大数を示しています。</span><span class="sxs-lookup"><span data-stu-id="0ce13-111">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="0ce13-112">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="0ce13-112">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="0ce13-113">ディスパッチを待機できる最大接続数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="0ce13-113">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="0ce13-114">既定値は、100 です。</span><span class="sxs-lookup"><span data-stu-id="0ce13-114">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="0ce13-115">フレーム データを読み取り、基礎となる接続から接続ディスパッチを実行するタイムアウトを指定する <xref:System.TimeSpan> です。</span><span class="sxs-lookup"><span data-stu-id="0ce13-115">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="0ce13-116">既定値は "00:00:10" です。</span><span class="sxs-lookup"><span data-stu-id="0ce13-116">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ce13-117">子要素</span><span class="sxs-lookup"><span data-stu-id="0ce13-117">Child Elements</span></span>  
  
|<span data-ttu-id="0ce13-118">要素</span><span class="sxs-lookup"><span data-stu-id="0ce13-118">Element</span></span>|<span data-ttu-id="0ce13-119">説明</span><span class="sxs-lookup"><span data-stu-id="0ce13-119">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="0ce13-120">`securityIdentifier`WCF サービスをホストするプロセスのユーザーアカウントを指定する属性を含む構成要素のコレクション。共有サービスへの接続アクセス権が付与されます。</span><span class="sxs-lookup"><span data-stu-id="0ce13-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0ce13-121">親要素</span><span class="sxs-lookup"><span data-stu-id="0ce13-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0ce13-122">要素</span><span class="sxs-lookup"><span data-stu-id="0ce13-122">Element</span></span>|<span data-ttu-id="0ce13-123">説明</span><span class="sxs-lookup"><span data-stu-id="0ce13-123">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="0ce13-124">リスナー プロセス SMSvcHost.exe の設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0ce13-124">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ce13-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ce13-125">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>

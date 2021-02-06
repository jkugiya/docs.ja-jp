---
description: 詳細については <behavior> 、 <serviceBehaviors>
title: <behavior> の <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: e34254661026ad6dcb3429ad1b381cc3e6718f27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639537"
---
# <a name="behavior-of-servicebehaviors"></a><span data-ttu-id="249a7-103">\<behavior> の \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="249a7-103">\<behavior> of \<serviceBehaviors></span></span>

<span data-ttu-id="249a7-104">`behavior` 要素には、サービスの動作設定のコレクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="249a7-104">The `behavior` element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="249a7-105">各動作には、それぞれの `name` によってインデックスが付けられます。</span><span class="sxs-lookup"><span data-stu-id="249a7-105">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="249a7-106">サービスは、要素の属性を使用して、この名前を使用して各動作にリンクでき `behaviorConfiguration` [\<endpoint>](endpoint-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="249a7-106">Services can link to each behavior through this name using the `behaviorConfiguration` attribute of the [\<endpoint>](endpoint-element.md) element.</span></span> <span data-ttu-id="249a7-107">これにより、設定を再定義することなく、エンドポイント間で共通の動作構成を共有できます。</span><span class="sxs-lookup"><span data-stu-id="249a7-107">This allows endpoints to share common behavior configurations without redefining the settings.</span></span> <span data-ttu-id="249a7-108">.NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="249a7-108">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="249a7-109">既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="249a7-109">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="249a7-110">要素など、Windows Workflow アクティビティに固有の動作要素について [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) は[ \<behavior> \<serviceBehaviors> ](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) 、「」ページで説明されています。</span><span class="sxs-lookup"><span data-stu-id="249a7-110">Behavior elements specific to Windows Workflow activities, such as the [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) element, are documented in the [\<behavior> of \<serviceBehaviors>](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) page.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="249a7-111">構文</span><span class="sxs-lookup"><span data-stu-id="249a7-111">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="249a7-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="249a7-112">Attributes and Elements</span></span>  

 <span data-ttu-id="249a7-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="249a7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="249a7-114">属性</span><span class="sxs-lookup"><span data-stu-id="249a7-114">Attributes</span></span>  
  
|<span data-ttu-id="249a7-115">属性</span><span class="sxs-lookup"><span data-stu-id="249a7-115">Attribute</span></span>|<span data-ttu-id="249a7-116">説明</span><span class="sxs-lookup"><span data-stu-id="249a7-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="249a7-117">name</span><span class="sxs-lookup"><span data-stu-id="249a7-117">name</span></span>|<span data-ttu-id="249a7-118">動作の構成名を含む一意の文字列。</span><span class="sxs-lookup"><span data-stu-id="249a7-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="249a7-119">この値は、要素の識別文字列として機能するため、一意のユーザー定義の文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="249a7-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="249a7-120">.NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="249a7-120">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="249a7-121">既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="249a7-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="249a7-122">子要素</span><span class="sxs-lookup"><span data-stu-id="249a7-122">Child Elements</span></span>  
  
|<span data-ttu-id="249a7-123">要素</span><span class="sxs-lookup"><span data-stu-id="249a7-123">Element</span></span>|<span data-ttu-id="249a7-124">説明</span><span class="sxs-lookup"><span data-stu-id="249a7-124">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|<span data-ttu-id="249a7-125">DataContractSerializer 用の構成データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="249a7-125">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<persistenceProvider>](persistenceprovider.md)|<span data-ttu-id="249a7-126">使用する永続化プロバイダーの実装の型と、永続化操作に使用するタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="249a7-126">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>|  
|[\<routing>](routing-of-servicebehavior.md)|<span data-ttu-id="249a7-127">ルーティング構成の動的な変更を可能にするルーティング サービスへの実行時アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="249a7-127">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|<span data-ttu-id="249a7-128">サービス レベルで転送、メッセージ、または送信元の有効性を確立するワークフロー構成要素を提供します。</span><span class="sxs-lookup"><span data-stu-id="249a7-128">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|<span data-ttu-id="249a7-129">サービス操作へのアクセスを承認する設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="249a7-129">Specifies settings that authorize access to service operations.</span></span>|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="249a7-130">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="249a7-130">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>|  
|[\<serviceDebug>](servicedebug.md)|<span data-ttu-id="249a7-131">Windows Communication Foundation (WCF) サービスのデバッグ機能とヘルプ情報機能を指定します。</span><span class="sxs-lookup"><span data-stu-id="249a7-131">Specifies debugging and help information features for a Windows Communication Foundation (WCF) service.</span></span>|  
|[\<serviceDiscovery>](servicediscovery.md)|<span data-ttu-id="249a7-132">サービス エンドポイントの探索可能性を指定します。</span><span class="sxs-lookup"><span data-stu-id="249a7-132">Specifies the discoverability of service endpoints.</span></span>|  
|[\<serviceMetadata>](servicemetadata.md)|<span data-ttu-id="249a7-133">サービス メタデータと関連情報の公開を指定します。</span><span class="sxs-lookup"><span data-stu-id="249a7-133">Specifies the publication of service metadata and associated information.</span></span>|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|<span data-ttu-id="249a7-134">サービス操作中にセキュリティ イベントの監査を有効にする設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="249a7-134">Specifies settings that enable auditing of security events during service operations.</span></span>|  
|[\<serviceThrottling>](servicethrottling.md)|<span data-ttu-id="249a7-135">WCF サービスの制限メカニズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="249a7-135">Specifies the throttling mechanism of a WCF service.</span></span>|  
|[\<serviceTimeouts>](servicetimeouts.md)|<span data-ttu-id="249a7-136">サービスのタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="249a7-136">Specifies the timeout for a service.</span></span>|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="249a7-137">ワークフローベースの WCF サービスをホストするための WorkflowRuntime のインスタンスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="249a7-137">Specifies settings for an instance of WorkflowRuntime for hosting workflow-based WCF services.</span></span>|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="249a7-138">メタデータのアドレス情報を要求メッセージ ヘッダーから取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="249a7-138">Enables the retrieval of metadata address information from the request message headers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="249a7-139">親要素</span><span class="sxs-lookup"><span data-stu-id="249a7-139">Parent Elements</span></span>  
  
|<span data-ttu-id="249a7-140">要素</span><span class="sxs-lookup"><span data-stu-id="249a7-140">Element</span></span>|<span data-ttu-id="249a7-141">説明</span><span class="sxs-lookup"><span data-stu-id="249a7-141">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="249a7-142">サービス動作要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="249a7-142">A collection of service behavior elements.</span></span>|

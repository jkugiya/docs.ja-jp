---
description: 詳細については、「」を参照してください。 <behavior> <serviceBehaviors>
title: <behavior><serviceBehaviors>ワークフローの
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 7504e9b307286871440bb6efdb672a59d3d13cb1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725286"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="49f74-103">\<behavior>\<serviceBehaviors>ワークフローの</span><span class="sxs-lookup"><span data-stu-id="49f74-103">\<behavior> of \<serviceBehaviors> of workflow</span></span>

<span data-ttu-id="49f74-104">**Behavior** 要素には、サービスの動作に関する設定のコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="49f74-104">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="49f74-105">各動作は、 **名前** によってインデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="49f74-105">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="49f74-106">サービスは、要素の **設定** 属性を使用して、この名前を使用して各動作にリンクでき [\<endpoint>](../wcf/endpoint-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="49f74-106">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="49f74-107">これにより、設定を再定義することなく、エンドポイント間で共通の動作構成を共有できます。</span><span class="sxs-lookup"><span data-stu-id="49f74-107">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="49f74-108">構文</span><span class="sxs-lookup"><span data-stu-id="49f74-108">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan"
                           leaseTimeout="TimeSpan"
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan"
                           leaseTimeout="TimeSpan"
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String"
                                  hostLockRenewalPeriod="TimeSpan"
                                  instanceCompletionAction="DeleteNothing/DeleteAll"
                                  instanceEncodingAction="None/GZip"
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan"
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49f74-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="49f74-109">Attributes and Elements</span></span>  

 <span data-ttu-id="49f74-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="49f74-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49f74-111">属性</span><span class="sxs-lookup"><span data-stu-id="49f74-111">Attributes</span></span>  
  
|<span data-ttu-id="49f74-112">属性</span><span class="sxs-lookup"><span data-stu-id="49f74-112">Attribute</span></span>|<span data-ttu-id="49f74-113">説明</span><span class="sxs-lookup"><span data-stu-id="49f74-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49f74-114">name</span><span class="sxs-lookup"><span data-stu-id="49f74-114">name</span></span>|<span data-ttu-id="49f74-115">動作の構成名を含む一意の文字列。</span><span class="sxs-lookup"><span data-stu-id="49f74-115">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="49f74-116">この値は、要素の識別文字列として機能するため、一意のユーザー定義の文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="49f74-116">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49f74-117">子要素</span><span class="sxs-lookup"><span data-stu-id="49f74-117">Child Elements</span></span>  
  
|<span data-ttu-id="49f74-118">要素</span><span class="sxs-lookup"><span data-stu-id="49f74-118">Element</span></span>|<span data-ttu-id="49f74-119">説明</span><span class="sxs-lookup"><span data-stu-id="49f74-119">Description</span></span>|  
|-------------|-----------------|  
|[\<bufferReceive>](bufferreceive.md)|<span data-ttu-id="49f74-120">サービスが、バッファーされた受信処理を使用するためのサービス動作。これにより、ワークフロー サービスは、順番を無視したメッセージを処理できます。</span><span class="sxs-lookup"><span data-stu-id="49f74-120">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[\<routing>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="49f74-121"><xref:System.Activities.Tracking.EtwTrackingParticipant> を使用して、サービスで ETW 追跡を利用するためのサービス動作。</span><span class="sxs-lookup"><span data-stu-id="49f74-121">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|<span data-ttu-id="49f74-122">キャッシュの共有レベルのカスタマイズや、チャネル ファクトリ キャッシュの設定を可能にするほか、Send メッセージング アクティビティを使用してサービス エンドポイントにメッセージを送信するワークフローのチャネル キャッシュの設定も可能にするサービス動作。</span><span class="sxs-lookup"><span data-stu-id="49f74-122">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|<span data-ttu-id="49f74-123">ワークフロー サービス インスタンスの状態情報の永続化を SQL Server 2005 または SQL Server 2008 データベースでサポートする <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 機能を構成するためのサービス動作。</span><span class="sxs-lookup"><span data-stu-id="49f74-123">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[\<workflowIdle>](workflowidle.md)|<span data-ttu-id="49f74-124">アイドル状態のワークフロー インスタンスのアンロードおよび永続化のタイミングを制御するサービス動作。</span><span class="sxs-lookup"><span data-stu-id="49f74-124">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[\<workflowInstanceManagement>](workflowinstancemanagement.md)|<span data-ttu-id="49f74-125">ワークフロー インスタンスの実行方法を制御する設定を指定するためのサービス動作。これには、永続する未処理の例外動作やアイドル状態の動作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="49f74-125">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[\<workflowUnhandledException>](workflowunhandledexception.md)|<span data-ttu-id="49f74-126">ワークフロー サービス内で未処理の例外が発生した場合のアクションを指定するためのサービス動作。</span><span class="sxs-lookup"><span data-stu-id="49f74-126">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="49f74-127">親要素</span><span class="sxs-lookup"><span data-stu-id="49f74-127">Parent Elements</span></span>  
  
|<span data-ttu-id="49f74-128">要素</span><span class="sxs-lookup"><span data-stu-id="49f74-128">Element</span></span>|<span data-ttu-id="49f74-129">説明</span><span class="sxs-lookup"><span data-stu-id="49f74-129">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="49f74-130">サービス動作要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="49f74-130">A collection of service behavior elements.</span></span>|

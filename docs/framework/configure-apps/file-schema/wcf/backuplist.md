---
description: '詳細情報: <backupList>'
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 5323c8dad827ebb95e3cad65b3ad527d04517e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749715"
---
# \<backupList>

<span data-ttu-id="c8642-102">プライマリ エンドポイントに接続できないときにルーティング サービスで使用するエンドポイント セットを列挙したバックアップ リストを定義するための構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="c8642-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="c8642-103">リストの最初のエンドポイントがダウンしていると、ルーティング サービスは自動的にリスト内で次にあるエンドポイントにフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="c8642-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="c8642-104">これにより、クライアント アプリケーションに複雑なパターンの処理方法やサービスの配置場所を示すことなく、アプリケーションの信頼性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="c8642-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**  
  
## <a name="syntax"></a><span data-ttu-id="c8642-105">構文</span><span class="sxs-lookup"><span data-stu-id="c8642-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8642-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c8642-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c8642-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c8642-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8642-108">属性</span><span class="sxs-lookup"><span data-stu-id="c8642-108">Attributes</span></span>  
  
|<span data-ttu-id="c8642-109">属性</span><span class="sxs-lookup"><span data-stu-id="c8642-109">Attribute</span></span>|<span data-ttu-id="c8642-110">説明</span><span class="sxs-lookup"><span data-stu-id="c8642-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8642-111">name</span><span class="sxs-lookup"><span data-stu-id="c8642-111">name</span></span>|<span data-ttu-id="c8642-112">このエンドポイント リストを指定するために使用される名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="c8642-112">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8642-113">子要素</span><span class="sxs-lookup"><span data-stu-id="c8642-113">Child Elements</span></span>  
  
|<span data-ttu-id="c8642-114">要素</span><span class="sxs-lookup"><span data-stu-id="c8642-114">Element</span></span>|<span data-ttu-id="c8642-115">説明</span><span class="sxs-lookup"><span data-stu-id="c8642-115">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="c8642-116">親要素</span><span class="sxs-lookup"><span data-stu-id="c8642-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c8642-117">要素</span><span class="sxs-lookup"><span data-stu-id="c8642-117">Element</span></span>|<span data-ttu-id="c8642-118">説明</span><span class="sxs-lookup"><span data-stu-id="c8642-118">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="c8642-119">バックアップ エンドポイントの一覧。</span><span class="sxs-lookup"><span data-stu-id="c8642-119">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8642-120">解説</span><span class="sxs-lookup"><span data-stu-id="c8642-120">Remarks</span></span>  

 <span data-ttu-id="c8642-121">このセクションには、プライマリ エンドポイントへの送信時に通信例外が発生した場合にメッセージが送信されるエンドポイントの、順序付けられたコレクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c8642-121">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="c8642-122">の属性に示されているプライマリエンドポイントへの送信が `endpointName` [\<add>](add-of-entries.md) 通信例外で失敗した場合、ルーティングサービスは、この構成セクションの最初のエンドポイントにメッセージを送信しようとします。</span><span class="sxs-lookup"><span data-stu-id="c8642-122">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="c8642-123">これも通信例外によって失敗した場合、ルーティング サービスは、送信に成功するか、通信例外以外のエラーを返すか、コレクション内のすべてのエンドポイントがエラーを返すまで、このセクションに格納された次のエンドポイントにメッセージを送信しようとします。</span><span class="sxs-lookup"><span data-stu-id="c8642-123">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="c8642-124">次の例では、"Destination" という名前のプライマリエンドポイントへの送信で通信例外が返された場合、サービスは "alternateServiceQueue" にメッセージを送信しようとします。</span><span class="sxs-lookup"><span data-stu-id="c8642-124">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="c8642-125">この試行でも通信例外が返された場合、ルーティング サービスはコレクション内の次のエンドポイントにメッセージを送信しようとします。</span><span class="sxs-lookup"><span data-stu-id="c8642-125">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a><span data-ttu-id="c8642-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8642-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>

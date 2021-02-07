---
description: '詳細情報: <backupLists>'
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 9647c507f85eba6bfd001b34dbf617bc881d3f2e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749702"
---
# \<backupLists>

<span data-ttu-id="8f28c-102">エラー処理に使用されるバックアップ サービス セットを定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="8f28c-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="8f28c-103">各子要素は、プライマリ エンドポイントに接続できないときにルーティング サービスが使用するエンドポイント セットを列挙したバックアップ リストです。</span><span class="sxs-lookup"><span data-stu-id="8f28c-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="8f28c-104">リストの最初のエンドポイントがダウンしていると、ルーティング サービスは自動的にリスト内で次にあるエンドポイントにフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="8f28c-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="8f28c-105">これにより、クライアント アプリケーションに複雑なパターンの処理方法やサービスの配置場所を示すことなく、アプリケーションの信頼性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="8f28c-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**  
  
## <a name="syntax"></a><span data-ttu-id="8f28c-106">構文</span><span class="sxs-lookup"><span data-stu-id="8f28c-106">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f28c-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8f28c-107">Attributes and Elements</span></span>  

 <span data-ttu-id="8f28c-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8f28c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f28c-109">属性</span><span class="sxs-lookup"><span data-stu-id="8f28c-109">Attributes</span></span>  

 <span data-ttu-id="8f28c-110">なし。</span><span class="sxs-lookup"><span data-stu-id="8f28c-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8f28c-111">子要素</span><span class="sxs-lookup"><span data-stu-id="8f28c-111">Child Elements</span></span>  
  
|<span data-ttu-id="8f28c-112">要素</span><span class="sxs-lookup"><span data-stu-id="8f28c-112">Element</span></span>|<span data-ttu-id="8f28c-113">説明</span><span class="sxs-lookup"><span data-stu-id="8f28c-113">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)|<span data-ttu-id="8f28c-114">プライマリ エンドポイントに接続できないときにルーティング サービスが使用するエンドポイントのリストを格納します。</span><span class="sxs-lookup"><span data-stu-id="8f28c-114">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="8f28c-115">.</span><span class="sxs-lookup"><span data-stu-id="8f28c-115">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8f28c-116">親要素</span><span class="sxs-lookup"><span data-stu-id="8f28c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8f28c-117">要素</span><span class="sxs-lookup"><span data-stu-id="8f28c-117">Element</span></span>|<span data-ttu-id="8f28c-118">説明</span><span class="sxs-lookup"><span data-stu-id="8f28c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="8f28c-119">一連のルーティングフィルターを定義するための構成セクションを表します。これにより、受信メッセージを評価するときに使用される Windows Communication Foundation (WCF) の種類、 <xref:System.ServiceModel.Dispatcher.MessageFilter> およびフィルターが一致したときにメッセージを送信するターゲットエンドポイントを定義するルーティングテーブルが決定されます。</span><span class="sxs-lookup"><span data-stu-id="8f28c-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f28c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f28c-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>

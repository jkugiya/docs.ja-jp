---
description: '詳細情報: <soapProcessing>'
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 1355dc5b344891d7b6ed0fa0d5c64f877ec0ba48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786669"
---
# \<soapProcessing>

<span data-ttu-id="0449a-102">異なるバインディングの種類およびメッセージ バージョンの間でメッセージのマーシャリングに使用されるクライアント エンドポイントの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="0449a-102">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**
  
## <a name="syntax"></a><span data-ttu-id="0449a-103">構文</span><span class="sxs-lookup"><span data-stu-id="0449a-103">Syntax</span></span>  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0449a-104">属性と要素</span><span class="sxs-lookup"><span data-stu-id="0449a-104">Attributes and elements</span></span>  
  
<span data-ttu-id="0449a-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0449a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0449a-106">属性</span><span class="sxs-lookup"><span data-stu-id="0449a-106">Attributes</span></span>  
  
|                   | <span data-ttu-id="0449a-107">説明</span><span class="sxs-lookup"><span data-stu-id="0449a-107">Description</span></span> |
| ----------------- | ----------- |
| `processMessages` | <span data-ttu-id="0449a-108">SOAP メッセージ バージョン間のメッセージをマーシャリングするかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="0449a-108">A Boolean value that specifies whether messages should be marshaled between SOAP message versions.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="0449a-109">子要素</span><span class="sxs-lookup"><span data-stu-id="0449a-109">Child elements</span></span>

<span data-ttu-id="0449a-110">なし</span><span class="sxs-lookup"><span data-stu-id="0449a-110">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0449a-111">親要素</span><span class="sxs-lookup"><span data-stu-id="0449a-111">Parent elements</span></span>

|     | <span data-ttu-id="0449a-112">説明</span><span class="sxs-lookup"><span data-stu-id="0449a-112">Description</span></span> |
| --- | ----------- |
| [**\<behavior>**](behavior-of-endpointbehaviors.md) | <span data-ttu-id="0449a-113">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="0449a-113">Specifies an endpoint behavior.</span></span> |

## <a name="remarks"></a><span data-ttu-id="0449a-114">解説</span><span class="sxs-lookup"><span data-stu-id="0449a-114">Remarks</span></span>

<span data-ttu-id="0449a-115">SOAP 処理は、メッセージ バージョン間でメッセージが変換されるプロセスです。</span><span class="sxs-lookup"><span data-stu-id="0449a-115">SOAP processing is the process where messages are converted between message versions.</span></span>

<span data-ttu-id="0449a-116">Windows Communication Foundation (WCF) ルーティングサービスでは、あるプロトコルから別のプロトコルにメッセージを変換できます。</span><span class="sxs-lookup"><span data-stu-id="0449a-116">The Windows Communication Foundation (WCF) Routing Service can convert messages from one protocol to another.</span></span> <span data-ttu-id="0449a-117">受信メッセージのバージョンと送信メッセージのバージョンが異なる場合、新しいメッセージが正しいバージョンで作成されます。</span><span class="sxs-lookup"><span data-stu-id="0449a-117">If the incoming and outgoing Message Versions are different, a new message of the correct version is created.</span></span> <span data-ttu-id="0449a-118">受信 WCF メッセージの本文および関連するヘッダーが含まれた新しい WCF メッセージを作成することで、ある <xref:System.ServiceModel.Channels.MessageVersion> から別のメッセージ バージョンへのメッセージの変換が完了します。</span><span class="sxs-lookup"><span data-stu-id="0449a-118">Processing messages from one <xref:System.ServiceModel.Channels.MessageVersion> to another is accomplished by constructing a new WCF message that contains the body part and relevant headers from the incoming WCF message.</span></span> <span data-ttu-id="0449a-119">アドレス指定に固有のヘッダーまたはルーター レベルで認識されるヘッダーは、新しい WCF メッセージの作成に使用されません。これらのヘッダーは、異なるバージョンであるか (アドレス指定ヘッダーの場合)、クライアントとルーターの間の通信の一部として処理されているためです。</span><span class="sxs-lookup"><span data-stu-id="0449a-119">Headers that are specific to addressing, or that are understood at the router level, are not used during construction of the new WCF message because these headers are either of a different version (in the case of addressing headers) or have been processed as part of the communication between the client and the router.</span></span>

<span data-ttu-id="0449a-120">発信メッセージにヘッダーが配置されるかどうかは、受信チャネル層を介して渡されたと認識されるようにマークされているかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="0449a-120">Whether a header is placed in the outbound message is determined by whether or not it was marked as understood as it passed through the incoming channel layer.</span></span> <span data-ttu-id="0449a-121">認識されないヘッダー (カスタム ヘッダーなど) は削除されずに送信メッセージにコピーされ、ルーティング サービスを介して渡されます。</span><span class="sxs-lookup"><span data-stu-id="0449a-121">Headers that are not understood (such as custom headers) are not removed and so pass through the routing service by being copied to the outbound message.</span></span> <span data-ttu-id="0449a-122">メッセージの本文は、送信メッセージにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="0449a-122">The body of the message is copied to the outbound message.</span></span> <span data-ttu-id="0449a-123">そして、メッセージは送信チャネルに送信されます。この時点で、すべてのヘッダー、および使用されている通信プロトコル/トランスポートに固有のエンベロープ データが作成され、追加されます。</span><span class="sxs-lookup"><span data-stu-id="0449a-123">The message is then sent out the outbound channel, at which point all of the headers and other envelope data specific to that communication protocol/transport will be created and added.</span></span>

<span data-ttu-id="0449a-124">このような処理手順は、SOAP 処理動作が指定されているときに行われます。</span><span class="sxs-lookup"><span data-stu-id="0449a-124">Such processing steps take place when the SOAP processing behavior is specified.</span></span> <span data-ttu-id="0449a-125">この [\<soapProcessingExtension>](soapprocessing.md) 動作は、ルーティングサービスの開始時にすべてのクライアント (送信) エンドポイントに適用されるエンドポイントの動作です。</span><span class="sxs-lookup"><span data-stu-id="0449a-125">This [\<soapProcessingExtension>](soapprocessing.md) behavior is an endpoint behavior that is applied to all client (outgoing) endpoints when the Routing Service starts up.</span></span> <span data-ttu-id="0449a-126">既定では、この動作によって、 [\<routing>](routing-of-servicebehavior.md) [\<soapProcessingExtension>](soapprocessing.md) `processMessages` クライアントエンドポイントごとにがに設定された新しい動作が作成およびアタッチされ `true` ます。</span><span class="sxs-lookup"><span data-stu-id="0449a-126">default, the [\<routing>](routing-of-servicebehavior.md) behavior creates and attaches a new [\<soapProcessingExtension>](soapprocessing.md) behavior with `processMessages` set to `true` for each client endpoint.</span></span> <span data-ttu-id="0449a-127">ルーティング サービスが認識しないプロトコルを使用している場合や既定の処理動作をオーバーライドする場合は、ルーティング サービス全体または特定のエンドポイントにおいて SOAP 処理を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="0449a-127">If you have a protocol that the Routing Service does not understand, or wish to override the default processing behavior, you can disable SOAP processing either for the entire Routing Service or just for particular endpoints.</span></span>  <span data-ttu-id="0449a-128">すべてのエンドポイントのルーティングサービス全体で SOAP 処理を無効にするには、 `soapProcessing` 動作の属性 [\<routing>](routing-of-servicebehavior.md) をに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="0449a-128">To disable SOAP processing for the entire routing service on all endpoints, set the `soapProcessing` attribute of the [\<routing>](routing-of-servicebehavior.md) behavior to `false`.</span></span> <span data-ttu-id="0449a-129">特定のエンドポイントで SOAP 処理を無効にするには、この動作を使用して `processMessages` 属性を `false` に設定してから、既定の処理コードを実行しないエンドポイントにこの動作をアタッチします。</span><span class="sxs-lookup"><span data-stu-id="0449a-129">To turn off SOAP processing for a particular endpoint, use this behavior and set its `processMessages` attribute to `false`, then attach this behavior to the endpoint you do not want the default processing code to run at.</span></span>  <span data-ttu-id="0449a-130">動作が [\<routing>](routing-of-servicebehavior.md) ルーティングサービスを設定すると、既に存在するため、エンドポイントの動作の再適用はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="0449a-130">When the [\<routing>](routing-of-servicebehavior.md) behavior sets up the Routing Service, it will skip reapplying the endpoint behavior since one already exists.</span></span>

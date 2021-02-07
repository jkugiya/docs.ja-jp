---
description: '詳細情報: <headers>'
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 2a9a353823ba83b0b9672ab20c28080ee4afcb1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729850"
---
# \<headers>

<span data-ttu-id="5f64e-102">エンドポイントは、基本となる URI だけでなく、1 つ以上の SOAP ヘッダーによってアドレス指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5f64e-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="5f64e-103">これが役に立つのは、エンドポイントのクライアントに中継局を指す SOAP ヘッダーを含める必要がある、SOAP 中継局のシナリオの場合です。</span><span class="sxs-lookup"><span data-stu-id="5f64e-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="5f64e-104">この構成要素を使用して、カスタムのアドレス ヘッダーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="5f64e-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="5f64e-105">エンドポイント ヘッダー コレクション内のエントリは、ユーザー定義の XML 要素です。</span><span class="sxs-lookup"><span data-stu-id="5f64e-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="5f64e-106">各要素は、正しい形式の XML である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f64e-106">Each element has to be well-formed XML.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**  
  
## <a name="syntax"></a><span data-ttu-id="5f64e-107">構文</span><span class="sxs-lookup"><span data-stu-id="5f64e-107">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f64e-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5f64e-108">Attributes and Elements</span></span>  

 <span data-ttu-id="5f64e-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f64e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f64e-110">属性</span><span class="sxs-lookup"><span data-stu-id="5f64e-110">Attributes</span></span>  

 <span data-ttu-id="5f64e-111">なし。</span><span class="sxs-lookup"><span data-stu-id="5f64e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5f64e-112">子要素</span><span class="sxs-lookup"><span data-stu-id="5f64e-112">Child Elements</span></span>  

 <span data-ttu-id="5f64e-113">ユーザー定義の XML 要素。</span><span class="sxs-lookup"><span data-stu-id="5f64e-113">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f64e-114">親要素</span><span class="sxs-lookup"><span data-stu-id="5f64e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="5f64e-115">要素</span><span class="sxs-lookup"><span data-stu-id="5f64e-115">Element</span></span>|<span data-ttu-id="5f64e-116">説明</span><span class="sxs-lookup"><span data-stu-id="5f64e-116">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="5f64e-117">さまざまなタイプのエンドポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="5f64e-117">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f64e-118">解説</span><span class="sxs-lookup"><span data-stu-id="5f64e-118">Remarks</span></span>  

 <span data-ttu-id="5f64e-119">オプション ヘッダーは、エンドポイントの識別または対話のために、より詳細なアドレス指定情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5f64e-119">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="5f64e-120">たとえば、ヘッダーを使用して、受信メッセージの処理方法や、エンドポイントからの応答メッセージの送信先を指定できるほか、複数のサービス インスタンスが使用できる場合に、特定ユーザーからの受信メッセージの処理に使用するインスタンスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f64e-120">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f64e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f64e-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="5f64e-122">エンドポイント:アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="5f64e-122">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)

---
description: '詳細情報: <byteStreamMessageEncoding>'
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 9cbb4eacb1a960481ee262db662160b5a342e27f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639290"
---
# \<byteStreamMessageEncoding>

<span data-ttu-id="833b7-102">文字エンコーディングを指定するオプションを使用し、メッセージ エンコーディングをバイト ストリームとして指定します。</span><span class="sxs-lookup"><span data-stu-id="833b7-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="833b7-103">構文</span><span class="sxs-lookup"><span data-stu-id="833b7-103">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="833b7-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="833b7-104">Attributes and Elements</span></span>  

 <span data-ttu-id="833b7-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="833b7-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="833b7-106">属性</span><span class="sxs-lookup"><span data-stu-id="833b7-106">Attributes</span></span>  
  
|<span data-ttu-id="833b7-107">属性</span><span class="sxs-lookup"><span data-stu-id="833b7-107">Attribute</span></span>|<span data-ttu-id="833b7-108">説明</span><span class="sxs-lookup"><span data-stu-id="833b7-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="833b7-109">messageVersion</span><span class="sxs-lookup"><span data-stu-id="833b7-109">messageVersion</span></span>|<span data-ttu-id="833b7-110">バインディングを使用して送信されたメッセージの SOAP バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="833b7-110">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="833b7-111">このプロパティは、<xref:System.ServiceModel.Channels.MessageVersion.None%2A> のメッセージ バージョン値にのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="833b7-111">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="833b7-112">バイト ストリーム メッセージ エンコーダーは、他のメッセージ バージョンをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="833b7-112">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="833b7-113">この属性は <xref:System.ServiceModel.Channels.MessageVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="833b7-113">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="833b7-114">子要素</span><span class="sxs-lookup"><span data-stu-id="833b7-114">Child Elements</span></span>  
  
|<span data-ttu-id="833b7-115">要素</span><span class="sxs-lookup"><span data-stu-id="833b7-115">Element</span></span>|<span data-ttu-id="833b7-116">説明</span><span class="sxs-lookup"><span data-stu-id="833b7-116">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="833b7-117">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="833b7-117">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="833b7-118">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="833b7-118">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="833b7-119">親要素</span><span class="sxs-lookup"><span data-stu-id="833b7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="833b7-120">要素</span><span class="sxs-lookup"><span data-stu-id="833b7-120">Element</span></span>|<span data-ttu-id="833b7-121">説明</span><span class="sxs-lookup"><span data-stu-id="833b7-121">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="833b7-122">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="833b7-122">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="833b7-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="833b7-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="833b7-124">メッセージ エンコーディング</span><span class="sxs-lookup"><span data-stu-id="833b7-124">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="833b7-125">メッセージ エンコーダーを選択する</span><span class="sxs-lookup"><span data-stu-id="833b7-125">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="833b7-126">バインド</span><span class="sxs-lookup"><span data-stu-id="833b7-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="833b7-127">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="833b7-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="833b7-128">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="833b7-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

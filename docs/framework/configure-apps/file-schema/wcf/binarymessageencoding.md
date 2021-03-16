---
description: '詳細情報: <binaryMessageEncoding>'
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 910b8b70bab40c1eb099ed2b54c0545e73e96c6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639498"
---
# \<binaryMessageEncoding>

<span data-ttu-id="32594-102">ネットワーク上で Windows Communication Foundation (WCF) メッセージをバイナリにエンコードするバイナリ メッセージ エンコーダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="32594-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="32594-103">構文</span><span class="sxs-lookup"><span data-stu-id="32594-103">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32594-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="32594-104">Attributes and Elements</span></span>  

 <span data-ttu-id="32594-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="32594-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32594-106">属性</span><span class="sxs-lookup"><span data-stu-id="32594-106">Attributes</span></span>  
  
|<span data-ttu-id="32594-107">属性</span><span class="sxs-lookup"><span data-stu-id="32594-107">Attribute</span></span>|<span data-ttu-id="32594-108">説明</span><span class="sxs-lookup"><span data-stu-id="32594-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32594-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="32594-109">maxReadPoolSize</span></span>|<span data-ttu-id="32594-110">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="32594-110">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="32594-111">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="32594-111">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="32594-112">既定値は、64 です。</span><span class="sxs-lookup"><span data-stu-id="32594-112">The default is 64.</span></span>|  
|<span data-ttu-id="32594-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="32594-113">maxSessionSize</span></span>|<span data-ttu-id="32594-114">エンコーディングに使用されるバッファーのサイズをバイト単位で設定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="32594-114">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="32594-115">バッファーが大きくなると、作業セットのサイズの増加時に、エンコーディングの速度が高まります。</span><span class="sxs-lookup"><span data-stu-id="32594-115">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="32594-116">既定値は 2048 です。</span><span class="sxs-lookup"><span data-stu-id="32594-116">The default is 2048.</span></span>|  
|<span data-ttu-id="32594-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="32594-117">maxWritePoolSize</span></span>|<span data-ttu-id="32594-118">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="32594-118">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="32594-119">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="32594-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="32594-120">既定値は 16 です。</span><span class="sxs-lookup"><span data-stu-id="32594-120">The default is 16.</span></span>|  
|<span data-ttu-id="32594-121">messageVersion</span><span class="sxs-lookup"><span data-stu-id="32594-121">messageVersion</span></span>|<span data-ttu-id="32594-122">使用または予想される SOAP メッセージおよび WS-Addressing のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="32594-122">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32594-123">子要素</span><span class="sxs-lookup"><span data-stu-id="32594-123">Child Elements</span></span>  
  
|<span data-ttu-id="32594-124">要素</span><span class="sxs-lookup"><span data-stu-id="32594-124">Element</span></span>|<span data-ttu-id="32594-125">説明</span><span class="sxs-lookup"><span data-stu-id="32594-125">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="32594-126">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="32594-126">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="32594-127">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="32594-127">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32594-128">親要素</span><span class="sxs-lookup"><span data-stu-id="32594-128">Parent Elements</span></span>  
  
|<span data-ttu-id="32594-129">要素</span><span class="sxs-lookup"><span data-stu-id="32594-129">Element</span></span>|<span data-ttu-id="32594-130">説明</span><span class="sxs-lookup"><span data-stu-id="32594-130">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="32594-131">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="32594-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32594-132">解説</span><span class="sxs-lookup"><span data-stu-id="32594-132">Remarks</span></span>  

 <span data-ttu-id="32594-133">エンコーディングは、メッセージをバイト シーケンスに変換するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="32594-133">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="32594-134">デコードは、その逆のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="32594-134">Decoding is the reverse process.</span></span> <span data-ttu-id="32594-135">WCF (Windows Communication Foundation) には、SOAP メッセージのエンコードとして、テキスト、バイナリ、および MTOM (Message Transmission Optimization Mechanism) の 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="32594-135">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="32594-136">`binaryMessageEncoding` 要素は、XML 用の .NET バイナリ形式を指定します。この要素には、使用する文字エンコーディング、SOAP バージョン、および WS-Addressing バージョンを指定するオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="32594-136">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="32594-137">バイナリ メッセージ エンコーダーは、ネットワーク上で Windows Communication Foundation (WCF) メッセージをバイナリにエンコードします。</span><span class="sxs-lookup"><span data-stu-id="32594-137">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="32594-138">このエンコーディングによりメッセージ転送は非常に高速になりますが、WS-\* 標準に基づいた相互運用性は失われます。</span><span class="sxs-lookup"><span data-stu-id="32594-138">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32594-139">例</span><span class="sxs-lookup"><span data-stu-id="32594-139">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="32594-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="32594-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="32594-141">メッセージ エンコーディング</span><span class="sxs-lookup"><span data-stu-id="32594-141">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="32594-142">メッセージ エンコーダーを選択する</span><span class="sxs-lookup"><span data-stu-id="32594-142">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="32594-143">バインド</span><span class="sxs-lookup"><span data-stu-id="32594-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="32594-144">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="32594-144">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="32594-145">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="32594-145">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

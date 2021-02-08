---
description: '詳細情報: <textMessageEncoding>'
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: a8c7820b2e22152850d6d21c5091e328feb7a9f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786604"
---
# \<textMessageEncoding>

<span data-ttu-id="4f06e-102">テキストベースの XML メッセージに使用される文字エンコーディングおよびメッセージ バージョン管理を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f06e-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="4f06e-103">構文</span><span class="sxs-lookup"><span data-stu-id="4f06e-103">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f06e-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4f06e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="4f06e-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4f06e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f06e-106">属性</span><span class="sxs-lookup"><span data-stu-id="4f06e-106">Attributes</span></span>  
  
|<span data-ttu-id="4f06e-107">属性</span><span class="sxs-lookup"><span data-stu-id="4f06e-107">Attribute</span></span>|<span data-ttu-id="4f06e-108">説明</span><span class="sxs-lookup"><span data-stu-id="4f06e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f06e-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4f06e-109">maxReadPoolSize</span></span>|<span data-ttu-id="4f06e-110">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="4f06e-110">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="4f06e-111">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="4f06e-111">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4f06e-112">既定値は、64 です。</span><span class="sxs-lookup"><span data-stu-id="4f06e-112">The default is 64.</span></span>|  
|<span data-ttu-id="4f06e-113">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4f06e-113">maxWritePoolSize</span></span>|<span data-ttu-id="4f06e-114">新しいライターを割り当てずに同時に送信可能なメッセージの数を指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="4f06e-114">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="4f06e-115">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="4f06e-115">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4f06e-116">既定値は 16 です。</span><span class="sxs-lookup"><span data-stu-id="4f06e-116">The default is 16.</span></span>|  
|<span data-ttu-id="4f06e-117">messageVersion</span><span class="sxs-lookup"><span data-stu-id="4f06e-117">messageVersion</span></span>|<span data-ttu-id="4f06e-118">バインディングを使用して送信されたメッセージの SOAP バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f06e-118">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="4f06e-119">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4f06e-119">Valid values are</span></span><br /><br /> <span data-ttu-id="4f06e-120">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="4f06e-120">-   Soap11Addressing10</span></span><br /><span data-ttu-id="4f06e-121">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="4f06e-121">-   Soap12Addressing10</span></span><br /><span data-ttu-id="4f06e-122">- Soap11</span><span class="sxs-lookup"><span data-stu-id="4f06e-122">-   Soap11</span></span><br /><span data-ttu-id="4f06e-123">- Soap12</span><span class="sxs-lookup"><span data-stu-id="4f06e-123">-  Soap12</span></span><br /><br /><span data-ttu-id="4f06e-124">既定値は Soap12Addressing10 です。</span><span class="sxs-lookup"><span data-stu-id="4f06e-124">The default is Soap12Addressing10.</span></span> <span data-ttu-id="4f06e-125">この属性は <xref:System.ServiceModel.Channels.MessageVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="4f06e-125">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="4f06e-126">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="4f06e-126">writeEncoding</span></span>|<span data-ttu-id="4f06e-127">バインドでメッセージの発行に使用される文字セット エンコーディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f06e-127">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4f06e-128">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4f06e-128">Valid values are</span></span><br /><br /> <span data-ttu-id="4f06e-129">-UnicodeFffeTextEncoding: Unicode BigEndian エンコード</span><span class="sxs-lookup"><span data-stu-id="4f06e-129">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="4f06e-130">-Utf16TextEncoding: Unicode エンコーディング</span><span class="sxs-lookup"><span data-stu-id="4f06e-130">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="4f06e-131">-Utf8TextEncoding: 8 ビットエンコード</span><span class="sxs-lookup"><span data-stu-id="4f06e-131">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="4f06e-132">既定値は Utf8TextEncoding です。</span><span class="sxs-lookup"><span data-stu-id="4f06e-132">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="4f06e-133">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="4f06e-133">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f06e-134">子要素</span><span class="sxs-lookup"><span data-stu-id="4f06e-134">Child Elements</span></span>  
  
|<span data-ttu-id="4f06e-135">要素</span><span class="sxs-lookup"><span data-stu-id="4f06e-135">Element</span></span>|<span data-ttu-id="4f06e-136">説明</span><span class="sxs-lookup"><span data-stu-id="4f06e-136">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="4f06e-137">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="4f06e-137">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4f06e-138">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="4f06e-138">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f06e-139">親要素</span><span class="sxs-lookup"><span data-stu-id="4f06e-139">Parent Elements</span></span>  
  
|<span data-ttu-id="4f06e-140">要素</span><span class="sxs-lookup"><span data-stu-id="4f06e-140">Element</span></span>|<span data-ttu-id="4f06e-141">説明</span><span class="sxs-lookup"><span data-stu-id="4f06e-141">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="4f06e-142">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="4f06e-142">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f06e-143">解説</span><span class="sxs-lookup"><span data-stu-id="4f06e-143">Remarks</span></span>  

 <span data-ttu-id="4f06e-144">エンコーディングは、メッセージをバイト シーケンスに変換するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="4f06e-144">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="4f06e-145">デコードは、その逆のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="4f06e-145">Decoding is the reverse process.</span></span> <span data-ttu-id="4f06e-146">WCF (Windows Communication Foundation) には、SOAP メッセージのエンコードとして、テキスト、バイナリ、および MTOM (Message Transmission Optimization Mechanism) の 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="4f06e-146">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="4f06e-147">`textMessageEncoding` 要素で表されるテキスト エンコーディングでは相互運用性が最も高くなりますが、XML メッセージのエンコーダーとしての効率は最も低くなります。</span><span class="sxs-lookup"><span data-stu-id="4f06e-147">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="4f06e-148">テキスト エンコーダーは、ネットワーク上でテキストベースのメッセージを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f06e-148">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="4f06e-149">このエンコーダーにより生成されるメッセージは、WS-\* ベースの相互運用に適しています。</span><span class="sxs-lookup"><span data-stu-id="4f06e-149">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="4f06e-150">Web サービスまたは Web サービス クライアントは、一般に、テキスト形式の XML を認識できます。</span><span class="sxs-lookup"><span data-stu-id="4f06e-150">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="4f06e-151">しかし、大きいブロックのバイナリ データをテキストとして転送するのは、XML メッセージをエンコードする上では、最も非効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="4f06e-151">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f06e-152">例</span><span class="sxs-lookup"><span data-stu-id="4f06e-152">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="4f06e-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f06e-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="4f06e-154">メッセージ エンコーダーを選択する</span><span class="sxs-lookup"><span data-stu-id="4f06e-154">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="4f06e-155">メッセージ エンコーディング</span><span class="sxs-lookup"><span data-stu-id="4f06e-155">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="4f06e-156">バインド</span><span class="sxs-lookup"><span data-stu-id="4f06e-156">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4f06e-157">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="4f06e-157">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4f06e-158">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="4f06e-158">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

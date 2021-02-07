---
description: '詳細情報: <mtomMessageEncoding>'
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 37ac0be5f3de84a4c310b8ec2a09ed6f3c4def56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684114"
---
# \<mtomMessageEncoding>

<span data-ttu-id="3c678-102">SOAP Message Transmission Optimization Mechanism (MTOM) ベースのメッセージに使用されるエンコーディングおよびメッセージ バージョン管理を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c678-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="3c678-103">構文</span><span class="sxs-lookup"><span data-stu-id="3c678-103">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c678-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3c678-104">Attributes and Elements</span></span>  

 <span data-ttu-id="3c678-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3c678-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c678-106">属性</span><span class="sxs-lookup"><span data-stu-id="3c678-106">Attributes</span></span>  
  
|<span data-ttu-id="3c678-107">属性</span><span class="sxs-lookup"><span data-stu-id="3c678-107">Attribute</span></span>|<span data-ttu-id="3c678-108">説明</span><span class="sxs-lookup"><span data-stu-id="3c678-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c678-109">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="3c678-109">maxBufferSize</span></span>|<span data-ttu-id="3c678-110">使用できるバッファーの最大サイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="3c678-110">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="3c678-111">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="3c678-111">maxReadPoolSize</span></span>|<span data-ttu-id="3c678-112">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="3c678-112">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="3c678-113">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="3c678-113">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="3c678-114">既定値は、64 です。</span><span class="sxs-lookup"><span data-stu-id="3c678-114">The default is 64.</span></span>|  
|<span data-ttu-id="3c678-115">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="3c678-115">maxWritePoolSize</span></span>|<span data-ttu-id="3c678-116">新しいライターを割り当てずに同時に送信可能なメッセージの数を指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="3c678-116">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="3c678-117">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="3c678-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="3c678-118">既定値は 16 です。</span><span class="sxs-lookup"><span data-stu-id="3c678-118">The default is 16.</span></span>|  
|<span data-ttu-id="3c678-119">messageVersion</span><span class="sxs-lookup"><span data-stu-id="3c678-119">messageVersion</span></span>|<span data-ttu-id="3c678-120">バインディングを使用して送信されたメッセージの SOAP バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c678-120">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="3c678-121">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3c678-121">Valid values are</span></span><br /><br /> <span data-ttu-id="3c678-122">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="3c678-122">-   Soap11Addressing1</span></span><br /><span data-ttu-id="3c678-123">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="3c678-123">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="3c678-124">既定値は Soap12Addressing10 です。</span><span class="sxs-lookup"><span data-stu-id="3c678-124">The default is Soap12Addressing10.</span></span> <span data-ttu-id="3c678-125">この属性は <xref:System.ServiceModel.Channels.MessageVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="3c678-125">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="3c678-126">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="3c678-126">writeEncoding</span></span>|<span data-ttu-id="3c678-127">バインドでメッセージの発行に使用される文字セット エンコーディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c678-127">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="3c678-128">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3c678-128">Valid values are</span></span><br /><br /> <span data-ttu-id="3c678-129">-UnicodeFffeTextEncoding: Unicode BigEndian エンコード</span><span class="sxs-lookup"><span data-stu-id="3c678-129">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="3c678-130">-Utf16TextEncoding: Unicode エンコーディング</span><span class="sxs-lookup"><span data-stu-id="3c678-130">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="3c678-131">-Utf8TextEncoding: 8 ビットエンコード</span><span class="sxs-lookup"><span data-stu-id="3c678-131">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="3c678-132">既定値は Utf8TextEncoding です。</span><span class="sxs-lookup"><span data-stu-id="3c678-132">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="3c678-133">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="3c678-133">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c678-134">子要素</span><span class="sxs-lookup"><span data-stu-id="3c678-134">Child Elements</span></span>  
  
|<span data-ttu-id="3c678-135">要素</span><span class="sxs-lookup"><span data-stu-id="3c678-135">Element</span></span>|<span data-ttu-id="3c678-136">説明</span><span class="sxs-lookup"><span data-stu-id="3c678-136">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="3c678-137">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="3c678-137">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="3c678-138">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="3c678-138">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3c678-139">親要素</span><span class="sxs-lookup"><span data-stu-id="3c678-139">Parent Elements</span></span>  
  
|<span data-ttu-id="3c678-140">要素</span><span class="sxs-lookup"><span data-stu-id="3c678-140">Element</span></span>|<span data-ttu-id="3c678-141">説明</span><span class="sxs-lookup"><span data-stu-id="3c678-141">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="3c678-142">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="3c678-142">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c678-143">解説</span><span class="sxs-lookup"><span data-stu-id="3c678-143">Remarks</span></span>  

 <span data-ttu-id="3c678-144">エンコーディングは、メッセージをバイト シーケンスに変換するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="3c678-144">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="3c678-145">デコードは、その逆のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="3c678-145">Decoding is the reverse process.</span></span> <span data-ttu-id="3c678-146">WCF (Windows Communication Foundation) には、SOAP メッセージのエンコードとして、テキスト、バイナリ、および MTOM (Message Transmission Optimization Mechanism) の 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="3c678-146">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="3c678-147">`MtomMessageEncoding` 要素は、MTOM (Message Transmission Optimization Mechanism) エンコーディングを使用するメッセージの文字エンコーディング、メッセージのバージョン管理、およびその他の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c678-147">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="3c678-148">MTOM は、WCF メッセージでバイナリ データを転送するための効率的なテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="3c678-148">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="3c678-149">MTOM エンコーダーは、効率と相互運用性のバランスをとろうとします。</span><span class="sxs-lookup"><span data-stu-id="3c678-149">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="3c678-150">MTOM エンコーディングは、ほとんどの XML をテキスト形式で転送しますが、大きいサイズのバイナリ データ ブロックは、base64 でエンコードされた形式に変換せずに、そのまま転送することによって最適化します。</span><span class="sxs-lookup"><span data-stu-id="3c678-150">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c678-151">例</span><span class="sxs-lookup"><span data-stu-id="3c678-151">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="3c678-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c678-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="3c678-153">メッセージ エンコーディング</span><span class="sxs-lookup"><span data-stu-id="3c678-153">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="3c678-154">メッセージ エンコーダーを選択する</span><span class="sxs-lookup"><span data-stu-id="3c678-154">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="3c678-155">バインド</span><span class="sxs-lookup"><span data-stu-id="3c678-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3c678-156">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="3c678-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3c678-157">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="3c678-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

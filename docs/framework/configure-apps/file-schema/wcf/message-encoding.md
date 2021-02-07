---
description: 詳細については、「メッセージエンコード」を参照してください。
title: メッセージ エンコーディング
ms.date: 03/30/2017
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
ms.openlocfilehash: 6c0afd61bbdb28c9bcf4dee662b31d93c590c464
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725351"
---
# <a name="message-encoding"></a><span data-ttu-id="22c35-103">メッセージ エンコーディング</span><span class="sxs-lookup"><span data-stu-id="22c35-103">Message Encoding</span></span>

<span data-ttu-id="22c35-104">エンコーディングは、Unicode 文字のセットをバイト シーケンスに変換するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="22c35-104">Encoding is the process of transforming a set of Unicode characters into a sequence of bytes.</span></span> <span data-ttu-id="22c35-105">デコードは、その逆のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="22c35-105">Decoding is the reverse process.</span></span> <span data-ttu-id="22c35-106">WCF (Windows Communication Foundation) には、SOAP メッセージのエンコードとして、テキスト、バイナリ、および MTOM (Message Transmission Optimization Mechanism) の 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="22c35-106">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="22c35-107">`binaryMessageEncoding` 構成セクションでは、バイナリ ベースの XML メッセージに使用される文字エンコーディングおよびメッセージ バージョン管理が指定されます。</span><span class="sxs-lookup"><span data-stu-id="22c35-107">The `binaryMessageEncoding` configuration section specifies the character encoding and message versioning used for binary-based XML messages.</span></span> <span data-ttu-id="22c35-108">バイナリ メッセージ エンコーダーは、ネットワーク上で Windows Communication Foundation (WCF) メッセージをバイナリにエンコードします。</span><span class="sxs-lookup"><span data-stu-id="22c35-108">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="22c35-109">このエンコーディングによりメッセージ転送は非常に高速になりますが、WS-\* 標準に基づいた相互運用性は失われます。</span><span class="sxs-lookup"><span data-stu-id="22c35-109">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
 <span data-ttu-id="22c35-110">`mtomMessageEncoding` 構成セクションでは、Message Transmission Optimization Mechanism (MTOM) エンコーディングを使用したメッセージの文字エンコーディングおよびメッセージ バージョン管理が指定されます。</span><span class="sxs-lookup"><span data-stu-id="22c35-110">The `mtomMessageEncoding` configuration section specifies the character encoding and message versioning used for a message using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="22c35-111">(MTOM) は、Windows Communication Foundation (WCF) メッセージでバイナリ データを送信する効率的な技術です。</span><span class="sxs-lookup"><span data-stu-id="22c35-111">(MTOM) is an efficient technology for transmitting binary data in Windows Communication Foundation (WCF) messages.</span></span> <span data-ttu-id="22c35-112">MTOM エンコーダーは、効率と相互運用性のバランスをとろうとします。</span><span class="sxs-lookup"><span data-stu-id="22c35-112">The MTOM encoder attempts to strike a balance between efficiency and interoperability.</span></span> <span data-ttu-id="22c35-113">MTOM エンコーディングは、ほとんどの XML をテキスト形式で転送しますが、大きいサイズのバイナリ データ ブロックはテキストに変換せずにそのまま転送することによって最適化します。</span><span class="sxs-lookup"><span data-stu-id="22c35-113">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to text.</span></span>  
  
 <span data-ttu-id="22c35-114">`textMessageEncoding` 構成セクションは、ネットワーク上でテキストベースのメッセージの作成に使用されるテキスト エンコーダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="22c35-114">The `textMessageEncoding` configuration section specifies a text encoder used to create text-based messages on the wire.</span></span> <span data-ttu-id="22c35-115">このエンコーダーにより生成されるメッセージは、WS-\* ベースの相互運用に適しています。</span><span class="sxs-lookup"><span data-stu-id="22c35-115">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="22c35-116">Web サービスまたは Web サービス クライアントは、一般に、テキスト形式の XML を認識できます。</span><span class="sxs-lookup"><span data-stu-id="22c35-116">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="22c35-117">ただし、バイナリ データの大きいブロックをテキストとして送信することは、XML メッセージをエンコードする最も効率の悪い方法です。</span><span class="sxs-lookup"><span data-stu-id="22c35-117">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c35-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="22c35-118">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- [<span data-ttu-id="22c35-119">バインド</span><span class="sxs-lookup"><span data-stu-id="22c35-119">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="22c35-120">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="22c35-120">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="22c35-121">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="22c35-121">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="22c35-122">メッセージ エンコーダーを選択する</span><span class="sxs-lookup"><span data-stu-id="22c35-122">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)

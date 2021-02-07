---
description: 詳細については、「データ転送とシリアル化」を参照してください。
title: データ転送とシリアル化
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 50e5068efc10d706fb9ce2634998408e48037ded
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756566"
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="903f6-103">データ転送とシリアル化</span><span class="sxs-lookup"><span data-stu-id="903f6-103">Data Transfer and Serialization</span></span>

<span data-ttu-id="903f6-104">接続されたシステムでは、サービスとクライアントのタスクの実行は、データの交換に依存します。</span><span class="sxs-lookup"><span data-stu-id="903f6-104">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="903f6-105">また、サービスまたはクライアントの開発者は、Windows Communication Foundation (WCF) がデータとデータのシリアル化を処理する方法についても理解しておく必要があります。これにより、効率的で保守が容易なアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="903f6-105">As a developer of a service or client, you must also understand how Windows Communication Foundation (WCF) handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="903f6-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="903f6-106">In This Section</span></span>  

 [<span data-ttu-id="903f6-107">サービス コントラクトでのデータ転送の指定</span><span class="sxs-lookup"><span data-stu-id="903f6-107">Specifying Data Transfer in Service Contracts</span></span>](specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="903f6-108">サービスでのデータ転送の基本的な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="903f6-108">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="903f6-109">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="903f6-109">Using Data Contracts</span></span>](using-data-contracts.md)  
 <span data-ttu-id="903f6-110">データ コントラクトの定義と、その作成方法と使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="903f6-110">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="903f6-111">データ コントラクト シリアライザー</span><span class="sxs-lookup"><span data-stu-id="903f6-111">Data Contract Serializer</span></span>](data-contract-serializer.md)  
 <span data-ttu-id="903f6-112"><xref:System.Runtime.Serialization.DataContractSerializer> クラス、または <xref:System.Runtime.Serialization.XmlObjectSerializer> クラスの拡張機能で、データのシリアル化を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="903f6-112">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="903f6-113">XmlSerializer クラスの使用</span><span class="sxs-lookup"><span data-stu-id="903f6-113">Using the XmlSerializer Class</span></span>](using-the-xmlserializer-class.md)  
 <span data-ttu-id="903f6-114"><xref:System.Xml.Serialization.XmlSerializer> クラスの代わりに、<xref:System.Runtime.Serialization.DataContractSerializer> クラスを使う方法とその理由について説明します。</span><span class="sxs-lookup"><span data-stu-id="903f6-114">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="903f6-115">メッセージ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="903f6-115">Using Message Contracts</span></span>](using-message-contracts.md)  
 <span data-ttu-id="903f6-116">メッセージ コントラクトで SOAP メッセージを詳細に制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="903f6-116">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="903f6-117">メッセージ クラスの使用</span><span class="sxs-lookup"><span data-stu-id="903f6-117">Using the Message Class</span></span>](using-the-message-class.md)  
 <span data-ttu-id="903f6-118">メッセージ クラス機能の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="903f6-118">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="903f6-119">フィルター処理</span><span class="sxs-lookup"><span data-stu-id="903f6-119">Filtering</span></span>](filtering.md)  
 <span data-ttu-id="903f6-120">各種の条件に基づいて、メッセージを事前処理できるフィルター処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="903f6-120">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="903f6-121">大規模データとストリーミング</span><span class="sxs-lookup"><span data-stu-id="903f6-121">Large Data and Streaming</span></span>](large-data-and-streaming.md)  
 <span data-ttu-id="903f6-122">バイナリ ファイルなど、大きなデータ ブロックを送信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="903f6-122">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="903f6-123">セキュリティに関するデータの考慮事項</span><span class="sxs-lookup"><span data-stu-id="903f6-123">Security Considerations for Data</span></span>](security-considerations-for-data.md)  
 <span data-ttu-id="903f6-124">データの転送とシリアル化をプログラムするときに注意する必要のある項目について説明します。</span><span class="sxs-lookup"><span data-stu-id="903f6-124">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="903f6-125">データ転送のアーキテクチャの概要</span><span class="sxs-lookup"><span data-stu-id="903f6-125">Data Transfer Architectural Overview</span></span>](data-transfer-architectural-overview.md)  
 <span data-ttu-id="903f6-126">WCF でのデータ転送の全体的な設計のビューについて説明します。</span><span class="sxs-lookup"><span data-stu-id="903f6-126">Describes a view of the overall design of data transfer in WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="903f6-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="903f6-127">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="903f6-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="903f6-128">Related Sections</span></span>  

 [<span data-ttu-id="903f6-129">エンコーダーとシリアライザーの拡張</span><span class="sxs-lookup"><span data-stu-id="903f6-129">Extending Encoders and Serializers</span></span>](../extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="903f6-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="903f6-130">See also</span></span>

- [<span data-ttu-id="903f6-131">ベスト プラクティス:データ コントラクトのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="903f6-131">Best Practices: Data Contract Versioning</span></span>](../best-practices-data-contract-versioning.md)
- [<span data-ttu-id="903f6-132">サービスのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="903f6-132">Service Versioning</span></span>](../service-versioning.md)

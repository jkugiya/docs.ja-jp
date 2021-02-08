---
description: 詳細については、「Forward-Compatible データコントラクト」を参照してください。
title: 上位互換性のあるデータ コントラクト
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
ms.openlocfilehash: 70256449d405290e9c32eebdc5b8e3a78b76ed56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793858"
---
# <a name="forward-compatible-data-contracts"></a><span data-ttu-id="17847-103">上位互換性のあるデータ コントラクト</span><span class="sxs-lookup"><span data-stu-id="17847-103">Forward-Compatible Data Contracts</span></span>

<span data-ttu-id="17847-104">Windows Communication Foundation (WCF) データコントラクトシステムの機能として、コントラクトは、非分離方式で時間の経過と共に進化することがあります。</span><span class="sxs-lookup"><span data-stu-id="17847-104">A feature of the Windows Communication Foundation (WCF) data contract system is that contracts can evolve over time in nonbreaking ways.</span></span> <span data-ttu-id="17847-105">つまり、古いバージョンのデータ コントラクトを使用するクライアントが同じデータ コントラクトの新しいバージョンのサービスと通信したり、新しいバージョンのデータ コントラクトを使用するクライアントが同じデータ コントラクトの古いバージョンと通信したりできます。</span><span class="sxs-lookup"><span data-stu-id="17847-105">That is, a client with an older version of a data contract can communicate with a service with a newer version of the same data contract, or a client with a newer version of a data contract can communicate with an older version of the same data contract.</span></span> <span data-ttu-id="17847-106">詳細については、「 [ベストプラクティス: データコントラクトのバージョン管理](../best-practices-data-contract-versioning.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17847-106">For more information, see [Best Practices: Data Contract Versioning](../best-practices-data-contract-versioning.md).</span></span>  
  
 <span data-ttu-id="17847-107">バージョン管理機能の大半は、既存のデータ コントラクトの新しいバージョンが作成されたときに、必要に応じて適用できます。</span><span class="sxs-lookup"><span data-stu-id="17847-107">You can apply most of the versioning features on an as-needed basis when new versions of an existing data contract are created.</span></span> <span data-ttu-id="17847-108">ただし、1つのバージョン管理機能である *ラウンドトリップ* は、適切に機能するために、最初のバージョンの型に組み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="17847-108">However, one versioning feature, *round-tripping*, must be built into the type from the first version in order to work properly.</span></span>  
  
## <a name="round-tripping"></a><span data-ttu-id="17847-109">ラウンド トリップ</span><span class="sxs-lookup"><span data-stu-id="17847-109">Round-Tripping</span></span>  

 <span data-ttu-id="17847-110">ラウンド トリップは、データ コントラクトの新しいバージョンから古いバージョンにデータが渡され、新しいバージョンに戻されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="17847-110">Round-tripping occurs when data passes from a new version to an old version and back to the new version of a data contract.</span></span> <span data-ttu-id="17847-111">ラウンド トリップでは、データの損失がないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="17847-111">Round-tripping guarantees that no data is lost.</span></span> <span data-ttu-id="17847-112">ラウンド トリップを有効にすると、データ コントラクト バージョン管理モデルによってサポートされる将来の変更に関して、型の上位互換性が保たれます。</span><span class="sxs-lookup"><span data-stu-id="17847-112">Enabling round-tripping makes the type forward-compatible with any future changes supported by the data contract versioning model.</span></span>  
  
 <span data-ttu-id="17847-113">特定の型のラウンド トリップを有効にするには、この型に <xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17847-113">To enable round-tripping for a particular type, the type must implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span> <span data-ttu-id="17847-114">このインターフェイスには、(<xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> 型を返す) <xref:System.Runtime.Serialization.ExtensionDataObject> プロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="17847-114">The interface contains one property, <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (returning the <xref:System.Runtime.Serialization.ExtensionDataObject> type).</span></span> <span data-ttu-id="17847-115">このプロパティにより、現在のバージョンでは未知の、今後使用されるデータ コントラクトの任意のデータが格納されます。</span><span class="sxs-lookup"><span data-stu-id="17847-115">The property stores any data from future versions of the data contract that is unknown to the current version.</span></span>  
  
### <a name="example"></a><span data-ttu-id="17847-116">例</span><span class="sxs-lookup"><span data-stu-id="17847-116">Example</span></span>  

 <span data-ttu-id="17847-117">次のデータ コントラクトは、将来の変更に対して上位互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="17847-117">The following data contract is not forward-compatible with future changes.</span></span>  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 <span data-ttu-id="17847-118">将来の変更 (たとえば、"phoneNumber" という名前の新しいデータ メンバーを追加する) に対して互換性を確保するには、<xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを次のように実装します。</span><span class="sxs-lookup"><span data-stu-id="17847-118">To make the type compatible with future changes (such as adding a new data member named "phoneNumber"), implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span>  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 <span data-ttu-id="17847-119">WCF インフラストラクチャによって、元のデータコントラクトの一部ではないデータが検出されると、データはプロパティに格納されて保存されます。</span><span class="sxs-lookup"><span data-stu-id="17847-119">When the WCF infrastructure encounters data that is not part of the original data contract, the data is stored in the property and preserved.</span></span> <span data-ttu-id="17847-120">データは一時的に格納されるだけで、処理されることはありません。</span><span class="sxs-lookup"><span data-stu-id="17847-120">It is not processed in any other way except for temporary storage.</span></span> <span data-ttu-id="17847-121">オブジェクトを発生元に返すと、元の (未知の) データも返されます。</span><span class="sxs-lookup"><span data-stu-id="17847-121">If the object is returned back to where it originated, the original (unknown) data is also returned.</span></span> <span data-ttu-id="17847-122">したがって、データが失われることなく、元のエンドポイントとの間でラウンド トリップ (往復) が行われます。</span><span class="sxs-lookup"><span data-stu-id="17847-122">Therefore, the data has made a round trip to and from the originating endpoint without loss.</span></span> <span data-ttu-id="17847-123">ただし、発生元のエンドポイントでデータを処理する必要がある場合、この要求は満たされないため、このエンドポイントでは何らかの方法で変更を検出して対応する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="17847-123">Note, however, that if the originating endpoint required the data to be processed, that expectation is unmet, and the endpoint must somehow detect and accommodate the change.</span></span>  
  
 <span data-ttu-id="17847-124"><xref:System.Runtime.Serialization.ExtensionDataObject> 型にはパブリックなメソッドやプロパティはありません。</span><span class="sxs-lookup"><span data-stu-id="17847-124">The <xref:System.Runtime.Serialization.ExtensionDataObject> type contains no public methods or properties.</span></span> <span data-ttu-id="17847-125">そのため、<xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> プロパティ内に格納されているデータに直接アクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="17847-125">Thus, it is impossible to get direct access to the data stored inside the <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> property.</span></span>  
  
 <span data-ttu-id="17847-126">ラウンド トリップ機能は、`ignoreExtensionDataObject` コンストラクターで `true` を <xref:System.Runtime.Serialization.DataContractSerializer> に設定する、または <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> で `true` プロパティを <xref:System.ServiceModel.ServiceBehaviorAttribute> に設定することで無効にできます。</span><span class="sxs-lookup"><span data-stu-id="17847-126">The round-tripping feature may be turned off, either by setting `ignoreExtensionDataObject` to `true` in the <xref:System.Runtime.Serialization.DataContractSerializer> constructor or by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> property to `true` on the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="17847-127">この機能を無効にすると、デシリアライザーが <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> プロパティを設定しないため、シリアライザーはプロパティの内容を出力しません。</span><span class="sxs-lookup"><span data-stu-id="17847-127">When this feature is off, the deserializer will not populate the <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> property, and the serializer will not emit the contents of the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17847-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="17847-128">See also</span></span>

- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- [<span data-ttu-id="17847-129">データ コントラクトのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="17847-129">Data Contract Versioning</span></span>](data-contract-versioning.md)
- [<span data-ttu-id="17847-130">ベスト プラクティス:データ コントラクトのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="17847-130">Best Practices: Data Contract Versioning</span></span>](../best-practices-data-contract-versioning.md)

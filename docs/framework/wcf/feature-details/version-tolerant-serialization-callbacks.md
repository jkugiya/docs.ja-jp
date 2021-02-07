---
description: 詳細については、Version-Tolerant シリアル化のコールバック
title: バージョン トレラントなシリアル化コールバック
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
ms.openlocfilehash: 8ee53e96b90ae6b0f2993a543fc129d75eb3481f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756007"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="4de60-103">バージョン トレラントなシリアル化コールバック</span><span class="sxs-lookup"><span data-stu-id="4de60-103">Version-Tolerant Serialization Callbacks</span></span>

<span data-ttu-id="4de60-104">データ コントラクトのプログラミング モデルでは、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> クラスと <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> クラスがサポートする、複数のバージョンに対応するシリアル化コールバック メソッドが完全にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="4de60-104">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="4de60-105">複数のバージョンに対応する属性</span><span class="sxs-lookup"><span data-stu-id="4de60-105">Version-Tolerant Attributes</span></span>  

 <span data-ttu-id="4de60-106">4 つのコールバック属性があります。</span><span class="sxs-lookup"><span data-stu-id="4de60-106">There are four callback attributes.</span></span> <span data-ttu-id="4de60-107">各属性は、さまざまなタイミングでシリアル化エンジンまたは逆シリアル化エンジンが呼び出すメソッドに適用できます。</span><span class="sxs-lookup"><span data-stu-id="4de60-107">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="4de60-108">次の表では、各属性を使用するタイミングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4de60-108">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="4de60-109">属性</span><span class="sxs-lookup"><span data-stu-id="4de60-109">Attribute</span></span>|<span data-ttu-id="4de60-110">対応するメソッドが呼び出されるタイミング</span><span class="sxs-lookup"><span data-stu-id="4de60-110">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="4de60-111">型をシリアル化する前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4de60-111">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="4de60-112">型をシリアル化した後に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4de60-112">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="4de60-113">型を逆シリアル化する前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4de60-113">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="4de60-114">型を逆シリアル化した後に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4de60-114">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="4de60-115">メソッドは、<xref:System.Runtime.Serialization.StreamingContext> パラメーターを受け入れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4de60-115">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="4de60-116">これらのメソッドは、主にバージョン管理と初期化に使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="4de60-116">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="4de60-117">逆シリアル化時にコンストラクターは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="4de60-117">During deserialization, no constructors are called.</span></span> <span data-ttu-id="4de60-118">このため、データ メンバーのデータが受信ストリームにない場合、たとえば、データの送信元が、一部のデータ メンバーが不足している前のバージョンの型である場合、そのデータ メンバーを目的の既定値に適切に初期化できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="4de60-118">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="4de60-119">これを修正するには、次の例で示すように、<xref:System.Runtime.Serialization.OnDeserializingAttribute> でマークされたコールバック メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4de60-119">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="4de60-120">上記の各コールバック属性でマークできるのは、型ごとに 1 つのメソッドだけです。</span><span class="sxs-lookup"><span data-stu-id="4de60-120">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="4de60-121">例</span><span class="sxs-lookup"><span data-stu-id="4de60-121">Example</span></span>  

 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="4de60-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="4de60-122">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="4de60-123">バージョントレラントなシリアル化</span><span class="sxs-lookup"><span data-stu-id="4de60-123">Version Tolerant Serialization</span></span>](../../../standard/serialization/version-tolerant-serialization.md)

---
description: '詳細情報: System.Object メソッド'
title: System.Object メソッド
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: 88ba4cf7cfc7dc9bea565b4689f77d088d424c44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681319"
---
# <a name="systemobject-methods"></a><span data-ttu-id="4ef2b-103">System.Object メソッド</span><span class="sxs-lookup"><span data-stu-id="4ef2b-103">System.Object Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="4ef2b-104">では、次の <xref:System.Object> メソッドがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="4ef2b-104">supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="4ef2b-105">は、次の <xref:System.Object> メソッドをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="4ef2b-105">does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="4ef2b-106"><xref:System.Object.ToString?displayProperty=nameWithType>、`BINARY`、`VARBINARY`、`IMAGE` などのバイナリ型の `TIMESTAMP`</span><span class="sxs-lookup"><span data-stu-id="4ef2b-106"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="4ef2b-107">.NET との相違</span><span class="sxs-lookup"><span data-stu-id="4ef2b-107">Differences from .NET</span></span>  

 <span data-ttu-id="4ef2b-108">SQL では、double 型に対する <xref:System.Object.ToString?displayProperty=nameWithType> の出力で、SQL `CONVERT` (NVARCHAR(30), @x, 2) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4ef2b-108">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="4ef2b-109">このとき、SQL は常に 16 桁と指数表記を使用します (たとえば、0 に対して "0.000000000000000e+000" を使用)。</span><span class="sxs-lookup"><span data-stu-id="4ef2b-109">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="4ef2b-110">そのため、<xref:System.Object.ToString?displayProperty=nameWithType> 変換では、.NET Framework 内の <xref:System.Convert.ToString%2A?displayProperty=nameWithType>  と同じ文字列は作成されません。</span><span class="sxs-lookup"><span data-stu-id="4ef2b-110">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef2b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ef2b-111">See also</span></span>

- [<span data-ttu-id="4ef2b-112">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="4ef2b-112">Data Types and Functions</span></span>](data-types-and-functions.md)

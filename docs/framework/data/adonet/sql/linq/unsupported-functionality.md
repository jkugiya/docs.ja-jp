---
description: '詳細情報: サポートされていない機能'
title: サポートされていない機能
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 5c44dd4aad2d2ee4ec5e00ce42f4de9400cea478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680890"
---
# <a name="unsupported-functionality"></a><span data-ttu-id="3fbaa-103">サポートされていない機能</span><span class="sxs-lookup"><span data-stu-id="3fbaa-103">Unsupported Functionality</span></span>

<span data-ttu-id="3fbaa-104">LINQ to SQL では、次の SQL 機能は、既存の共通言語ランタイム (CLR) および .NET Framework の構成要素の変換からは公開できません。</span><span class="sxs-lookup"><span data-stu-id="3fbaa-104">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
- `STDDEV`  
  
- `LIKE`  
  
     <span data-ttu-id="3fbaa-105">`LIKE` は直接変換によってサポートされませんが、同様の機能が <xref:System.Data.Linq.SqlClient.SqlMethods> クラスにあります。</span><span class="sxs-lookup"><span data-stu-id="3fbaa-105">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="3fbaa-106">詳細については、「<xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fbaa-106">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
- `DATEDIFF`  
  
     <span data-ttu-id="3fbaa-107">LINQ to SQL では、`DATEDIFF` のサポートが制限されています。</span><span class="sxs-lookup"><span data-stu-id="3fbaa-107">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="3fbaa-108">同様の機能が <xref:System.Data.Linq.SqlClient.SqlMethods> クラスにあります。</span><span class="sxs-lookup"><span data-stu-id="3fbaa-108">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
- `ROUND`  
  
     <span data-ttu-id="3fbaa-109">LINQ to SQL では、`ROUND` のサポートが制限されています。</span><span class="sxs-lookup"><span data-stu-id="3fbaa-109">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="3fbaa-110">詳細については、「[System.Math メソッド](system-math-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fbaa-110">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fbaa-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fbaa-111">See also</span></span>

- [<span data-ttu-id="3fbaa-112">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="3fbaa-112">Data Types and Functions</span></span>](data-types-and-functions.md)

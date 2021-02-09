---
description: '詳細情報: COLLECTION (Entity SQL)'
title: COLLECTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 1269680b2a9009277e79337cfe4df154885b7c1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697050"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="8bb85-103">COLLECTION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8bb85-103">COLLECTION (Entity SQL)</span></span>

<span data-ttu-id="8bb85-104">COLLECTION キーワードは、インライン関数を定義する場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="8bb85-104">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="8bb85-105">コレクション関数は、値のコレクションを操作してスカラー出力を生成する関数です。</span><span class="sxs-lookup"><span data-stu-id="8bb85-105">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bb85-106">構文</span><span class="sxs-lookup"><span data-stu-id="8bb85-106">Syntax</span></span>  
  
```csharp  
COLLECTION(type_definition)
```  
  
## <a name="arguments"></a><span data-ttu-id="8bb85-107">引数</span><span class="sxs-lookup"><span data-stu-id="8bb85-107">Arguments</span></span>  

 `type_definition`  
 <span data-ttu-id="8bb85-108">サポートされる型、行、または参照のコレクションを返す式。</span><span class="sxs-lookup"><span data-stu-id="8bb85-108">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bb85-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="8bb85-109">Remarks</span></span>  

 <span data-ttu-id="8bb85-110">COLLECTION キーワードについて詳しくは、「 [Type Definitions](type-definitions-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8bb85-110">For more information about the COLLECTION keyword, see [Type Definitions](type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bb85-111">例</span><span class="sxs-lookup"><span data-stu-id="8bb85-111">Example</span></span>  

 <span data-ttu-id="8bb85-112">次の例は、COLLECTION キーワードを使用して 10 進数のコレクションをインライン クエリ関数の引数として宣言する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8bb85-112">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="8bb85-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8bb85-113">See also</span></span>

- [<span data-ttu-id="8bb85-114">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="8bb85-114">Entity SQL Reference</span></span>](entity-sql-reference.md)

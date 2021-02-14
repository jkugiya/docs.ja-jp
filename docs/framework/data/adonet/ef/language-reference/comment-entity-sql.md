---
description: '詳細情報: -- (コメント) (Entity SQL)'
title: -- (コメント) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 793649177d9e64bead7b8755f35bdb51f53f4dd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724974"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="ce80f-103">-- (コメント) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ce80f-103">-- (Comment) (Entity SQL)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="ce80f-104">クエリには、コメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ce80f-104">queries can contain comments.</span></span> <span data-ttu-id="ce80f-105">コメント行の先頭には、2 個のダッシュ (`--`) を付けます。</span><span class="sxs-lookup"><span data-stu-id="ce80f-105">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce80f-106">構文</span><span class="sxs-lookup"><span data-stu-id="ce80f-106">Syntax</span></span>  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="ce80f-107">引数</span><span class="sxs-lookup"><span data-stu-id="ce80f-107">Arguments</span></span>  

 `text_of_comment`  
 <span data-ttu-id="ce80f-108">コメントのテキストを表す文字列です。</span><span class="sxs-lookup"><span data-stu-id="ce80f-108">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce80f-109">例</span><span class="sxs-lookup"><span data-stu-id="ce80f-109">Example</span></span>  

 <span data-ttu-id="ce80f-110">次の Entity SQL クエリは、コメントの使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="ce80f-110">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="ce80f-111">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="ce80f-111">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ce80f-112">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ce80f-112">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ce80f-113">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ce80f-113">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ce80f-114">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="ce80f-114">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="ce80f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce80f-115">See also</span></span>

- [<span data-ttu-id="ce80f-116">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="ce80f-116">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="ce80f-117">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="ce80f-117">Entity SQL Reference</span></span>](entity-sql-reference.md)

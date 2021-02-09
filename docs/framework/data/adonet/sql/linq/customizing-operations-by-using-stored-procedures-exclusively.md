---
description: '詳細情報: ストアド プロシージャのみによる操作のカスタマイズ'
title: ストアド プロシージャのみによる操作のカスタマイズ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 4ddcc6b4face1abccb502e12617105a734bb5f0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729550"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="da6ed-103">ストアド プロシージャのみによる操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="da6ed-103">Customizing Operations by Using Stored Procedures Exclusively</span></span>

<span data-ttu-id="da6ed-104">ストアド プロシージャのみを使用してデータにアクセスすることは、一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="da6ed-104">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da6ed-105">例</span><span class="sxs-lookup"><span data-stu-id="da6ed-105">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="da6ed-106">説明</span><span class="sxs-lookup"><span data-stu-id="da6ed-106">Description</span></span>  

 <span data-ttu-id="da6ed-107">最初のクエリ (動的に SQL を実行するクエリ) をストアド プロシージャのラップ メソッド呼び出しで置き換えることで、「[ストアド プロシージャによる操作のカスタマイズ](customizing-operations-by-using-stored-procedures.md)」に用意されたサンプル コードを変更できます。</span><span class="sxs-lookup"><span data-stu-id="da6ed-107">You can modify the example provided in [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="da6ed-108">次の例に示すように、`CustomersByCity` がこのメソッドであることを前提とします。</span><span class="sxs-lookup"><span data-stu-id="da6ed-108">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="da6ed-109">コード</span><span class="sxs-lookup"><span data-stu-id="da6ed-109">Code</span></span>  

 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="da6ed-110">次のコードは、動的 SQL を使わずに実行されます。</span><span class="sxs-lookup"><span data-stu-id="da6ed-110">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="da6ed-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="da6ed-111">See also</span></span>

- [<span data-ttu-id="da6ed-112">既定の動作をオーバーライドするときの開発者の責任</span><span class="sxs-lookup"><span data-stu-id="da6ed-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](responsibilities-of-the-developer-in-overriding-default-behavior.md)

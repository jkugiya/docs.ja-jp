---
description: '詳細情報: 方法:クエリで情報を取得する'
title: '方法: クエリで情報を取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 41774834fe919b28d71691203941cb8e0a8a0397
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802022"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="6e2ed-103">方法: クエリで情報を取得する</span><span class="sxs-lookup"><span data-stu-id="6e2ed-103">How to: Query for Information</span></span>

<span data-ttu-id="6e2ed-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] でのクエリでは、LINQ でのクエリと同じ構文が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e2ed-104">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in LINQ.</span></span> <span data-ttu-id="6e2ed-105">異なる点は、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリ内で参照されるオブジェクトは、データベース内の要素に割り当てられるという点だけです。</span><span class="sxs-lookup"><span data-stu-id="6e2ed-105">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="6e2ed-106">詳細については、「[LINQ クエリの概要 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e2ed-106">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="6e2ed-107">は、作成したクエリを同等の SQL クエリに変換し、それをサーバーに送って処理します。</span><span class="sxs-lookup"><span data-stu-id="6e2ed-107">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="6e2ed-108">LINQ クエリの機能の中には、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションで特に注意を要するものがあります。</span><span class="sxs-lookup"><span data-stu-id="6e2ed-108">Some features of LINQ queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="6e2ed-109">詳しくは、「[クエリの概念](query-concepts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6e2ed-109">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e2ed-110">例</span><span class="sxs-lookup"><span data-stu-id="6e2ed-110">Example</span></span>  

 <span data-ttu-id="6e2ed-111">次のクエリは、ロンドンからの顧客のリストを取得します。</span><span class="sxs-lookup"><span data-stu-id="6e2ed-111">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="6e2ed-112">この例の `Customers` は、Northwind サンプル データベース内のテーブルです。</span><span class="sxs-lookup"><span data-stu-id="6e2ed-112">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6e2ed-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e2ed-113">See also</span></span>

- [<span data-ttu-id="6e2ed-114">オブジェクト モデルの作成</span><span class="sxs-lookup"><span data-stu-id="6e2ed-114">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="6e2ed-115">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="6e2ed-115">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="6e2ed-116">データベースに対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="6e2ed-116">Querying the Database</span></span>](querying-the-database.md)

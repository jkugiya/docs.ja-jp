---
description: '詳細情報: LINQ to SQL の主な機能'
title: LINQ to SQL の主な機能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: adf1d8dfab69db27d15634a12dbdfbfa287dbb4c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791752"
---
# <a name="what-you-can-do-with-linq-to-sql"></a><span data-ttu-id="03e67-103">LINQ to SQL の主な機能</span><span class="sxs-lookup"><span data-stu-id="03e67-103">What You Can Do With LINQ to SQL</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="03e67-104">は、SQL 開発者が期待するすべての主要な機能に対応しています。</span><span class="sxs-lookup"><span data-stu-id="03e67-104">supports all the key capabilities you would expect as a SQL developer.</span></span> <span data-ttu-id="03e67-105">情報の照会、テーブルへの情報の挿入、およびテーブルの情報の更新と削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="03e67-105">You can query for information, and insert, update, and delete information from tables.</span></span>  
  
## <a name="selecting"></a><span data-ttu-id="03e67-106">選択</span><span class="sxs-lookup"><span data-stu-id="03e67-106">Selecting</span></span>  

 <span data-ttu-id="03e67-107">選択 ("*投影*") は、LINQ クエリを任意のプログラミング言語で記述し、そのクエリを実行して結果を取得することにより実現されます。</span><span class="sxs-lookup"><span data-stu-id="03e67-107">Selecting (*projection*) is achieved by just writing a LINQ query in your own programming language, and then executing that query to retrieve the results.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="03e67-108">自体は、必要なすべての操作を、使い慣れた SQL の操作に変換します。</span><span class="sxs-lookup"><span data-stu-id="03e67-108">itself translates all the necessary operations into the necessary SQL operations that you are familiar with.</span></span> <span data-ttu-id="03e67-109">詳細については、「 [LINQ to SQL](index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03e67-109">For more information, see [LINQ to SQL](index.md).</span></span>  
  
 <span data-ttu-id="03e67-110">次の例では、ロンドン在住の顧客の会社名を取得し、コンソール ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="03e67-110">In the following example, the company names of customers from London are retrieved and displayed in the console window.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a><span data-ttu-id="03e67-111">挿入</span><span class="sxs-lookup"><span data-stu-id="03e67-111">Inserting</span></span>  

 <span data-ttu-id="03e67-112">SQL の `Insert`を実行するには、前もって作成したオブジェクト モデルにオブジェクトを追加し、 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の <xref:System.Data.Linq.DataContext>を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="03e67-112">To execute a SQL `Insert`, just add objects to the object model you have created, and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="03e67-113">`Customers` を使って、新規の顧客の情報を <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>テーブルに追加する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="03e67-113">In the following example, a new customer and information about the customer is added to the `Customers` table by using <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a><span data-ttu-id="03e67-114">Updating</span><span class="sxs-lookup"><span data-stu-id="03e67-114">Updating</span></span>  

 <span data-ttu-id="03e67-115">データベース エントリの `Update` (更新) を実行するには、目的の項目をまず取得し、それをオブジェクト モデル内で直接編集します。</span><span class="sxs-lookup"><span data-stu-id="03e67-115">To `Update` a database entry, first retrieve the item and edit it directly in the object model.</span></span> <span data-ttu-id="03e67-116">オブジェクトを変更した後で、 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の <xref:System.Data.Linq.DataContext> を呼び出してデータベースを更新します。</span><span class="sxs-lookup"><span data-stu-id="03e67-116">After you have modified the object, call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to update the database.</span></span>  
  
 <span data-ttu-id="03e67-117">ロンドン出身のすべての顧客を取得する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="03e67-117">In the following example, all customers who are from London are retrieved.</span></span> <span data-ttu-id="03e67-118">その後で、市の名前を "London" から "London - Metro" に変更します。</span><span class="sxs-lookup"><span data-stu-id="03e67-118">Then the name of the city is changed from "London" to "London - Metro".</span></span> <span data-ttu-id="03e67-119">最後に、 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出して、変更をデータベースに送信します。</span><span class="sxs-lookup"><span data-stu-id="03e67-119">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to send the changes to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a><span data-ttu-id="03e67-120">削除中</span><span class="sxs-lookup"><span data-stu-id="03e67-120">Deleting</span></span>  

 <span data-ttu-id="03e67-121">項目を `Delete` (削除) するには、項目を所属先のコレクションから削除してから、 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の <xref:System.Data.Linq.DataContext> を呼び出して、変更をコミットします。</span><span class="sxs-lookup"><span data-stu-id="03e67-121">To `Delete` an item, remove the item from the collection to which it belongs, and then call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to commit the change.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="03e67-122">は連鎖削除操作を認識しません。</span><span class="sxs-lookup"><span data-stu-id="03e67-122">does not recognize cascade-delete operations.</span></span> <span data-ttu-id="03e67-123">制約が適用されているテーブルの行を削除する場合は、「[方法: 行をデータベースから削除する](how-to-delete-rows-from-the-database.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="03e67-123">If you want to delete a row in a table that has constraints against it, see [How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="03e67-124">次の例では、 `CustomerID` が `98128` の顧客をデータベースから取得します。</span><span class="sxs-lookup"><span data-stu-id="03e67-124">In the following example, the customer who has `CustomerID` of `98128` is retrieved from the database.</span></span> <span data-ttu-id="03e67-125">次に、顧客の行が取得されたことを確認した後で、 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> を呼び出して、このオブジェクトをコレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="03e67-125">Then, after confirming that the customer row was retrieved, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> is called to remove that object from the collection.</span></span> <span data-ttu-id="03e67-126">最後に、 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出して、削除をデータベースに転送します。</span><span class="sxs-lookup"><span data-stu-id="03e67-126">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to forward the deletion to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="03e67-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="03e67-127">See also</span></span>

- [<span data-ttu-id="03e67-128">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="03e67-128">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="03e67-129">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="03e67-129">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="03e67-130">はじめに</span><span class="sxs-lookup"><span data-stu-id="03e67-130">Getting Started</span></span>](getting-started.md)

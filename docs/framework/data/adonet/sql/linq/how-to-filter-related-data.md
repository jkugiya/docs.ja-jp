---
description: '詳細情報: 方法:関連データをフィルター処理する'
title: '方法: 関連データをフィルター処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: d44e0805b82c0c58f9ee19808e078f9f9b337050
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738950"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="b8efc-103">方法: 関連データをフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="b8efc-103">How to: Filter Related Data</span></span>

<span data-ttu-id="b8efc-104">取得したデータの量を制限するサブクエリを指定するには、<xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8efc-104">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8efc-105">例</span><span class="sxs-lookup"><span data-stu-id="b8efc-105">Example</span></span>  

 <span data-ttu-id="b8efc-106">次の例の <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> メソッドは、取得した `Orders` を、その日に出荷されていないものに限定します。</span><span class="sxs-lookup"><span data-stu-id="b8efc-106">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="b8efc-107">この処理を行わないと、サブセットのみが必要な場合でも、すべての `Orders` が取得されることになります。</span><span class="sxs-lookup"><span data-stu-id="b8efc-107">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b8efc-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8efc-108">See also</span></span>

- [<span data-ttu-id="b8efc-109">データベースに対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="b8efc-109">Querying the Database</span></span>](querying-the-database.md)

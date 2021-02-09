---
description: '詳細情報: DataSet の作成'
title: DataSet の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 7a52c6e73b5ab3ba4bf384d6bab3640b85929fcc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739652"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="51a66-103">DataSet の作成</span><span class="sxs-lookup"><span data-stu-id="51a66-103">Creating a DataSet</span></span>

<span data-ttu-id="51a66-104"><xref:System.Data.DataSet> のインスタンスを作成するには、<xref:System.Data.DataSet> のコンストラクターを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="51a66-104">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="51a66-105">必要に応じて、引数 name を指定します。</span><span class="sxs-lookup"><span data-stu-id="51a66-105">Optionally specify a name argument.</span></span> <span data-ttu-id="51a66-106">名前を指定しない場合、<xref:System.Data.DataSet> の名前は "NewDataSet" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="51a66-106">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="51a66-107">また、既存の <xref:System.Data.DataSet> に基づいて新しい <xref:System.Data.DataSet> を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="51a66-107">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="51a66-108">既存の <xref:System.Data.DataSet> の正確なコピーを新しい <xref:System.Data.DataSet> として作成できるのは、リレーショナル構造またはスキーマはコピーするけれども既存の <xref:System.Data.DataSet> からのデータは含まない <xref:System.Data.DataSet> のクローン、または <xref:System.Data.DataSet> メソッドを使用して既存の <xref:System.Data.DataSet> から変更された行だけを含む <xref:System.Data.DataSet.GetChanges%2A> のサブセットのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="51a66-108">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="51a66-109">詳しくは、「[DataSet の内容のコピー](copying-dataset-contents.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="51a66-109">For more information, see [Copying DataSet Contents](copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="51a66-110"><xref:System.Data.DataSet> のインスタンスの作成方法を示すコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="51a66-110">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="51a66-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="51a66-111">See also</span></span>

- [<span data-ttu-id="51a66-112">DataAdapter からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="51a66-112">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="51a66-113">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="51a66-113">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="51a66-114">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="51a66-114">ADO.NET Overview</span></span>](../ado-net-overview.md)

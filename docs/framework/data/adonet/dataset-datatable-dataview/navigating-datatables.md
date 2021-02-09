---
description: '詳細情報: DataTable の移動'
title: DataTable の移動
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 0564af241adc082ef1b736f2e4a561328fbcc976
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651783"
---
# <a name="navigating-datatables"></a><span data-ttu-id="a17be-103">DataTable の移動</span><span class="sxs-lookup"><span data-stu-id="a17be-103">Navigating DataTables</span></span>

<span data-ttu-id="a17be-104"><xref:System.Data.DataTableReader> は、1 つ以上の <xref:System.Data.DataTable> オブジェクトの内容を、読み取り専用、前方参照専用の 1 つ以上の結果セットとして取得します。</span><span class="sxs-lookup"><span data-stu-id="a17be-104">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="a17be-105"><xref:System.Data.DataTableReader> メソッドの呼び出しにより DataTableReader を作成した場合、<xref:System.Data.DataSet.CreateDataReader%2A> に複数の結果セットが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a17be-105">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="a17be-106">結果セットが複数ある場合、<xref:System.Data.DataTableReader.NextResult%2A> メソッドは、カーソルを次の結果セットに移動します。</span><span class="sxs-lookup"><span data-stu-id="a17be-106">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="a17be-107">これは前方参照専用です。</span><span class="sxs-lookup"><span data-stu-id="a17be-107">This is a forward-only process.</span></span> <span data-ttu-id="a17be-108">前の結果セットに戻ることはできません。</span><span class="sxs-lookup"><span data-stu-id="a17be-108">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a17be-109">例</span><span class="sxs-lookup"><span data-stu-id="a17be-109">Example</span></span>  

 <span data-ttu-id="a17be-110">次の例では、`TestConstructor` メソッドで 2 つの <xref:System.Data.DataTable> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a17be-110">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="a17be-111"><xref:System.Data.DataTableReader> クラスを対象としたこのコンストラクターを示すために、この例では、2 つの **DataTable** が含まれる配列に基づいた新しい **DataTableReader** を作成し、単純な操作を実行して、最初の数列の内容をコンソール ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="a17be-111">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a17be-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="a17be-112">See also</span></span>

- [<span data-ttu-id="a17be-113">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="a17be-113">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="a17be-114">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="a17be-114">ADO.NET Overview</span></span>](../ado-net-overview.md)

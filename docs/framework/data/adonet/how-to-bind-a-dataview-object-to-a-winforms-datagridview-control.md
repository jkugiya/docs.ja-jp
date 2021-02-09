---
description: '詳細情報: 方法:DataView オブジェクトを Windows フォーム DataGridView コントロールにバインドする'
title: '方法: DataView オブジェクトを Windows フォーム DataGridView コントロールにバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 59bc1a0f6b7b2b0d6da4fa6d88e06922d95c9f46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723908"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a><span data-ttu-id="149dd-103">方法: DataView オブジェクトを Windows フォーム DataGridView コントロールにバインドする</span><span class="sxs-lookup"><span data-stu-id="149dd-103">How to: Bind a DataView Object to a Windows Forms DataGridView Control</span></span>

<span data-ttu-id="149dd-104"><xref:System.Windows.Forms.DataGridView> コントロールには、データを表形式で表示するための強力で柔軟な機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="149dd-104">The <xref:System.Windows.Forms.DataGridView> control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="149dd-105"><xref:System.Windows.Forms.DataGridView> コントロールは、標準 Windows フォーム データ バインディング モデルをサポートするため、<xref:System.Data.DataView> およびその他の各種のデータ ソースにバインドします。</span><span class="sxs-lookup"><span data-stu-id="149dd-105">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to <xref:System.Data.DataView> and a variety of other data sources.</span></span> <span data-ttu-id="149dd-106">ただし、ほとんどの状況では、データ ソースとの対話の詳細を管理する <xref:System.Windows.Forms.BindingSource> コンポーネントにバインドします。</span><span class="sxs-lookup"><span data-stu-id="149dd-106">In most situations, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component that will manage the details of interacting with the data source.</span></span>  
  
 <span data-ttu-id="149dd-107"><xref:System.Windows.Forms.DataGridView> コントロールについて詳しくは、「[DataGridView コントロールの概要](/dotnet/desktop/winforms/controls/datagridview-control-overview-windows-forms)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="149dd-107">For more information about the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](/dotnet/desktop/winforms/controls/datagridview-control-overview-windows-forms).</span></span>  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a><span data-ttu-id="149dd-108">DataGridView コントロールを DataView に接続するには</span><span class="sxs-lookup"><span data-stu-id="149dd-108">To connect a DataGridView control to a DataView</span></span>  
  
1. <span data-ttu-id="149dd-109">データベースからデータを取得する操作の詳細を処理するメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="149dd-109">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="149dd-110">次のコード例では、`GetData` コンポーネントを初期化する <xref:System.Data.SqlClient.SqlDataAdapter> メソッドを実装し、これを使用して <xref:System.Data.DataSet> に値を設定します。</span><span class="sxs-lookup"><span data-stu-id="149dd-110">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to fill a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="149dd-111">`connectionString` 変数は、使用しているデータベースに合った値に設定してください。</span><span class="sxs-lookup"><span data-stu-id="149dd-111">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="149dd-112">AdventureWorks SQL Server サンプル データベースがインストールされているサーバーにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="149dd-112">You will need access to a server with the AdventureWorks SQL Server sample database installed.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. <span data-ttu-id="149dd-113">フォームの <xref:System.Windows.Forms.Form.Load> イベント ハンドラーで、<xref:System.Windows.Forms.DataGridView> コントロールを <xref:System.Windows.Forms.BindingSource> コンポーネントにバインドし、`GetData` メソッドを呼び出してデータベースからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="149dd-113">In the <xref:System.Windows.Forms.Form.Load> event handler of your form, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span> <span data-ttu-id="149dd-114"><xref:System.Data.DataView> は、Contact <xref:System.Data.DataTable> に対する LINQ to DataSet クエリから作成された後、<xref:System.Windows.Forms.BindingSource> コンポーネントにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="149dd-114">The <xref:System.Data.DataView> is created from a LINQ to DataSet query over the Contact <xref:System.Data.DataTable> and is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a><span data-ttu-id="149dd-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="149dd-115">See also</span></span>

- [<span data-ttu-id="149dd-116">データ バインディングと LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="149dd-116">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)

---
description: '詳細情報: DataTable 内のデータの操作'
title: DataTable 内のデータの操作
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: 41f70bd15a023f8d92733bdce142666a08245d9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652069"
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="7358e-103">DataTable 内のデータの操作</span><span class="sxs-lookup"><span data-stu-id="7358e-103">Manipulating Data in a DataTable</span></span>

<span data-ttu-id="7358e-104"><xref:System.Data.DataTable> 内に <xref:System.Data.DataSet> を作成した後で、データベース内のテーブルを使用する場合と同じ操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="7358e-104">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="7358e-105">テーブル内のデータの追加、表示、編集、および削除を実行したり、エラーとイベントを監視したり、テーブル内のデータを照会したりできます。</span><span class="sxs-lookup"><span data-stu-id="7358e-105">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="7358e-106">**DataTable** 内のデータを変更するときに、変更が正確かどうかを検証したり、変更を受け入れるか拒否するかをプログラムによって決定したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="7358e-106">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7358e-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7358e-107">In This Section</span></span>  

 [<span data-ttu-id="7358e-108">DataTable へのデータの追加</span><span class="sxs-lookup"><span data-stu-id="7358e-108">Adding Data to a DataTable</span></span>](adding-data-to-a-datatable.md)  
 <span data-ttu-id="7358e-109">新しい行を作成してテーブルに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7358e-109">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="7358e-110">DataTable 内のデータの表示</span><span class="sxs-lookup"><span data-stu-id="7358e-110">Viewing Data in a DataTable</span></span>](viewing-data-in-a-datatable.md)  
 <span data-ttu-id="7358e-111">元のバージョンのデータや現在のバージョンのデータを含め、行内のデータにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7358e-111">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="7358e-112">Load メソッド</span><span class="sxs-lookup"><span data-stu-id="7358e-112">The Load Method</span></span>](the-load-method.md)  
 <span data-ttu-id="7358e-113">**Load** メソッドを使用して、**DataTable** に行を格納する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7358e-113">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="7358e-114">DataTable の編集</span><span class="sxs-lookup"><span data-stu-id="7358e-114">DataTable Edits</span></span>](datatable-edits.md)  
 <span data-ttu-id="7358e-115">提示された変更が検証され、受け入れられるまで行への実際の変更を保留しておく方法も含め、行内のデータを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7358e-115">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="7358e-116">行の状態とバージョン</span><span class="sxs-lookup"><span data-stu-id="7358e-116">Row States and Row Versions</span></span>](row-states-and-row-versions.md)  
 <span data-ttu-id="7358e-117">行のさまざまな状態について説明します。</span><span class="sxs-lookup"><span data-stu-id="7358e-117">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="7358e-118">DataRow の削除</span><span class="sxs-lookup"><span data-stu-id="7358e-118">DataRow Deletion</span></span>](datarow-deletion.md)  
 <span data-ttu-id="7358e-119">テーブルから行を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7358e-119">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="7358e-120">行エラー情報</span><span class="sxs-lookup"><span data-stu-id="7358e-120">Row Error Information</span></span>](row-error-information.md)  
 <span data-ttu-id="7358e-121">アプリケーション内でのデータに関する問題を解決するために、行ごとのエラー情報を挿入する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7358e-121">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="7358e-122">AcceptChange と RejectChange</span><span class="sxs-lookup"><span data-stu-id="7358e-122">AcceptChanges and RejectChanges</span></span>](acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="7358e-123">行への変更を受け入れたり拒否したりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7358e-123">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7358e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="7358e-124">See also</span></span>

- [<span data-ttu-id="7358e-125">DataTables</span><span class="sxs-lookup"><span data-stu-id="7358e-125">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="7358e-126">DataTable イベントの処理</span><span class="sxs-lookup"><span data-stu-id="7358e-126">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="7358e-127">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="7358e-127">ADO.NET Overview</span></span>](../ado-net-overview.md)

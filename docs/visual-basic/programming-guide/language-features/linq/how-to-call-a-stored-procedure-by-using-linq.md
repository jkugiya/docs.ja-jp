---
description: '詳細情報: 方法:LINQ を使用してストアド プロシージャを呼び出す (Visual Basic)'
title: '方法: LINQ を使用してストアド プロシージャを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: f6fca7ac008e5f0d5f68fdf9c192eaadae9412ef
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466329"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="5ab06-103">方法: LINQ を使用してストアド プロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ab06-103">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="5ab06-104">統合言語クエリ (LINQ) を使用すると、ストアド プロシージャなどのデータベース オブジェクトを始めとするデータベース情報に簡単にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5ab06-104">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="5ab06-105">次の例では、SQL Server データベースのストアド プロシージャを呼び出すアプリケーションを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5ab06-105">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="5ab06-106">このサンプルでは、データベース内の 2 つの異なるストアド プロシージャを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5ab06-106">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="5ab06-107">各プロシージャは、クエリの結果を返します。</span><span class="sxs-lookup"><span data-stu-id="5ab06-107">Each procedure returns the results of a query.</span></span> <span data-ttu-id="5ab06-108">プロシージャのうちの 1 つは入力パラメーターを受け取りますが、もう 1 つのプロシージャはパラメーターを受け取りません。</span><span class="sxs-lookup"><span data-stu-id="5ab06-108">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="5ab06-109">このトピックの例では、Northwind サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="5ab06-109">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="5ab06-110">開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード センターからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="5ab06-110">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="5ab06-111">手順については、「[サンプル データベースのダウンロード](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ab06-111">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="5ab06-112">データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="5ab06-112">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="5ab06-113">Visual Studio で、 **[表示]** メニューの **[サーバー エクスプローラー]** / **[データベース エクスプローラー]** をクリックして、 **[サーバー エクスプローラー]** / **[データベース エクスプローラー]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="5ab06-113">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="5ab06-114">**[サーバー エクスプローラー]** / **[データベース エクスプローラー]** で **[データ接続]** を右クリックし、 **[接続の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ab06-114">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="5ab06-115">Northwind サンプル データベースへの有効な接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ab06-115">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="5ab06-116">LINQ to SQL ファイルを含むプロジェクトを追加するには</span><span class="sxs-lookup"><span data-stu-id="5ab06-116">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="5ab06-117">Visual Studio で、 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ab06-117">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="5ab06-118">プロジェクト タイプとして Visual Basic **[Windows フォーム アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5ab06-118">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="5ab06-119">**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ab06-119">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="5ab06-120">**[LINQ to SQL クラス]** 項目テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="5ab06-120">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="5ab06-121">そのファイルに `northwind.dbml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="5ab06-121">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="5ab06-122">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ab06-122">Click **Add**.</span></span> <span data-ttu-id="5ab06-123">オブジェクト リレーショナル デザイナー (O/R デザイナー) が northwind.dbml ファイル用に開きます。</span><span class="sxs-lookup"><span data-stu-id="5ab06-123">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="5ab06-124">ストアド プロシージャを O/R デザイナーに追加するには</span><span class="sxs-lookup"><span data-stu-id="5ab06-124">To add stored procedures to the O/R Designer</span></span>  
  
1. <span data-ttu-id="5ab06-125">**[サーバー エクスプローラー]** / **[データベース エクスプローラー]** で、Northwind データベースへの接続を展開します。</span><span class="sxs-lookup"><span data-stu-id="5ab06-125">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="5ab06-126">**[ストアド プロシージャ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="5ab06-126">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="5ab06-127">O/R デザイナーを閉じている場合は、前に追加した northwind.dbml ファイルをダブルクリックして再度開くことができます。</span><span class="sxs-lookup"><span data-stu-id="5ab06-127">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="5ab06-128">**Sales by Year** ストアド プロシージャをクリックし、デザイナーの右ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5ab06-128">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="5ab06-129">**Ten Most Expensive Products** ストアド プロシージャをクリックして、デザイナーの右ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5ab06-129">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3. <span data-ttu-id="5ab06-130">変更を保存し、デザイナーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="5ab06-130">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="5ab06-131">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="5ab06-131">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="5ab06-132">ストアド プロシージャの結果を表示するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="5ab06-132">To add code to display the results of the stored procedures</span></span>  
  
1. <span data-ttu-id="5ab06-133">**[ツールボックス]** から、プロジェクトの既定の Windows フォームである Form1 に <xref:System.Windows.Forms.DataGridView> コントロールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5ab06-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="5ab06-134">Form1 をダブルクリックして、`Load` イベントにコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5ab06-134">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3. <span data-ttu-id="5ab06-135">ストアド プロシージャを O/R デザイナーに追加したときに、<xref:System.Data.Linq.DataContext> オブジェクトがプロジェクトに追加されました。</span><span class="sxs-lookup"><span data-stu-id="5ab06-135">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="5ab06-136">このオブジェクトには、これらのプロシージャにアクセスするために必要なコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5ab06-136">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="5ab06-137">プロジェクトの <xref:System.Data.Linq.DataContext> オブジェクトの名前は、.dbml ファイルの名前に基づいて付けられます。</span><span class="sxs-lookup"><span data-stu-id="5ab06-137">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="5ab06-138">このプロジェクトでは、<xref:System.Data.Linq.DataContext> オブジェクトに `northwindDataContext` という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="5ab06-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="5ab06-139">コード内で <xref:System.Data.Linq.DataContext> のインスタンスを作成し、O/R デザイナーによって指定されたストアド プロシージャのメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5ab06-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="5ab06-140"><xref:System.Windows.Forms.DataGridView> オブジェクトにバインドするために、ストアド プロシージャの結果に対して <xref:System.Linq.Enumerable.ToList%2A> メソッドを呼び出すことで、クエリの即時実行を強制することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="5ab06-140">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="5ab06-141">次のコードを `Load` イベントに追加して、データ コンテキストのメソッドとして公開されているストアド プロシージャのいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5ab06-141">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. <span data-ttu-id="5ab06-142">F5 キーを押してプロジェクトを実行し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="5ab06-142">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab06-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ab06-143">See also</span></span>

- [<span data-ttu-id="5ab06-144">LINQ</span><span class="sxs-lookup"><span data-stu-id="5ab06-144">LINQ</span></span>](index.md)
- [<span data-ttu-id="5ab06-145">クエリ</span><span class="sxs-lookup"><span data-stu-id="5ab06-145">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="5ab06-146">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5ab06-146">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="5ab06-147">DataContext メソッド (O/R デザイナー)</span><span class="sxs-lookup"><span data-stu-id="5ab06-147">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="5ab06-148">方法: 更新、挿入、および削除を実行するストアド プロシージャを割り当てる (O/R デザイナー)</span><span class="sxs-lookup"><span data-stu-id="5ab06-148">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)

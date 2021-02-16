---
description: '詳細情報: 方法:LINQ を使用してクエリ結果をフィルター処理する (Visual Basic)'
title: '方法: LINQ を使用してクエリ結果をフィルター処理する'
ms.date: 07/20/2015
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
ms.openlocfilehash: b3f861d9a7fb7b601606f190ad3bfbeef054cad7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100422797"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="0236e-103">方法: LINQ を使用してクエリ結果をフィルター処理する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0236e-103">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="0236e-104">統合言語クエリ (LINQ) を使用すると、データベース情報に簡単にアクセスしてクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0236e-104">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>

<span data-ttu-id="0236e-105">次の例は、SQL Server データベースに対してクエリを実行し、`Where` 句を使用して特定の値で結果をフィルター処理する新しいアプリケーションの作成方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0236e-105">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="0236e-106">詳細については、「[Where 句](../../../language-reference/queries/where-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0236e-106">For more information, see [Where Clause](../../../language-reference/queries/where-clause.md).</span></span>

<span data-ttu-id="0236e-107">このトピックの例では、Northwind サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="0236e-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="0236e-108">開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード センターからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="0236e-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="0236e-109">手順については、「[サンプル データベースのダウンロード](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0236e-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="0236e-110">データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="0236e-110">To create a connection to a database</span></span>

1. <span data-ttu-id="0236e-111">Visual Studio で、 **[表示]** メニューの **[サーバー エクスプローラー]** / **[データベース エクスプローラー]** をクリックして、 **[サーバー エクスプローラー]** / **[データベース エクスプローラー]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="0236e-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>

2. <span data-ttu-id="0236e-112">**[サーバー エクスプローラー]** / **[データベース エクスプローラー]** で **[データ接続]** を右クリックし、 **[接続の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0236e-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>

3. <span data-ttu-id="0236e-113">Northwind サンプル データベースへの有効な接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="0236e-113">Specify a valid connection to the Northwind sample database.</span></span>

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="0236e-114">LINQ to SQL ファイルを含むプロジェクトを追加するには</span><span class="sxs-lookup"><span data-stu-id="0236e-114">To add a project that contains a LINQ to SQL file</span></span>

1. <span data-ttu-id="0236e-115">Visual Studio で、 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0236e-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="0236e-116">プロジェクト タイプとして Visual Basic **[Windows フォーム アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0236e-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="0236e-117">**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0236e-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="0236e-118">**[LINQ to SQL クラス]** 項目テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="0236e-118">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="0236e-119">そのファイルに `northwind.dbml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="0236e-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="0236e-120">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0236e-120">Click **Add**.</span></span> <span data-ttu-id="0236e-121">オブジェクト リレーショナル デザイナー (O/R デザイナー) が northwind.dbml ファイル用に開きます。</span><span class="sxs-lookup"><span data-stu-id="0236e-121">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>

## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="0236e-122">O/R デザイナーにクエリを実行するテーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="0236e-122">To add tables to query to the O/R Designer</span></span>

1. <span data-ttu-id="0236e-123">**[サーバー エクスプローラー]** / **[データベース エクスプローラー]** で、Northwind データベースへの接続を展開します。</span><span class="sxs-lookup"><span data-stu-id="0236e-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="0236e-124">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="0236e-124">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="0236e-125">O/R デザイナーを閉じている場合は、前に追加した northwind.dbml ファイルをダブルクリックして再度開くことができます。</span><span class="sxs-lookup"><span data-stu-id="0236e-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>

2. <span data-ttu-id="0236e-126">Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0236e-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="0236e-127">Orders テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0236e-127">Click the Orders table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="0236e-128">デザイナーによって、プロジェクトの新しい `Customer` と `Order` オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0236e-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="0236e-129">デザイナーによってテーブル間のリレーションシップが自動的に検出され、関連するオブジェクトの子プロパティが作成されることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="0236e-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="0236e-130">たとえば、IntelliSense では、`Customer` オブジェクトに、その顧客に関連するすべての注文の `Orders` プロパティがあることを示します。</span><span class="sxs-lookup"><span data-stu-id="0236e-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>

3. <span data-ttu-id="0236e-131">変更を保存し、デザイナーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0236e-131">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="0236e-132">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="0236e-132">Save your project.</span></span>

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="0236e-133">データベースに対してクエリを実行し、結果を表示するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="0236e-133">To add code to query the database and display the results</span></span>

1. <span data-ttu-id="0236e-134">**[ツールボックス]** から、プロジェクトの既定の Windows フォームである Form1 に <xref:System.Windows.Forms.DataGridView> コントロールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0236e-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="0236e-135">Form1 をダブルクリックして、コードをフォームの `Load` イベントに追加します。</span><span class="sxs-lookup"><span data-stu-id="0236e-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>

3. <span data-ttu-id="0236e-136">テーブルを O/R デザイナーに追加したときに、<xref:System.Data.Linq.DataContext> オブジェクトがプロジェクトに追加されました。</span><span class="sxs-lookup"><span data-stu-id="0236e-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="0236e-137">このオブジェクトには、各テーブルの個々のオブジェクトとコレクションに加え、それらのテーブルにアクセスするために必要なコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0236e-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="0236e-138">プロジェクトの <xref:System.Data.Linq.DataContext> オブジェクトの名前は、.dbml ファイルの名前に基づいて付けられます。</span><span class="sxs-lookup"><span data-stu-id="0236e-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="0236e-139">このプロジェクトでは、<xref:System.Data.Linq.DataContext> オブジェクトに `northwindDataContext` という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="0236e-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

    <span data-ttu-id="0236e-140">コードで <xref:System.Data.Linq.DataContext> のインスタンスを作成し、O/R デザイナーによって指定されたテーブルに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0236e-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>

    <span data-ttu-id="0236e-141">次のコードを `Load` イベントに追加し、データ コンテキストのプロパティとして公開されているテーブルに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="0236e-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="0236e-142">クエリでは結果がフィルター処理され、`London` にある顧客のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="0236e-142">The query filters the results and returns only customers that are located in `London`.</span></span>

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. <span data-ttu-id="0236e-143">F5 キーを押してプロジェクトを実行し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="0236e-143">Press F5 to run your project and view the results.</span></span>

5. <span data-ttu-id="0236e-144">他にも、次のようなフィルターをいくつか試すことができます。</span><span class="sxs-lookup"><span data-stu-id="0236e-144">Following are some other filters that you can try.</span></span>

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a><span data-ttu-id="0236e-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="0236e-145">See also</span></span>

- [<span data-ttu-id="0236e-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="0236e-146">LINQ</span></span>](index.md)
- [<span data-ttu-id="0236e-147">クエリ</span><span class="sxs-lookup"><span data-stu-id="0236e-147">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="0236e-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0236e-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="0236e-149">DataContext メソッド (O/R デザイナー)</span><span class="sxs-lookup"><span data-stu-id="0236e-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)

---
description: '詳細情報: 方法:LINQ を使用してデータベースのデータを変更する (Visual Basic)'
title: '方法: LINQ を使用してデータベースのデータを変更する'
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: b58ca542fbc6f4d63705e45b53edc8ded83ab88b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100422771"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="875e2-103">方法: LINQ を使用してデータベースのデータを変更する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="875e2-103">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="875e2-104">統合言語クエリ (LINQ) というクエリを使用すると、簡単にデータベース情報にアクセスして、データベースの値を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="875e2-104">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>

<span data-ttu-id="875e2-105">次の例は、SQL Server データベースの情報を取得して更新する新しいアプリケーションを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="875e2-105">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>

<span data-ttu-id="875e2-106">このトピックの例では、Northwind サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="875e2-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="875e2-107">開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード センターからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="875e2-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="875e2-108">手順については、「[サンプル データベースのダウンロード](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="875e2-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="875e2-109">データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="875e2-109">To create a connection to a database</span></span>

1. <span data-ttu-id="875e2-110">Visual Studio で、 **[表示]** メニューをクリックして **[サーバー エクスプローラー]** / **[データベース エクスプローラー]** を開き、 **[サーバー エクスプローラー]** / **[データベース エクスプローラー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="875e2-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>

2. <span data-ttu-id="875e2-111">**[サーバー エクスプローラー]** / **[データベース エクスプローラー]** で **[データ接続]** を右クリックし、 **[接続の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="875e2-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>

3. <span data-ttu-id="875e2-112">Northwind サンプル データベースへの有効な接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="875e2-112">Specify a valid connection to the Northwind sample database.</span></span>

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="875e2-113">LINQ to SQL ファイルを含むプロジェクトを追加するには</span><span class="sxs-lookup"><span data-stu-id="875e2-113">To add a Project with a LINQ to SQL file</span></span>

1. <span data-ttu-id="875e2-114">Visual Studio で、 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="875e2-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="875e2-115">プロジェクト タイプとして Visual Basic **[Windows フォーム アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="875e2-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="875e2-116">**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="875e2-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="875e2-117">**[LINQ to SQL クラス]** 項目テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="875e2-117">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="875e2-118">そのファイルに `northwind.dbml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="875e2-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="875e2-119">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="875e2-119">Click **Add**.</span></span> <span data-ttu-id="875e2-120">オブジェクト リレーショナル デザイナー (O/R デザイナー) が `northwind.dbml` ファイル用に開きます。</span><span class="sxs-lookup"><span data-stu-id="875e2-120">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="875e2-121">デザイナーにクエリを実行して変更するテーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="875e2-121">To add tables to query and modify to the designer</span></span>

1. <span data-ttu-id="875e2-122">**[サーバー エクスプローラー]** / **[データベース エクスプローラー]** で、Northwind データベースへの接続を展開します。</span><span class="sxs-lookup"><span data-stu-id="875e2-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="875e2-123">**[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="875e2-123">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="875e2-124">O/R デザイナーを閉じている場合は、前に追加した `northwind.dbml` ファイルをダブルクリックして再度開くことができます。</span><span class="sxs-lookup"><span data-stu-id="875e2-124">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>

2. <span data-ttu-id="875e2-125">Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="875e2-125">Click the Customers table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="875e2-126">デザイナーによって、プロジェクトの新しい Customer オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="875e2-126">The designer creates a new Customer object for your project.</span></span>

3. <span data-ttu-id="875e2-127">変更を保存し、デザイナーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="875e2-127">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="875e2-128">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="875e2-128">Save your project.</span></span>

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="875e2-129">データベースを変更して結果を表示するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="875e2-129">To add code to modify the database and display the results</span></span>

1. <span data-ttu-id="875e2-130">**[ツールボックス]** から、プロジェクトの既定の Windows フォームである Form1 に <xref:System.Windows.Forms.DataGridView> コントロールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="875e2-130">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="875e2-131">テーブルを O/R デザイナーに追加したときに、デザイナーによって <xref:System.Data.Linq.DataContext> オブジェクトがプロジェクトに追加されました。</span><span class="sxs-lookup"><span data-stu-id="875e2-131">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="875e2-132">このオブジェクトには、Customers テーブルにアクセスするために使用できるコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="875e2-132">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="875e2-133">また、ローカルの Customer オブジェクトとテーブルの Customers コレクションを定義するコードも含まれています。</span><span class="sxs-lookup"><span data-stu-id="875e2-133">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="875e2-134">プロジェクトの <xref:System.Data.Linq.DataContext> オブジェクトの名前は、.dbml ファイルの名前に基づいて付けられます。</span><span class="sxs-lookup"><span data-stu-id="875e2-134">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="875e2-135">このプロジェクトでは、<xref:System.Data.Linq.DataContext> オブジェクトに `northwindDataContext` という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="875e2-135">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

     <span data-ttu-id="875e2-136">コードで <xref:System.Data.Linq.DataContext> オブジェクトのインスタンスを作成し、O/R デザイナーによって指定された Customers コレクションに対してクエリを実行し、変更することができます。</span><span class="sxs-lookup"><span data-stu-id="875e2-136">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="875e2-137">Customers コレクションに加えた変更は、<xref:System.Data.Linq.DataContext> オブジェクトの <xref:System.Data.Linq.DataContext.SubmitChanges%2A> メソッドを呼び出すことによって送信されるまで、データベースに反映されません。</span><span class="sxs-lookup"><span data-stu-id="875e2-137">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>

     <span data-ttu-id="875e2-138">Windows フォームの Form1 をダブルクリックして、<xref:System.Windows.Forms.Form.Load> イベントにコードを追加し、<xref:System.Data.Linq.DataContext> のプロパティとして公開されている Customers テーブルに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="875e2-138">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="875e2-139">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="875e2-139">Add the following code:</span></span>

    ```vb
    Private db As northwindDataContext

    Private Sub Form1_Load(ByVal sender As System.Object,
                           ByVal e As System.EventArgs
                          ) Handles MyBase.Load
      db = New northwindDataContext()

      RefreshData()
    End Sub

    Private Sub RefreshData()
      Dim customers = From cust In db.Customers
                      Where cust.City(0) = "W"
                      Select cust

      DataGridView1.DataSource = customers
    End Sub
    ```

3. <span data-ttu-id="875e2-140">**[ツールボックス]**  から、3 つの <xref:System.Windows.Forms.Button> コントロールをフォームにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="875e2-140">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="875e2-141">最初の `Button` コントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="875e2-141">Select the first `Button` control.</span></span> <span data-ttu-id="875e2-142">**[プロパティ]** ウィンドウで、`Button` コントロールの `Name` プロパティを `AddButton` に、`Text` を `Add` に設定します。</span><span class="sxs-lookup"><span data-stu-id="875e2-142">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="875e2-143">2 番目のボタンを選択し、`Name` プロパティを `UpdateButton` に、`Text` プロパティを `Update` に設定します。</span><span class="sxs-lookup"><span data-stu-id="875e2-143">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="875e2-144">3 番目のボタンを選択し、`Name` プロパティを `DeleteButton` に、`Text` プロパティを `Delete` に設定します。</span><span class="sxs-lookup"><span data-stu-id="875e2-144">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>

4. <span data-ttu-id="875e2-145">**[追加]** ボタンをダブルクリックして、コードをその `Click` イベントに追加します。</span><span class="sxs-lookup"><span data-stu-id="875e2-145">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="875e2-146">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="875e2-146">Add the following code:</span></span>

    ```vb
    Private Sub AddButton_Click(ByVal sender As System.Object,
                                ByVal e As System.EventArgs
                               ) Handles AddButton.Click
      Dim cust As New Customer With {
        .City = "Wellington",
        .CompanyName = "Blue Yonder Airlines",
        .ContactName = "Jill Frank",
        .Country = "New Zealand",
        .CustomerID = "JILLF"}

      db.Customers.InsertOnSubmit(cust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

5. <span data-ttu-id="875e2-147">**[更新]** ボタンをダブルクリックして、コードをその `Click` イベントに追加します。</span><span class="sxs-lookup"><span data-stu-id="875e2-147">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="875e2-148">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="875e2-148">Add the following code:</span></span>

    ```vb
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles UpdateButton.Click
      Dim updateCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

6. <span data-ttu-id="875e2-149">**[削除]** ボタンをダブルクリックして、コードをその `Click` イベントに追加します。</span><span class="sxs-lookup"><span data-stu-id="875e2-149">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="875e2-150">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="875e2-150">Add the following code:</span></span>

    ```vb
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles DeleteButton.Click
      Dim deleteCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      db.Customers.DeleteOnSubmit(deleteCust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

7. <span data-ttu-id="875e2-151">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="875e2-151">Press F5 to run your project.</span></span> <span data-ttu-id="875e2-152">**[追加]** をクリックして、新しいレコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="875e2-152">Click **Add** to add a new record.</span></span> <span data-ttu-id="875e2-153">**[更新]** をクリックして、新しいレコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="875e2-153">Click **Update** to modify the new record.</span></span> <span data-ttu-id="875e2-154">**[削除]** をクリックして、新しいレコードを削除します。</span><span class="sxs-lookup"><span data-stu-id="875e2-154">Click **Delete** to delete the new record.</span></span>

## <a name="see-also"></a><span data-ttu-id="875e2-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="875e2-155">See also</span></span>

- [<span data-ttu-id="875e2-156">LINQ</span><span class="sxs-lookup"><span data-stu-id="875e2-156">LINQ</span></span>](index.md)
- [<span data-ttu-id="875e2-157">クエリ</span><span class="sxs-lookup"><span data-stu-id="875e2-157">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="875e2-158">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="875e2-158">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="875e2-159">DataContext メソッド (O/R デザイナー)</span><span class="sxs-lookup"><span data-stu-id="875e2-159">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="875e2-160">方法: 更新、挿入、および削除を実行するストアド プロシージャを割り当てる (O/R デザイナー)</span><span class="sxs-lookup"><span data-stu-id="875e2-160">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)

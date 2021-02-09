---
description: '詳細情報: チュートリアル: データの操作 (C#)'
title: 'チュートリアル: データの操作 (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: 6176709a2e02d8c06ec54b70cc6e0e4c302509c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729589"
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="399cb-103">チュートリアル: データの操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="399cb-103">Walkthrough: Manipulating Data (C#)</span></span>

<span data-ttu-id="399cb-104">このチュートリアルでは、データベースに対してデータの追加、変更、および削除を行う、基本の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] シナリオ全体を示します。</span><span class="sxs-lookup"><span data-stu-id="399cb-104">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="399cb-105">顧客の追加、顧客名の変更、および注文の削除を行うため、サンプルの Northwind データベースのコピーを使用します。</span><span class="sxs-lookup"><span data-stu-id="399cb-105">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="399cb-106">このチュートリアルは、Visual C# 開発設定を使用して記述されています。</span><span class="sxs-lookup"><span data-stu-id="399cb-106">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="399cb-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="399cb-107">Prerequisites</span></span>  

 <span data-ttu-id="399cb-108">このチュートリアルの前提条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="399cb-108">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="399cb-109">このチュートリアルでは、専用フォルダー ("c:\linqtest6") を使用してファイルを保持します。</span><span class="sxs-lookup"><span data-stu-id="399cb-109">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="399cb-110">チュートリアルを開始する前に、このフォルダーを作成してください。</span><span class="sxs-lookup"><span data-stu-id="399cb-110">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="399cb-111">Northwind サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="399cb-111">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="399cb-112">開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード サイトからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="399cb-112">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="399cb-113">手順については、「[サンプル データベースのダウンロード](downloading-sample-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="399cb-113">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="399cb-114">データベースをダウンロードしたら、northwnd.mdf ファイルを c:\linqtest6 フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="399cb-114">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
- <span data-ttu-id="399cb-115">Northwind データベースから生成された C# コード ファイル。</span><span class="sxs-lookup"><span data-stu-id="399cb-115">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="399cb-116">このファイルを生成するには、オブジェクト リレーショナル デザイナーまたは SQLMetal ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="399cb-116">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="399cb-117">このチュートリアルは、SQLMetal ツールを使用して次のコマンド ラインで作成されています。</span><span class="sxs-lookup"><span data-stu-id="399cb-117">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="399cb-118">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span><span class="sxs-lookup"><span data-stu-id="399cb-118">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="399cb-119">詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="399cb-119">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="399cb-120">概要</span><span class="sxs-lookup"><span data-stu-id="399cb-120">Overview</span></span>  

 <span data-ttu-id="399cb-121">このチュートリアルは、主に次の 6 つの手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="399cb-121">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="399cb-122">Visual Studio で [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="399cb-122">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="399cb-123">プロジェクトにデータベース コード ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="399cb-123">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="399cb-124">新しい顧客オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="399cb-124">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="399cb-125">顧客の連絡先名を変更します。</span><span class="sxs-lookup"><span data-stu-id="399cb-125">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="399cb-126">注文を削除します。</span><span class="sxs-lookup"><span data-stu-id="399cb-126">Deleting an order.</span></span>  
  
- <span data-ttu-id="399cb-127">これらの変更を Northwind データベースに送信します。</span><span class="sxs-lookup"><span data-stu-id="399cb-127">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="399cb-128">LINQ to SQL ソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="399cb-128">Creating a LINQ to SQL Solution</span></span>  

 <span data-ttu-id="399cb-129">最初のタスクに、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロジェクトをビルドおよび実行するために必要な参照を含む Visual Studio ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="399cb-129">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="399cb-130">LINQ to SQL ソリューションを作成するには</span><span class="sxs-lookup"><span data-stu-id="399cb-130">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="399cb-131">Visual Studio の **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="399cb-131">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="399cb-132">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Visual C#]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="399cb-132">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3. <span data-ttu-id="399cb-133">**[テンプレート]** ペインの **[コンソール アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="399cb-133">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="399cb-134">**[プロジェクト名]** ボックスに「**LinqDataManipulationApp**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="399cb-134">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="399cb-135">**[場所]** ボックスで、プロジェクト ファイルを格納する場所を確認します。</span><span class="sxs-lookup"><span data-stu-id="399cb-135">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6. <span data-ttu-id="399cb-136">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="399cb-136">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="399cb-137">LINQ の参照とディレクティブを追加する</span><span class="sxs-lookup"><span data-stu-id="399cb-137">Adding LINQ References and Directives</span></span>  

 <span data-ttu-id="399cb-138">このチュートリアルで使用するアセンブリは、既定ではプロジェクトにインストールされていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="399cb-138">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="399cb-139">System.Data.Linq がプロジェクトの参照として表示されない場合は、次に説明する手順に従って追加してください。</span><span class="sxs-lookup"><span data-stu-id="399cb-139">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="399cb-140">System.Data.Linq を追加するには</span><span class="sxs-lookup"><span data-stu-id="399cb-140">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="399cb-141">**ソリューション エクスプローラー** で、 **[参照設定]** を右クリックし、 **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="399cb-141">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="399cb-142">**[参照の追加]** ダイアログ ボックスで、 **[.NET]** をクリックし、System.Data.Linq アセンブリをクリックします。次に、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="399cb-142">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="399cb-143">アセンブリがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="399cb-143">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="399cb-144">Program.cs の冒頭に、次のディレクティブを追加します。</span><span class="sxs-lookup"><span data-stu-id="399cb-144">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="399cb-145">プロジェクトに Northwind コード ファイルを追加する</span><span class="sxs-lookup"><span data-stu-id="399cb-145">Adding the Northwind Code File to the Project</span></span>  

 <span data-ttu-id="399cb-146">これらの手順では、SQLMetal ツールを使用して Northwind サンプル データベースからコード ファイルを生成していることが前提です。</span><span class="sxs-lookup"><span data-stu-id="399cb-146">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="399cb-147">詳細については、このチュートリアルの「前提条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="399cb-147">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="399cb-148">プロジェクトに Northwind コード ファイルを追加するには</span><span class="sxs-lookup"><span data-stu-id="399cb-148">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="399cb-149">**[プロジェクト]** メニューの **[既存項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="399cb-149">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="399cb-150">**[既存項目の追加]** ダイアログ ボックスで c:\linqtest6\northwind.cs に移動し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="399cb-150">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="399cb-151">northwind.cs ファイルがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="399cb-151">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="399cb-152">データベース接続の設定</span><span class="sxs-lookup"><span data-stu-id="399cb-152">Setting Up the Database Connection</span></span>  

 <span data-ttu-id="399cb-153">最初に、データベースへの接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="399cb-153">First, test your connection to the database.</span></span> <span data-ttu-id="399cb-154">データベースの名前 Northwnd に i の文字が欠けていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="399cb-154">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="399cb-155">次の手順でエラーが生成された後で、northwind.cs ファイルを調べて、Northwind 部分クラスのスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="399cb-155">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="399cb-156">データベース接続を設定してテストするには</span><span class="sxs-lookup"><span data-stu-id="399cb-156">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="399cb-157">Program クラスの `Main` メソッドに次のコードを入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="399cb-157">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2. <span data-ttu-id="399cb-158">この時点でアプリケーションをテストするには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="399cb-158">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="399cb-159">**コンソール** ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="399cb-159">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="399cb-160">**コンソール** ウィンドウで Enter キーを押すか、Visual Studio の **[デバッグ]** メニューの **[デバッグの停止]** をクリックして、アプリケーションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="399cb-160">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="399cb-161">新しいエンティティの作成</span><span class="sxs-lookup"><span data-stu-id="399cb-161">Creating a New Entity</span></span>  

 <span data-ttu-id="399cb-162">新しいエンティティを作成する手順は簡単です。</span><span class="sxs-lookup"><span data-stu-id="399cb-162">Creating a new entity is straightforward.</span></span> <span data-ttu-id="399cb-163">`Customer` キーワードを使用してオブジェクト (`new` など) を作成できます。</span><span class="sxs-lookup"><span data-stu-id="399cb-163">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="399cb-164">以降のセクションでは、ローカル キャッシュのみに変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="399cb-164">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="399cb-165">このチュートリアルの終盤で <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すまで、変更内容はデータベースに送信されません。</span><span class="sxs-lookup"><span data-stu-id="399cb-165">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="399cb-166">新しい Customer エンティティ オブジェクトを追加するには</span><span class="sxs-lookup"><span data-stu-id="399cb-166">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="399cb-167">次のコードを `Customer` メソッド内の `Console.ReadLine();` の前に追加することで、新しい `Main` を作成します。</span><span class="sxs-lookup"><span data-stu-id="399cb-167">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="399cb-168">F5 キーを押してソリューションをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="399cb-168">Press F5 to debug the solution.</span></span>  
  
3. <span data-ttu-id="399cb-169">**コンソール** ウィンドウで Enter キーを押して、デバッグを停止し、このチュートリアルを続行します。</span><span class="sxs-lookup"><span data-stu-id="399cb-169">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="399cb-170">エンティティの更新</span><span class="sxs-lookup"><span data-stu-id="399cb-170">Updating an Entity</span></span>  

 <span data-ttu-id="399cb-171">以降の手順では、`Customer` オブジェクトを取得し、そのプロパティの 1 つを変更します。</span><span class="sxs-lookup"><span data-stu-id="399cb-171">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="399cb-172">顧客の名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="399cb-172">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="399cb-173">`Console.ReadLine();` の前に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="399cb-173">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="399cb-174">エンティティの削除</span><span class="sxs-lookup"><span data-stu-id="399cb-174">Deleting an Entity</span></span>  

 <span data-ttu-id="399cb-175">同じ顧客オブジェクトを使用して、最初の注文を削除できます。</span><span class="sxs-lookup"><span data-stu-id="399cb-175">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="399cb-176">行間のリレーションシップを切断し、データベースから行を削除する方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="399cb-176">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="399cb-177">オブジェクトを削除できることを確認するため、次のコードを `Console.ReadLine` の前に追加します。</span><span class="sxs-lookup"><span data-stu-id="399cb-177">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="399cb-178">行を削除するには</span><span class="sxs-lookup"><span data-stu-id="399cb-178">To delete a row</span></span>  
  
- <span data-ttu-id="399cb-179">`Console.ReadLine();` の直前に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="399cb-179">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="399cb-180">変更内容のデータベースへの送信</span><span class="sxs-lookup"><span data-stu-id="399cb-180">Submitting Changes to the Database</span></span>  

 <span data-ttu-id="399cb-181">最後の手順は、オブジェクトの作成、更新、および削除を実際にデータベースに送信するために必要です。</span><span class="sxs-lookup"><span data-stu-id="399cb-181">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="399cb-182">この手順を行わないと、変更はローカルのみに留まり、クエリの結果には反映されません。</span><span class="sxs-lookup"><span data-stu-id="399cb-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="399cb-183">データベースに変更内容を送信するには</span><span class="sxs-lookup"><span data-stu-id="399cb-183">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="399cb-184">`Console.ReadLine` の直前に次のコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="399cb-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2. <span data-ttu-id="399cb-185">変更内容の送信前と送信後の変化を示すために、次のコードを (`SubmitChanges` の後に) 挿入します。</span><span class="sxs-lookup"><span data-stu-id="399cb-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3. <span data-ttu-id="399cb-186">F5 キーを押してソリューションをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="399cb-186">Press F5 to debug the solution.</span></span>  
  
4. <span data-ttu-id="399cb-187">**コンソール** ウィンドウで Enter キーを押してアプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="399cb-187">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="399cb-188">変更内容を送信して新しい顧客を追加した後で、このソリューションを再度実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="399cb-188">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="399cb-189">ソリューションを再度実行するには、追加する顧客の名前と顧客 ID を変更します。</span><span class="sxs-lookup"><span data-stu-id="399cb-189">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="399cb-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="399cb-190">See also</span></span>

- [<span data-ttu-id="399cb-191">チュートリアルによる学習</span><span class="sxs-lookup"><span data-stu-id="399cb-191">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)

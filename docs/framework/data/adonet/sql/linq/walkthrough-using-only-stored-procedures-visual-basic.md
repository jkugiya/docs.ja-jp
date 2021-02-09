---
description: '詳細情報: チュートリアル: ストアド プロシージャのみの使用 (Visual Basic)'
title: 'チュートリアル: ストアド プロシージャのみの使用 (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: b368bdd5717c0f424192c3eabb8058d633cac61e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791765"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="9534f-103">チュートリアル: ストアド プロシージャのみの使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9534f-103">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>

<span data-ttu-id="9534f-104">このチュートリアルでは、ストアド プロシージャのみを使用してデータにアクセスする、基本の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] シナリオ全体を示します。</span><span class="sxs-lookup"><span data-stu-id="9534f-104">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="9534f-105">この方法は、データ ストアへのアクセス方法を制限する目的で、データベース管理者によってよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="9534f-105">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9534f-106">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションでストアド プロシージャを使用して、既定の動作をオーバーライドすることもできます。これは、`Create`、`Update`、および `Delete` の各プロセスで特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9534f-106">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="9534f-107">詳細については、「[挿入、更新、および削除の各操作のカスタマイズ](customizing-insert-update-and-delete-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9534f-107">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="9534f-108">このチュートリアルでは、Northwind サンプル データベース内のストアド プロシージャにマップされた 2 つのメソッドを使用します:CustOrdersDetail および CustOrderHist。</span><span class="sxs-lookup"><span data-stu-id="9534f-108">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="9534f-109">このマップは、SqlMetal コマンドライン ツールを実行して Visual Basic ファイルを生成したときに作成されます。</span><span class="sxs-lookup"><span data-stu-id="9534f-109">The mapping occurs when you run the SqlMetal command-line tool to generate a Visual Basic file.</span></span> <span data-ttu-id="9534f-110">詳細については、このチュートリアルの「前提条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9534f-110">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="9534f-111">このチュートリアルでは、オブジェクト リレーショナル デザイナーを利用しません。</span><span class="sxs-lookup"><span data-stu-id="9534f-111">This walkthrough does not rely on the Object Relational Designer.</span></span> <span data-ttu-id="9534f-112">Visual Studio を使用している開発者は、O/R デザイナーを使用してストアド プロシージャの機能を実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="9534f-112">Developers using Visual Studio can also use the O/R Designer to implement stored procedure functionality.</span></span> <span data-ttu-id="9534f-113">「[Visual Studio の LINQ to SQL ツール](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9534f-113">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="9534f-114">このチュートリアルは、Visual Basic 開発設定を使用して記述されています。</span><span class="sxs-lookup"><span data-stu-id="9534f-114">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9534f-115">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9534f-115">Prerequisites</span></span>  

 <span data-ttu-id="9534f-116">このチュートリアルの前提条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9534f-116">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="9534f-117">このチュートリアルでは、専用フォルダー ("c:\linqtest3") を使用してファイルを保持します。</span><span class="sxs-lookup"><span data-stu-id="9534f-117">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="9534f-118">チュートリアルを開始する前に、このフォルダーを作成してください。</span><span class="sxs-lookup"><span data-stu-id="9534f-118">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="9534f-119">Northwind サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="9534f-119">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="9534f-120">開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード サイトからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9534f-120">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="9534f-121">手順については、「[サンプル データベースのダウンロード](downloading-sample-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9534f-121">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="9534f-122">データベースをダウンロードしたら、northwnd.mdf ファイルを c:\linqtest3 フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="9534f-122">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
- <span data-ttu-id="9534f-123">Northwind データベースから生成された Visual Basic コード ファイル。</span><span class="sxs-lookup"><span data-stu-id="9534f-123">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="9534f-124">このチュートリアルは、SqlMetal ツールを使用して次のコマンド ラインで作成されています。</span><span class="sxs-lookup"><span data-stu-id="9534f-124">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="9534f-125">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span><span class="sxs-lookup"><span data-stu-id="9534f-125">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="9534f-126">詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9534f-126">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="9534f-127">概要</span><span class="sxs-lookup"><span data-stu-id="9534f-127">Overview</span></span>  

 <span data-ttu-id="9534f-128">このチュートリアルは、主に次の 6 つの手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="9534f-128">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="9534f-129">Visual Studio で [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ソリューションを設定します。</span><span class="sxs-lookup"><span data-stu-id="9534f-129">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="9534f-130">プロジェクトに System.Data.Linq アセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="9534f-130">Adding the System.Data.Linq assembly to the project.</span></span>  
  
- <span data-ttu-id="9534f-131">プロジェクトにデータベース コード ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="9534f-131">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="9534f-132">データベースへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="9534f-132">Creating a connection to the database.</span></span>  
  
- <span data-ttu-id="9534f-133">ユーザー インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="9534f-133">Setting up the user interface.</span></span>  
  
- <span data-ttu-id="9534f-134">アプリケーションを実行およびテストします。</span><span class="sxs-lookup"><span data-stu-id="9534f-134">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="9534f-135">LINQ to SQL ソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="9534f-135">Creating a LINQ to SQL Solution</span></span>  

 <span data-ttu-id="9534f-136">最初のタスクに、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロジェクトをビルドおよび実行するために必要な参照を含む Visual Studio ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="9534f-136">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="9534f-137">LINQ to SQL ソリューションを作成するには</span><span class="sxs-lookup"><span data-stu-id="9534f-137">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="9534f-138">Visual Studio で **[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-138">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="9534f-139">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Visual Basic]** を展開し、 **[Windows]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-139">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3. <span data-ttu-id="9534f-140">**[テンプレート]** ペインの **[Windows フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-140">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4. <span data-ttu-id="9534f-141">**[名前]** ボックスに「**SprocOnlyApp**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9534f-141">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5. <span data-ttu-id="9534f-142">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="9534f-143">Windows フォーム デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="9534f-143">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="9534f-144">LINQ to SQL アセンブリ参照を追加する</span><span class="sxs-lookup"><span data-stu-id="9534f-144">Adding the LINQ to SQL Assembly Reference</span></span>  

 <span data-ttu-id="9534f-145">標準の Windows フォーム アプリケーション テンプレートには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アセンブリは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="9534f-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="9534f-146">次の手順に従って、アセンブリを自分で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9534f-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="9534f-147">System.Data.Linq.dll を追加するには</span><span class="sxs-lookup"><span data-stu-id="9534f-147">To add System.Data.Linq.dll</span></span>  
  
1. <span data-ttu-id="9534f-148">**ソリューション エクスプローラー** で、 **[すべてのファイルを表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-148">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2. <span data-ttu-id="9534f-149">**ソリューション エクスプローラー** で、 **[参照設定]** を右クリックし、 **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-149">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3. <span data-ttu-id="9534f-150">**[参照の追加]** ダイアログ ボックスで、 **[.NET]** をクリックし、System.Data.Linq アセンブリをクリックします。次に、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-150">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="9534f-151">アセンブリがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="9534f-151">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="9534f-152">プロジェクトに Northwind コード ファイルを追加する</span><span class="sxs-lookup"><span data-stu-id="9534f-152">Adding the Northwind Code File to the Project</span></span>  

 <span data-ttu-id="9534f-153">この手順では、事前に SqlMetal ツールを使用して、Northwind サンプル データベースからコード ファイルを生成していることが前提となります。</span><span class="sxs-lookup"><span data-stu-id="9534f-153">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="9534f-154">詳細については、このチュートリアルの「前提条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9534f-154">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="9534f-155">プロジェクトに Northwind コード ファイルを追加するには</span><span class="sxs-lookup"><span data-stu-id="9534f-155">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="9534f-156">**[プロジェクト]** メニューの **[既存項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-156">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="9534f-157">**[既存項目の追加]** ダイアログ ボックスで c:\linqtest3\northwind.vb ファイルに移動し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-157">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="9534f-158">プロジェクトに northwind.vb ファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="9534f-158">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="9534f-159">データベース接続を作成する</span><span class="sxs-lookup"><span data-stu-id="9534f-159">Creating a Database Connection</span></span>  

 <span data-ttu-id="9534f-160">この手順では、Northwind サンプル データベースへの接続を定義します。</span><span class="sxs-lookup"><span data-stu-id="9534f-160">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="9534f-161">このチュートリアルでは、パスとして "c:\linqtest3\northwnd.mdf" を使用します。</span><span class="sxs-lookup"><span data-stu-id="9534f-161">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
### <a name="to-create-the-database-connection"></a><span data-ttu-id="9534f-162">データベース接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="9534f-162">To create the database connection</span></span>  
  
1. <span data-ttu-id="9534f-163">**ソリューション エクスプローラー** で **[Form1.vb]** を右クリックし、 **[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-163">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="9534f-164">コード エディターに `Class Form1` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9534f-164">`Class Form1` appears in the code editor.</span></span>  
  
2. <span data-ttu-id="9534f-165">`Form1` コード ブロックに次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="9534f-165">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="9534f-166">ユーザー インターフェイスを設定する</span><span class="sxs-lookup"><span data-stu-id="9534f-166">Setting up the User Interface</span></span>  

 <span data-ttu-id="9534f-167">このタスクでは、ユーザーがストアド プロシージャを実行してデータベース内のデータにアクセスできるように、インターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9534f-167">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="9534f-168">このチュートリアルで作成するアプリケーションでは、ユーザーはアプリケーションに埋め込まれているストアド プロシージャを使用してのみ、データベース内のデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9534f-168">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="9534f-169">ユーザー インターフェイスを設定するには</span><span class="sxs-lookup"><span data-stu-id="9534f-169">To set up the user interface</span></span>  
  
1. <span data-ttu-id="9534f-170">Windows フォーム デザイナーに戻ります ( **[Form1.vb [デザイン]]** )。</span><span class="sxs-lookup"><span data-stu-id="9534f-170">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2. <span data-ttu-id="9534f-171">**[表示]** メニューの **[ツールボックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-171">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="9534f-172">ツールボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9534f-172">The toolbox opens.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9534f-173">このセクションの残りの手順を実行する間、ツールボックスを開いたままにしておくには、 **[自動的に隠す]** プッシュピンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-173">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3. <span data-ttu-id="9534f-174">ツールボックスから、2 つのボタン、2 つのテキスト ボックス、および 2 つのラベルを **Form1** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9534f-174">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="9534f-175">図のようにコントロールを配置します。</span><span class="sxs-lookup"><span data-stu-id="9534f-175">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="9534f-176">コントロールを簡単に配置できるように、**Form1** のサイズを拡大します。</span><span class="sxs-lookup"><span data-stu-id="9534f-176">Expand **Form1** so that the controls fit easily.</span></span>  
  
4. <span data-ttu-id="9534f-177">**[Label1]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-177">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="9534f-178">**Text** プロパティを「**Label1**」から「**Enter OrderID:** 」に変更します。</span><span class="sxs-lookup"><span data-stu-id="9534f-178">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6. <span data-ttu-id="9534f-179">**Label2** についても同様に、**Text** プロパティを **[Label2]** から **[Enter CustomerID:]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="9534f-179">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7. <span data-ttu-id="9534f-180">同様に、 **[Button1]** の **Text** プロパティを「**Order Details**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="9534f-180">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8. <span data-ttu-id="9534f-181">**Button2** の **Text** プロパティを **[Order History]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="9534f-181">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="9534f-182">すべてのテキストが表示されるように、ボタン コントロールの幅を広げます。</span><span class="sxs-lookup"><span data-stu-id="9534f-182">Widen the button controls so that all the text is visible.</span></span>  
  
### <a name="to-handle-button-clicks"></a><span data-ttu-id="9534f-183">ボタン クリックを処理するには</span><span class="sxs-lookup"><span data-stu-id="9534f-183">To handle button clicks</span></span>  
  
1. <span data-ttu-id="9534f-184">**[Form1]** の **[Order Details]** をダブルクリックして `Button1` イベント ハンドラーを作成し、コード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="9534f-184">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2. <span data-ttu-id="9534f-185">`Button1` のハンドラーに次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="9534f-185">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3. <span data-ttu-id="9534f-186">Form1 の **[Button2]** をダブルクリックして `Button2` イベント ハンドラーを作成し、コード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="9534f-186">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4. <span data-ttu-id="9534f-187">`Button2` のハンドラーに次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="9534f-187">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="9534f-188">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="9534f-188">Testing the Application</span></span>  

 <span data-ttu-id="9534f-189">次に、アプリケーションをテストします。</span><span class="sxs-lookup"><span data-stu-id="9534f-189">Now it is time to test your application.</span></span> <span data-ttu-id="9534f-190">データ ストアに対する操作は、2 つのストアド プロシージャで実行できる処理に制限されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9534f-190">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="9534f-191">つまり、入力した orderID に含まれている製品を返す処理と、入力した CustomerID の注文製品の履歴を返す処理のみを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9534f-191">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="9534f-192">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="9534f-192">To test the application</span></span>  
  
1. <span data-ttu-id="9534f-193">F5 キーを押してデバッグを開始します。</span><span class="sxs-lookup"><span data-stu-id="9534f-193">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="9534f-194">Form1 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9534f-194">Form1 appears.</span></span>  
  
2. <span data-ttu-id="9534f-195">**[Enter OrderID]** ボックスに「**10249**」と入力し、 **[Order Details]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-195">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="9534f-196">注文 10249 に含まれている製品がメッセージ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9534f-196">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="9534f-197">**[OK]** をクリックして、メッセージ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9534f-197">Click **OK** to close the message box.</span></span>  
  
3. <span data-ttu-id="9534f-198">**[Enter CustomerID]** ボックスに「`ALFKI`」と入力し、 **[Order History]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-198">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="9534f-199">メッセージ ボックスに、顧客 ALFKI の注文履歴が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9534f-199">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="9534f-200">**[OK]** をクリックして、メッセージ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9534f-200">Click **OK** to close the message box.</span></span>  
  
4. <span data-ttu-id="9534f-201">**[Enter OrderID]** ボックスに「`123`」と入力し、 **[Order Details]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-201">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="9534f-202">メッセージ ボックスに "No results" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9534f-202">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="9534f-203">**[OK]** をクリックして、メッセージ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9534f-203">Click **OK** to close the message box.</span></span>  
  
5. <span data-ttu-id="9534f-204">**[デバッグ]** メニューの **[デバッグの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9534f-204">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="9534f-205">デバッグ セッションが終了します。</span><span class="sxs-lookup"><span data-stu-id="9534f-205">The debug session closes.</span></span>  
  
6. <span data-ttu-id="9534f-206">操作が終了したら、 **[ファイル]** メニューの **[プロジェクトを閉じる]** をクリックし、メッセージに従ってプロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="9534f-206">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9534f-207">次の手順</span><span class="sxs-lookup"><span data-stu-id="9534f-207">Next Steps</span></span>  

 <span data-ttu-id="9534f-208">いくつかの変更を加えることによって、このプロジェクトを強化できます。</span><span class="sxs-lookup"><span data-stu-id="9534f-208">You can enhance this project by making some changes.</span></span> <span data-ttu-id="9534f-209">たとえば、使用できるストアド プロシージャの一覧をリスト ボックスに表示し、実行するプロシージャをユーザーに選択させることができます。</span><span class="sxs-lookup"><span data-stu-id="9534f-209">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="9534f-210">レポートの出力をテキスト ファイルに送ることもできます。</span><span class="sxs-lookup"><span data-stu-id="9534f-210">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9534f-211">関連項目</span><span class="sxs-lookup"><span data-stu-id="9534f-211">See also</span></span>

- [<span data-ttu-id="9534f-212">チュートリアルによる学習</span><span class="sxs-lookup"><span data-stu-id="9534f-212">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="9534f-213">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="9534f-213">Stored Procedures</span></span>](stored-procedures.md)

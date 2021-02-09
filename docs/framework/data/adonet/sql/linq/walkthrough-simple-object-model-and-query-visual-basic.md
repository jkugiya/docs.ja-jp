---
description: '詳細情報: チュートリアル: 簡単なオブジェクト モデルとクエリ (Visual Basic)'
title: 'チュートリアル: 簡単なオブジェクト モデルとクエリ (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: def2fecf0d6d97841ebd47a1d675f85341053d39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791804"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a><span data-ttu-id="dce20-103">チュートリアル: 簡単なオブジェクト モデルとクエリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dce20-103">Walkthrough: Simple Object Model and Query (Visual Basic)</span></span>

<span data-ttu-id="dce20-104">このチュートリアルでは、複雑さを抑えた、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 全体の基本的なシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="dce20-104">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="dce20-105">サンプルの Northwind データベースにある Customers テーブルのモデル化を行うエンティティ クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dce20-105">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="dce20-106">次に、住所がロンドンの顧客を表示するための簡単なクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="dce20-106">You will then create a simple query to list customers who are located in London.</span></span>

<span data-ttu-id="dce20-107">このチュートリアルでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の考え方を示すために、コード中心の方法をあえて使用しています。</span><span class="sxs-lookup"><span data-stu-id="dce20-107">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="dce20-108">通常は、オブジェクト リレーショナル デザイナーを使用してオブジェクト モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="dce20-108">Normally speaking, you would use the Object Relational Designer to create your object model.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="dce20-109">このチュートリアルは、Visual Basic 開発設定を使用して記述されています。</span><span class="sxs-lookup"><span data-stu-id="dce20-109">This walkthrough was written by using Visual Basic Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dce20-110">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="dce20-110">Prerequisites</span></span>

- <span data-ttu-id="dce20-111">このチュートリアルでは、専用フォルダー ("c:\linqtest") を使用してファイルを保持します。</span><span class="sxs-lookup"><span data-stu-id="dce20-111">This walkthrough uses a dedicated folder ("c:\linqtest") to hold files.</span></span> <span data-ttu-id="dce20-112">チュートリアルを開始する前に、このフォルダーを作成してください。</span><span class="sxs-lookup"><span data-stu-id="dce20-112">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="dce20-113">このチュートリアルには、Northwind サンプル データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="dce20-113">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="dce20-114">開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード サイトからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="dce20-114">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="dce20-115">手順については、「[サンプル データベースのダウンロード](downloading-sample-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dce20-115">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="dce20-116">データベースをダウンロードしたら、ファイルを c:\linqtest フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="dce20-116">After you have downloaded the database, copy the file to the c:\linqtest folder.</span></span>

## <a name="overview"></a><span data-ttu-id="dce20-117">概要</span><span class="sxs-lookup"><span data-stu-id="dce20-117">Overview</span></span>

<span data-ttu-id="dce20-118">このチュートリアルは、主に次の 6 つの手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="dce20-118">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="dce20-119">Visual Studio で [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="dce20-119">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="dce20-120">データベース テーブルにクラスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="dce20-120">Mapping a class to a database table.</span></span>

- <span data-ttu-id="dce20-121">クラスに対し、データベース列を表すプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="dce20-121">Designating properties on the class to represent database columns.</span></span>

- <span data-ttu-id="dce20-122">Northwind データベースへの接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="dce20-122">Specifying the connection to the Northwind database.</span></span>

- <span data-ttu-id="dce20-123">データベースに対して実行する簡単なクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="dce20-123">Creating a simple query to run against the database.</span></span>

- <span data-ttu-id="dce20-124">クエリを実行して結果を観察する。</span><span class="sxs-lookup"><span data-stu-id="dce20-124">Executing the query and observing the results.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="dce20-125">LINQ to SQL ソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="dce20-125">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="dce20-126">最初のタスクに、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロジェクトをビルドおよび実行するために必要な参照を含む Visual Studio ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="dce20-126">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="dce20-127">LINQ to SQL ソリューションを作成するには</span><span class="sxs-lookup"><span data-stu-id="dce20-127">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="dce20-128">**[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dce20-128">On the **File** menu, click **New Project**.</span></span>

2. <span data-ttu-id="dce20-129">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Visual Basic]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dce20-129">In the **Project types** pane of the **New Project** dialog box, click **Visual Basic**.</span></span>

3. <span data-ttu-id="dce20-130">**[テンプレート]** ペインの **[コンソール アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dce20-130">In the **Templates** pane, click **Console Application**.</span></span>

4. <span data-ttu-id="dce20-131">**[名前]** ボックスに「**LinqConsoleApp**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="dce20-131">In the **Name** box, type **LinqConsoleApp**.</span></span>

5. <span data-ttu-id="dce20-132">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dce20-132">Click **OK**.</span></span>

## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="dce20-133">LINQ の参照とディレクティブを追加する</span><span class="sxs-lookup"><span data-stu-id="dce20-133">Adding LINQ References and Directives</span></span>

<span data-ttu-id="dce20-134">このチュートリアルで使用するアセンブリは、既定ではプロジェクトにインストールされていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="dce20-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="dce20-135">`System.Data.Linq` がプロジェクトの参照 (**ソリューション エクスプローラー** で **[すべてのファイルを表示]** をクリックし、 **[参照設定]** ノードを展開) に表示されていない場合は、以下の手順に従って追加します。</span><span class="sxs-lookup"><span data-stu-id="dce20-135">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>

### <a name="to-add-systemdatalinq"></a><span data-ttu-id="dce20-136">System.Data.Linq を追加するには</span><span class="sxs-lookup"><span data-stu-id="dce20-136">To add System.Data.Linq</span></span>

1. <span data-ttu-id="dce20-137">**ソリューション エクスプローラー** で、 **[参照設定]** を右クリックし、 **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dce20-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="dce20-138">**[参照の追加]** ダイアログ ボックスで、 **[.NET]** をクリックし、System.Data.Linq アセンブリをクリックします。次に、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dce20-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="dce20-139">アセンブリがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="dce20-139">The assembly is added to the project.</span></span>

3. <span data-ttu-id="dce20-140">また、 **[参照の追加]** ダイアログ ボックスで、 **[.NET]** をクリックし、System.Windows.Forms までスクロールして、これをクリックします。次に、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dce20-140">Also in the **Add Reference** dialog box, click **.NET**, scroll to and click System.Windows.Forms, and then click **OK**.</span></span>

     <span data-ttu-id="dce20-141">このチュートリアルで使用するメッセージ ボックスをサポートするアセンブリがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="dce20-141">This assembly, which supports the message box in the walkthrough, is added to the project.</span></span>

4. <span data-ttu-id="dce20-142">`Module1` の上に次のディレクティブを追加します。</span><span class="sxs-lookup"><span data-stu-id="dce20-142">Add the following directives above `Module1`:</span></span>

     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]

## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="dce20-143">データベース テーブルにクラスを対応付ける</span><span class="sxs-lookup"><span data-stu-id="dce20-143">Mapping a Class to a Database Table</span></span>

<span data-ttu-id="dce20-144">この手順では、クラスを作成して、データベース テーブルに対応付けます。</span><span class="sxs-lookup"><span data-stu-id="dce20-144">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="dce20-145">このようなクラスのことを "*エンティティ クラス*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="dce20-145">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="dce20-146">対応付けは、<xref:System.Data.Linq.Mapping.TableAttribute> 属性を追加するだけで完了します。</span><span class="sxs-lookup"><span data-stu-id="dce20-146">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="dce20-147"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> プロパティを使用して、データベースのテーブルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="dce20-147">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="dce20-148">エンティティ クラスを作成し、データベース テーブルに対応付けるには</span><span class="sxs-lookup"><span data-stu-id="dce20-148">To create an entity class and map it to a database table</span></span>

- <span data-ttu-id="dce20-149">Module1.vb で、`Sub Main` の直前に次のコードを入力または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="dce20-149">Type or paste the following code into Module1.vb immediately above `Sub Main`:</span></span>

     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="dce20-150">データベース列を表すプロパティをクラスに追加する</span><span class="sxs-lookup"><span data-stu-id="dce20-150">Designating Properties on the Class to Represent Database Columns</span></span>

<span data-ttu-id="dce20-151">この手順では、いくつかのタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="dce20-151">In this step, you accomplish several tasks.</span></span>

- <span data-ttu-id="dce20-152"><xref:System.Data.Linq.Mapping.ColumnAttribute> 属性を使用して、エンティティ クラスの `CustomerID` プロパティおよび `City` プロパティを、データベース テーブルの列を表すものとして指定します。</span><span class="sxs-lookup"><span data-stu-id="dce20-152">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>

- <span data-ttu-id="dce20-153">`CustomerID` プロパティを、データベースの主キー列を表すものとして指定します。</span><span class="sxs-lookup"><span data-stu-id="dce20-153">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>

- <span data-ttu-id="dce20-154">プライベートでの格納用として `_CustomerID` フィールドおよび `_City` フィールドを指定します。</span><span class="sxs-lookup"><span data-stu-id="dce20-154">You designate `_CustomerID` and `_City` fields for private storage.</span></span> <span data-ttu-id="dce20-155">これで、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、ビジネス ロジックを含む場合があるパブリック アクセサーを使用せずに、値を直接格納および取得できます。</span><span class="sxs-lookup"><span data-stu-id="dce20-155">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>

### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="dce20-156">2 つのデータベース列の特性を指定するには</span><span class="sxs-lookup"><span data-stu-id="dce20-156">To represent characteristics of two database columns</span></span>

- <span data-ttu-id="dce20-157">Module1.vb で、`End Class` の直前に次のコードを入力または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="dce20-157">Type or paste the following code into Module1.vb just before `End Class`:</span></span>

     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="dce20-158">Northwind データベースへの接続を指定する</span><span class="sxs-lookup"><span data-stu-id="dce20-158">Specifying the Connection to the Northwind Database</span></span>

<span data-ttu-id="dce20-159">この手順では、<xref:System.Data.Linq.DataContext> オブジェクトを使用して、コードで作成したデータ構造とデータベース本体との間の接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="dce20-159">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="dce20-160">データベースからのオブジェクトの取得や、変更内容の送信では、<xref:System.Data.Linq.DataContext> を仲介役として使用します。</span><span class="sxs-lookup"><span data-stu-id="dce20-160">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>

<span data-ttu-id="dce20-161">また、データベースの Customers テーブルに対するクエリ用として、型指定された論理的なテーブルの役割を果たす `Table(Of Customer)` を宣言します。</span><span class="sxs-lookup"><span data-stu-id="dce20-161">You also declare a `Table(Of Customer)` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="dce20-162">これらのクエリの作成と実行は後の手順で行います。</span><span class="sxs-lookup"><span data-stu-id="dce20-162">You will create and execute these queries in later steps.</span></span>

### <a name="to-specify-the-database-connection"></a><span data-ttu-id="dce20-163">データベース接続を指定するには</span><span class="sxs-lookup"><span data-stu-id="dce20-163">To specify the database connection</span></span>

- <span data-ttu-id="dce20-164">`Sub Main` メソッドに次のコードを入力または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="dce20-164">Type or paste the following code into the `Sub Main` method.</span></span>

     <span data-ttu-id="dce20-165">`northwnd.mdf` ファイルは linqtest フォルダーに置かれているものとします。</span><span class="sxs-lookup"><span data-stu-id="dce20-165">Note that the `northwnd.mdf` file is assumed to be in the linqtest folder.</span></span> <span data-ttu-id="dce20-166">詳細については、このチュートリアルの「前提条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dce20-166">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]

## <a name="creating-a-simple-query"></a><span data-ttu-id="dce20-167">簡単なクエリの作成</span><span class="sxs-lookup"><span data-stu-id="dce20-167">Creating a Simple Query</span></span>

<span data-ttu-id="dce20-168">この手順では、データベースの Customers テーブルから、住所が London の顧客を検索するクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="dce20-168">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="dce20-169">この手順で作成するクエリ コードは、クエリを指定するだけです。</span><span class="sxs-lookup"><span data-stu-id="dce20-169">The query code in this step just describes the query.</span></span> <span data-ttu-id="dce20-170">実行は行いません。</span><span class="sxs-lookup"><span data-stu-id="dce20-170">It does not execute it.</span></span> <span data-ttu-id="dce20-171">このような方法を "*遅延実行*" といいます。</span><span class="sxs-lookup"><span data-stu-id="dce20-171">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="dce20-172">詳細については、「[LINQ クエリの概要 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dce20-172">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

<span data-ttu-id="dce20-173">また、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が生成した SQL コマンドをログに出力します。</span><span class="sxs-lookup"><span data-stu-id="dce20-173">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="dce20-174"><xref:System.Data.Linq.DataContext.Log%2A> を使用したこのログ機能は、デバッグに有効で、データベースに送信されたコマンドが目的のクエリを正確に表しているかどうかを確認するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="dce20-174">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="dce20-175">簡単なクエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="dce20-175">To create a simple query</span></span>

- <span data-ttu-id="dce20-176">`Sub Main` メソッドの `Table(Of Customer)` 宣言の後に次のコードを入力または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="dce20-176">Type or paste the following code into the `Sub Main` method after the `Table(Of Customer)` declaration:</span></span>

     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]

## <a name="executing-the-query"></a><span data-ttu-id="dce20-177">クエリの実行</span><span class="sxs-lookup"><span data-stu-id="dce20-177">Executing the Query</span></span>

<span data-ttu-id="dce20-178">この手順では、実際にクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="dce20-178">In this step, you actually execute the query.</span></span> <span data-ttu-id="dce20-179">ここまでの手順で作成したクエリ式は、結果が必要になるまでは評価されません。</span><span class="sxs-lookup"><span data-stu-id="dce20-179">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="dce20-180">`For Each` の反復処理を開始した時点で、データベースに対して SQL コマンドが実行され、オブジェクトが実体化されます。</span><span class="sxs-lookup"><span data-stu-id="dce20-180">When you begin the `For Each` iteration, a SQL command is executed against the database and objects are materialized.</span></span>

### <a name="to-execute-the-query"></a><span data-ttu-id="dce20-181">クエリを実行するには</span><span class="sxs-lookup"><span data-stu-id="dce20-181">To execute the query</span></span>

1. <span data-ttu-id="dce20-182">`Sub Main` メソッドの末尾 (クエリ指定の後) に次のコードを入力または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="dce20-182">Type or paste the following code at the end of the `Sub Main` method (after the query description):</span></span>

     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]

2. <span data-ttu-id="dce20-183">F5 キーを押してアプリケーションをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="dce20-183">Press F5 to debug the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="dce20-184">アプリケーションで実行時エラーが発生した場合は、「[チュートリアルによる学習](learning-by-walkthroughs.md)」のトラブルシューティングのセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dce20-184">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

     <span data-ttu-id="dce20-185">メッセージ ボックスには 6 人の顧客の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dce20-185">The message box displays a list of six customers.</span></span> <span data-ttu-id="dce20-186">コンソール ウィンドウには生成された SQL コードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dce20-186">The Console window displays the generated SQL code.</span></span>

3. <span data-ttu-id="dce20-187">**[OK]** をクリックしてメッセージ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="dce20-187">Click **OK** to dismiss the message box.</span></span>

     <span data-ttu-id="dce20-188">アプリケーションが終了します。</span><span class="sxs-lookup"><span data-stu-id="dce20-188">The application closes.</span></span>

4. <span data-ttu-id="dce20-189">**[ファイル]** メニューの **[すべてを保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dce20-189">On the **File** menu, click **Save All**.</span></span>

     <span data-ttu-id="dce20-190">引き続き次のチュートリアルに進む場合は、このアプリケーションが必要になります。</span><span class="sxs-lookup"><span data-stu-id="dce20-190">You will need this application if you continue with the next walkthrough.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dce20-191">次の手順</span><span class="sxs-lookup"><span data-stu-id="dce20-191">Next Steps</span></span>

<span data-ttu-id="dce20-192">「[チュートリアル: リレーションシップ間でクエリを実行する (Visual Basic)](walkthrough-querying-across-relationships-visual-basic.md)」トピックは、このチュートリアルの終了位置から続行します。</span><span class="sxs-lookup"><span data-stu-id="dce20-192">The [Walkthrough: Querying Across Relationships (Visual Basic)](walkthrough-querying-across-relationships-visual-basic.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="dce20-193">「リレーションシップ間でクエリを実行する」のチュートリアルでは、リレーショナル データベースの "*結合*" と同じように、複数のテーブルにまたがったクエリを [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="dce20-193">The Querying Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>

<span data-ttu-id="dce20-194">「リレーションシップ間でクエリを実行する」のチュートリアルに進む場合は、必要条件として、ここで完了したチュートリアルのソリューションを保存しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="dce20-194">If you want to do the Querying Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>

## <a name="see-also"></a><span data-ttu-id="dce20-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="dce20-195">See also</span></span>

- [<span data-ttu-id="dce20-196">チュートリアルによる学習</span><span class="sxs-lookup"><span data-stu-id="dce20-196">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)

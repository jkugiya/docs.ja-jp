---
title: SqlMetal.exe (コード生成ツール)
description: SqlMetal.exe (コード生成ツール) について理解します。 このツールを使用して、.NET の LINQ to SQL コンポーネント用のコードとマッピングを生成します。
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: b3d52e5ce070f1a86554a2c8b8cd581b2e4bc685
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258765"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="15773-104">SqlMetal.exe (コード生成ツール)</span><span class="sxs-lookup"><span data-stu-id="15773-104">SqlMetal.exe (Code Generation Tool)</span></span>

<span data-ttu-id="15773-105">SqlMetal コマンドライン ツールは、.NET Framework の [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] コンポーネント用のコードとマッピングを生成します。</span><span class="sxs-lookup"><span data-stu-id="15773-105">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="15773-106">このトピックで後述するオプションを適用することにより、次のようなアクションを SqlMetal で実行できます。</span><span class="sxs-lookup"><span data-stu-id="15773-106">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="15773-107">データベースから、ソース コードとマッピング属性またはマッピング ファイルを生成する。</span><span class="sxs-lookup"><span data-stu-id="15773-107">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="15773-108">データベースから、カスタマイズ用の中間的なデータベース マークアップ言語 (.dbml) ファイルを生成する。</span><span class="sxs-lookup"><span data-stu-id="15773-108">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="15773-109">.dbml ファイルから、コードとマッピング属性またはマッピング ファイルを生成する。</span><span class="sxs-lookup"><span data-stu-id="15773-109">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
<span data-ttu-id="15773-110">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="15773-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="15773-111">既定では、このファイルは `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin にあります。</span><span class="sxs-lookup"><span data-stu-id="15773-111">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="15773-112">Visual Studio をインストールしない場合は、 [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225)をダウンロードすることによって SQLMetal ファイルを入手することもできます。</span><span class="sxs-lookup"><span data-stu-id="15773-112">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15773-113">Visual Studio を使用する開発者は、オブジェクト リレーショナル デザイナーを使用してエンティティ クラスを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="15773-113">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="15773-114">コマンド ライン方式は、大きなデータベースにも適切に対応できます。</span><span class="sxs-lookup"><span data-stu-id="15773-114">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="15773-115">SqlMetal はコマンド ライン ツールであるため、ビルド プロセスでこれを使用できます。</span><span class="sxs-lookup"><span data-stu-id="15773-115">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
<span data-ttu-id="15773-116">ツールを実行するには、[開発者向けのコマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)を使用します。</span><span class="sxs-lookup"><span data-stu-id="15773-116">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span> <span data-ttu-id="15773-117">コマンド プロンプトで、次のコマンドを入力します:</span><span class="sxs-lookup"><span data-stu-id="15773-117">At the command prompt, enter the following command:</span></span>

```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="15773-118">Options</span><span class="sxs-lookup"><span data-stu-id="15773-118">Options</span></span>  

 <span data-ttu-id="15773-119">最新のオプションの一覧を確認するには、コマンド プロンプトでインストール場所に移動し、「 `sqlmetal /?` 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="15773-119">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="15773-120">**接続オプション**</span><span class="sxs-lookup"><span data-stu-id="15773-120">**Connection Options**</span></span>  
  
|<span data-ttu-id="15773-121">オプション</span><span class="sxs-lookup"><span data-stu-id="15773-121">Option</span></span>|<span data-ttu-id="15773-122">説明</span><span class="sxs-lookup"><span data-stu-id="15773-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="15773-123">**/server:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="15773-123">**/server:** *\<name>*</span></span>|<span data-ttu-id="15773-124">データベース サーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="15773-124">Specifies database server name.</span></span>|  
|<span data-ttu-id="15773-125">**/database:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="15773-125">**/database:** *\<name>*</span></span>|<span data-ttu-id="15773-126">サーバー上のデータベース カタログを指定します。</span><span class="sxs-lookup"><span data-stu-id="15773-126">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="15773-127">**/user:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="15773-127">**/user:** *\<name>*</span></span>|<span data-ttu-id="15773-128">ログオン ユーザー ID を指定します。既定値:Windows 認証の使用。</span><span class="sxs-lookup"><span data-stu-id="15773-128">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="15773-129">**/password:** *\<password>*</span><span class="sxs-lookup"><span data-stu-id="15773-129">**/password:** *\<password>*</span></span>|<span data-ttu-id="15773-130">ログオン パスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="15773-130">Specifies logon password.</span></span> <span data-ttu-id="15773-131">既定値:Windows 認証の使用。</span><span class="sxs-lookup"><span data-stu-id="15773-131">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="15773-132">**/conn:** *\<connection string>*</span><span class="sxs-lookup"><span data-stu-id="15773-132">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="15773-133">データベース接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="15773-133">Specifies database connection string.</span></span> <span data-ttu-id="15773-134">**/server**、 **/database**、 **/user**、または **/password** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="15773-134">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="15773-135">接続文字列にファイル名は含めないでください。</span><span class="sxs-lookup"><span data-stu-id="15773-135">Do not include the file name in the connection string.</span></span> <span data-ttu-id="15773-136">代わりに、コマンド ラインにファイル名を入力ファイルとして追加します。</span><span class="sxs-lookup"><span data-stu-id="15773-136">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="15773-137">たとえば、 **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"** というコマンド ラインは、入力ファイルとして "c:\northwnd.mdf" を指定します。</span><span class="sxs-lookup"><span data-stu-id="15773-137">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="15773-138">**/timeout:** *\<seconds>*</span><span class="sxs-lookup"><span data-stu-id="15773-138">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="15773-139">SqlMetal がデータベースにアクセスする際のタイムアウト値を指定します。</span><span class="sxs-lookup"><span data-stu-id="15773-139">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="15773-140">既定値:0 (時間制限なし)。</span><span class="sxs-lookup"><span data-stu-id="15773-140">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="15773-141">**抽出オプション**</span><span class="sxs-lookup"><span data-stu-id="15773-141">**Extraction options**</span></span>  
  
|<span data-ttu-id="15773-142">オプション</span><span class="sxs-lookup"><span data-stu-id="15773-142">Option</span></span>|<span data-ttu-id="15773-143">説明</span><span class="sxs-lookup"><span data-stu-id="15773-143">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="15773-144">**/views**</span><span class="sxs-lookup"><span data-stu-id="15773-144">**/views**</span></span>|<span data-ttu-id="15773-145">データベース ビューを抽出します。</span><span class="sxs-lookup"><span data-stu-id="15773-145">Extracts database views.</span></span>|  
|<span data-ttu-id="15773-146">**/functions**</span><span class="sxs-lookup"><span data-stu-id="15773-146">**/functions**</span></span>|<span data-ttu-id="15773-147">データベース関数を抽出します。</span><span class="sxs-lookup"><span data-stu-id="15773-147">Extracts database functions.</span></span>|  
|<span data-ttu-id="15773-148">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="15773-148">**/sprocs**</span></span>|<span data-ttu-id="15773-149">ストアド プロシージャを抽出します。</span><span class="sxs-lookup"><span data-stu-id="15773-149">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="15773-150">**出力オプション**</span><span class="sxs-lookup"><span data-stu-id="15773-150">**Output options**</span></span>  
  
|<span data-ttu-id="15773-151">オプション</span><span class="sxs-lookup"><span data-stu-id="15773-151">Option</span></span>|<span data-ttu-id="15773-152">説明</span><span class="sxs-lookup"><span data-stu-id="15773-152">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="15773-153">**/dbml** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="15773-153">**/dbml** *[:file]*</span></span>|<span data-ttu-id="15773-154">出力を .dbml として送ります。</span><span class="sxs-lookup"><span data-stu-id="15773-154">Sends output as .dbml.</span></span> <span data-ttu-id="15773-155">**/map** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="15773-155">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="15773-156">**/code** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="15773-156">**/code** *[:file]*</span></span>|<span data-ttu-id="15773-157">出力をソース コードとして送ります。</span><span class="sxs-lookup"><span data-stu-id="15773-157">Sends output as source code.</span></span> <span data-ttu-id="15773-158">**/dbml** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="15773-158">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="15773-159">**/map** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="15773-159">**/map** *[:file]*</span></span>|<span data-ttu-id="15773-160">属性ではなく XML マッピング ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="15773-160">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="15773-161">**/dbml** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="15773-161">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="15773-162">**その他**</span><span class="sxs-lookup"><span data-stu-id="15773-162">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="15773-163">オプション</span><span class="sxs-lookup"><span data-stu-id="15773-163">Option</span></span>|<span data-ttu-id="15773-164">説明</span><span class="sxs-lookup"><span data-stu-id="15773-164">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="15773-165">**/language:** *\<language>*</span><span class="sxs-lookup"><span data-stu-id="15773-165">**/language:** *\<language>*</span></span>|<span data-ttu-id="15773-166">ソース コードの言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="15773-166">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="15773-167">有効な *\<language>* : vb、csharp。</span><span class="sxs-lookup"><span data-stu-id="15773-167">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="15773-168">既定値:コード ファイル名の拡張子から派生します。</span><span class="sxs-lookup"><span data-stu-id="15773-168">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="15773-169">**/namespace:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="15773-169">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="15773-170">生成されるコードの名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="15773-170">Specifies namespace of the generated code.</span></span> <span data-ttu-id="15773-171">既定値は、名前空間なしです。</span><span class="sxs-lookup"><span data-stu-id="15773-171">Default value: no namespace.</span></span>|  
|<span data-ttu-id="15773-172">**/context:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="15773-172">**/context:** *\<type>*</span></span>|<span data-ttu-id="15773-173">データ コンテキスト クラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="15773-173">Specifies name of data context class.</span></span> <span data-ttu-id="15773-174">既定値:データベース名から派生します。</span><span class="sxs-lookup"><span data-stu-id="15773-174">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="15773-175">**/entitybase:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="15773-175">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="15773-176">生成されるコード内のエンティティ クラスの基本クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="15773-176">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="15773-177">既定値:エンティティの基本クラスなしです。</span><span class="sxs-lookup"><span data-stu-id="15773-177">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="15773-178">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="15773-178">**/pluralize**</span></span>|<span data-ttu-id="15773-179">クラスとメンバーの名前を自動的に複数化または単数化します。</span><span class="sxs-lookup"><span data-stu-id="15773-179">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="15773-180">このオプションは、米国英語バージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="15773-180">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="15773-181">**/serialization:** *\<option>*</span><span class="sxs-lookup"><span data-stu-id="15773-181">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="15773-182">シリアル化可能なクラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="15773-182">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="15773-183">有効な *\<option>* :None と Unidirectional。</span><span class="sxs-lookup"><span data-stu-id="15773-183">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="15773-184">既定値:なし。</span><span class="sxs-lookup"><span data-stu-id="15773-184">Default value: None.</span></span><br /><br /> <span data-ttu-id="15773-185">詳細については、「[Serialization](../data/adonet/sql/linq/serialization.md)」 (シリアル化) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15773-185">For more information, see [Serialization](../data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="15773-186">**入力ファイル**</span><span class="sxs-lookup"><span data-stu-id="15773-186">**Input File**</span></span>  
  
|<span data-ttu-id="15773-187">オプション</span><span class="sxs-lookup"><span data-stu-id="15773-187">Option</span></span>|<span data-ttu-id="15773-188">説明</span><span class="sxs-lookup"><span data-stu-id="15773-188">Description</span></span>|  
|------------|-----------------|  
|**\<input file>**|<span data-ttu-id="15773-189">SQL Server Express .mdf ファイル、SQL Server Compact 3.5 .sdf ファイル、または .dbml 中間ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="15773-189">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15773-190">Remarks</span><span class="sxs-lookup"><span data-stu-id="15773-190">Remarks</span></span>  

 <span data-ttu-id="15773-191">SqlMetal の実際の機能には、次の 2 つの段階が含まれています。</span><span class="sxs-lookup"><span data-stu-id="15773-191">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="15773-192">データベースのメタデータを .dbml ファイルに抽出する。</span><span class="sxs-lookup"><span data-stu-id="15773-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="15773-193">コード出力ファイルを生成する。</span><span class="sxs-lookup"><span data-stu-id="15773-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="15773-194">適切なコマンド ライン オプションを使用することで、Visual Basic または C# ソース コードを生成するか、XML マッピング ファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="15773-194">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="15773-195">メタデータを .mdf ファイルから抽出するには、他のすべてのオプションの後に .mdf ファイルの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15773-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="15773-196">**/server** を指定しない場合、 **localhost/sqlexpress** と見なされます。</span><span class="sxs-lookup"><span data-stu-id="15773-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="15773-197">Microsoft SQL Server 2005 は、次の条件が少なくとも 1 つ満たされる場合に例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="15773-197">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="15773-198">自身を呼び出すストアド プロシージャを SqlMetal が抽出しようとした。</span><span class="sxs-lookup"><span data-stu-id="15773-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="15773-199">ストアド プロシージャ、関数、またはビューの入れ子レベルが 32 を超える。</span><span class="sxs-lookup"><span data-stu-id="15773-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="15773-200">SqlMetal はこの例外をキャッチして、それを警告として報告します。</span><span class="sxs-lookup"><span data-stu-id="15773-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="15773-201">入力ファイル名を指定するには、その名前をコマンド ラインに入力ファイルとして追加します。</span><span class="sxs-lookup"><span data-stu-id="15773-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="15773-202">( **/conn** オプションを使用して) 接続文字列にファイル名を含める操作は、サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="15773-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="15773-203">使用例</span><span class="sxs-lookup"><span data-stu-id="15773-203">Examples</span></span>  

 <span data-ttu-id="15773-204">抽出された SQL メタデータを格納する .dbml ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="15773-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="15773-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="15773-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="15773-206">SQL Server Express を使用して .mdf ファイルから抽出された SQL メタデータを格納する .dbml ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="15773-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="15773-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="15773-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="15773-208">SQL Server Express から抽出された SQL メタデータを格納する .dbml ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="15773-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="15773-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="15773-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="15773-210">.dbml メタデータ ファイルからソース コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="15773-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="15773-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="15773-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="15773-212">SQL メタデータからソース コードを直接生成します。</span><span class="sxs-lookup"><span data-stu-id="15773-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="15773-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="15773-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15773-214">サンプル データベース Northwind で **/pluralize** オプションを使用する場合には、注意を必要とする動作があります。</span><span class="sxs-lookup"><span data-stu-id="15773-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="15773-215">SqlMetal がテーブルのために行型の名前を生成するとき、テーブル名は単数形です。</span><span class="sxs-lookup"><span data-stu-id="15773-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="15773-216">テーブルに関する <xref:System.Data.Linq.DataContext> プロパティを生成するときには、テーブル名は複数形です。</span><span class="sxs-lookup"><span data-stu-id="15773-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="15773-217">偶然にも、サンプル データベース Northwind 内のテーブルには既に複数形が使われています。</span><span class="sxs-lookup"><span data-stu-id="15773-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="15773-218">このため、この部分はうまく機能しません。</span><span class="sxs-lookup"><span data-stu-id="15773-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="15773-219">データベース テーブルの名前は単数形にするのが一般的ですが、.NET では、コレクションの名前を複数形にすることも一般的です。</span><span class="sxs-lookup"><span data-stu-id="15773-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15773-220">関連項目</span><span class="sxs-lookup"><span data-stu-id="15773-220">See also</span></span>

- [<span data-ttu-id="15773-221">方法: Visual Basic または C# でオブジェクト モデルを生成する</span><span class="sxs-lookup"><span data-stu-id="15773-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="15773-222">LINQ to SQL でのコード生成</span><span class="sxs-lookup"><span data-stu-id="15773-222">Code Generation in LINQ to SQL</span></span>](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="15773-223">外部マップ</span><span class="sxs-lookup"><span data-stu-id="15773-223">External Mapping</span></span>](../data/adonet/sql/linq/external-mapping.md)

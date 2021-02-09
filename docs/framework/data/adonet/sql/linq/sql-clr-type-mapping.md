---
description: '詳細情報: SQL と CLR の型マッピング'
title: SQL と CLR の型マッピング
ms.date: 07/23/2018
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
ms.openlocfilehash: 59d3594287ceb20f5c3887c58a0f5527df35218a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803738"
---
# <a name="sql-clr-type-mapping"></a><span data-ttu-id="788ed-103">SQL と CLR の型マッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-103">SQL-CLR Type Mapping</span></span>

<span data-ttu-id="788ed-104">LINQ to SQL では、リレーショナル データベースのデータ モデルが、任意のプログラミング言語で表されるオブジェクト モデルに対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="788ed-104">In LINQ to SQL, the data model of a relational database maps to an object model that is expressed in the programming language of your choice.</span></span> <span data-ttu-id="788ed-105">アプリケーションが実行されると、LINQ to SQL は、オブジェクト モデルの統合言語クエリを SQL に変換し、それをデータベースに送信して実行します。</span><span class="sxs-lookup"><span data-stu-id="788ed-105">When the application runs, LINQ to SQL translates the language-integrated queries in the object model into SQL and sends them to the database for execution.</span></span> <span data-ttu-id="788ed-106">データベースから結果が返されると、LINQ to SQL はその結果をプログラミング言語で操作できるオブジェクトに変換し直します。</span><span class="sxs-lookup"><span data-stu-id="788ed-106">When the database returns the results, LINQ to SQL translates the results back to objects that you can work with in your own programming language.</span></span>  
  
 <span data-ttu-id="788ed-107">オブジェクト モデルとデータベースの間でデータを変換するには、"*型マッピング*" を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="788ed-107">In order to translate data between the object model and the database, a *type mapping* must be defined.</span></span> <span data-ttu-id="788ed-108">LINQ to SQL は型マッピングを使用して、共通言語ランタイム (CLR) のそれぞれの型を SQL Server の特定の型に対応付けます。</span><span class="sxs-lookup"><span data-stu-id="788ed-108">LINQ to SQL uses a type mapping to match each common language runtime (CLR) type with a particular SQL Server type.</span></span> <span data-ttu-id="788ed-109">型マッピングおよびその他のマッピング情報 (データベース構造やテーブルのリレーションシップなど) は、オブジェクト モデル内で属性ベースの対応付けを使用して定義できます。</span><span class="sxs-lookup"><span data-stu-id="788ed-109">You can define type mappings and other mapping information, such as database structure and table relationships, inside the object model with attribute-based mapping.</span></span> <span data-ttu-id="788ed-110">また、オブジェクト モデルの外部で外部マッピング ファイルを使用して指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="788ed-110">Alternatively, you can specify the mapping information outside the object model with an external mapping file.</span></span> <span data-ttu-id="788ed-111">詳しくは、「[属性ベースの対応付け](attribute-based-mapping.md)」および「[外部マップ](external-mapping.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="788ed-111">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md) and [External Mapping](external-mapping.md).</span></span>  
  
 <span data-ttu-id="788ed-112">このトピックでは、以下の点について説明します。</span><span class="sxs-lookup"><span data-stu-id="788ed-112">This topic discusses the following points:</span></span>  
  
- [<span data-ttu-id="788ed-113">既定の型マッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-113">Default Type Mapping</span></span>](#DefaultTypeMapping)  
  
- [<span data-ttu-id="788ed-114">型マッピングと実行時動作の関係</span><span class="sxs-lookup"><span data-stu-id="788ed-114">Type Mapping Run-time Behavior Matrix</span></span>](#BehaviorMatrix)  
  
- [<span data-ttu-id="788ed-115">CLR と SQL の実行時の動作の違い</span><span class="sxs-lookup"><span data-stu-id="788ed-115">Behavior Differences Between CLR and SQL Execution</span></span>](#BehaviorDiffs)  
  
- [<span data-ttu-id="788ed-116">Enum 型のマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-116">Enum Mapping</span></span>](#EnumMapping)  
  
- [<span data-ttu-id="788ed-117">数値のマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-117">Numeric Mapping</span></span>](#NumericMapping)  
  
- [<span data-ttu-id="788ed-118">テキストおよび XML のマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-118">Text and XML Mapping</span></span>](#TextMapping)  
  
- [<span data-ttu-id="788ed-119">日付および時刻のマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-119">Date and Time Mapping</span></span>](#DateMapping)  
  
- [<span data-ttu-id="788ed-120">バイナリのマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-120">Binary Mapping</span></span>](#BinaryMapping)  
  
- [<span data-ttu-id="788ed-121">その他のマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-121">Miscellaneous Mapping</span></span>](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>

## <a name="default-type-mapping"></a><span data-ttu-id="788ed-122">既定の型マッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-122">Default Type Mapping</span></span>  

 <span data-ttu-id="788ed-123">オブジェクト モデルまたは外部マッピング ファイルは、オブジェクト リレーショナル デザイナー (O/R デザイナー) または SQLMetal コマンド ライン ツールを使用して自動的に作成できます。</span><span class="sxs-lookup"><span data-stu-id="788ed-123">You can create the object model or external mapping file automatically with the Object Relational Designer (O/R Designer) or the SQLMetal command-line tool.</span></span> <span data-ttu-id="788ed-124">これらのツールの既定の型マッピングでは、SQL Server データベース内の列にマップするためにどの CLR 型を選択するかが定義されています。</span><span class="sxs-lookup"><span data-stu-id="788ed-124">The default type mappings for these tools define which CLR types are chosen to map to columns inside the SQL Server database.</span></span> <span data-ttu-id="788ed-125">これらのツールの使用方法の詳細については、「[オブジェクト モデルの作成](creating-the-object-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-125">For more information about using these tools, see [Creating the Object Model](creating-the-object-model.md).</span></span>  
  
 <span data-ttu-id="788ed-126">また、<xref:System.Data.Linq.DataContext.CreateDatabase%2A> メソッドを使用して、オブジェクト モデルまたは外部マッピング ファイルのマッピング情報に基づいて SQL Server データベースを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="788ed-126">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A> method to create a SQL Server database based on the mapping information in the object model or external mapping file.</span></span> <span data-ttu-id="788ed-127"><xref:System.Data.Linq.DataContext.CreateDatabase%2A> メソッドの既定の型マッピングでは、オブジェクト モデル内の CLR 型にマップするためにどの型の SQL Server 列を作成するかが定義されています。</span><span class="sxs-lookup"><span data-stu-id="788ed-127">The default type mappings for the <xref:System.Data.Linq.DataContext.CreateDatabase%2A> method define which type of SQL Server columns are created to map to the CLR types in the object model.</span></span> <span data-ttu-id="788ed-128">詳細については、[データベースを動的に作成する](how-to-dynamically-create-a-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-128">For more information, see [How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md).</span></span>  
  
<a name="BehaviorMatrix"></a>

## <a name="type-mapping-run-time-behavior-matrix"></a><span data-ttu-id="788ed-129">型マッピングと実行時動作の関係</span><span class="sxs-lookup"><span data-stu-id="788ed-129">Type Mapping Run-time Behavior Matrix</span></span>  

 <span data-ttu-id="788ed-130">次の図は、データがデータベースから取得されるときやデータベースに保存されるときに、特定の型マッピングで行われる実行時の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="788ed-130">The following diagram shows the expected run-time behavior of specific type mappings when data is retrieved from or saved to the database.</span></span> <span data-ttu-id="788ed-131">シリアル化を除き、LINQ to SQL では、このマトリックスに指定されていない CLR または SQL Server のデータ型のマッピングはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="788ed-131">With the exception of serialization, LINQ to SQL does not support mapping between any CLR or SQL Server data types that are not specified in this matrix.</span></span> <span data-ttu-id="788ed-132">シリアル化のサポートの詳細については、「[バイナリ シリアル化](#BinarySerialization)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-132">For more information on serialization support, see [Binary Serialization](#BinarySerialization).</span></span>  

![SQL Server と SQL CLR のデータ型マッピング テーブル](./media/sql-clr-type-mapping.png)

> [!NOTE]
> <span data-ttu-id="788ed-134">一部の型マッピングでは、データベースに対する変換操作中にオーバーフローやデータ損失の例外が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="788ed-134">Some type mappings may result in overflow or data loss exceptions while translating to or from the database.</span></span>  
  
### <a name="custom-type-mapping"></a><span data-ttu-id="788ed-135">カスタム型マッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-135">Custom Type Mapping</span></span>  

 <span data-ttu-id="788ed-136">LINQ to SQL では、O/R デザイナー、SQLMetal、および <xref:System.Data.Linq.DataContext.CreateDatabase%2A> メソッドで使用される既定の型マッピング以外も使用できます。</span><span class="sxs-lookup"><span data-stu-id="788ed-136">With LINQ to SQL, you are not limited to the default type mappings used by the O/R Designer, SQLMetal, and the <xref:System.Data.Linq.DataContext.CreateDatabase%2A> method.</span></span> <span data-ttu-id="788ed-137">DBML ファイルで明示的に指定すると、カスタム型マッピングを作成できます。</span><span class="sxs-lookup"><span data-stu-id="788ed-137">You can create custom type mappings by explicitly specifying them in a DBML file.</span></span> <span data-ttu-id="788ed-138">次に、その DBML ファイルを使用してオブジェクト モデル コードとマッピング ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="788ed-138">Then you can use that DBML file to create the object model code and mapping file.</span></span> <span data-ttu-id="788ed-139">詳細については、「[SQL と CLR のカスタム型マッピング](sql-clr-custom-type-mappings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-139">For more information, see [SQL-CLR Custom Type Mappings](sql-clr-custom-type-mappings.md).</span></span>  
  
<a name="BehaviorDiffs"></a>

## <a name="behavior-differences-between-clr-and-sql-execution"></a><span data-ttu-id="788ed-140">CLR と SQL の実行時の動作の違い</span><span class="sxs-lookup"><span data-stu-id="788ed-140">Behavior Differences Between CLR and SQL Execution</span></span>  

 <span data-ttu-id="788ed-141">CLR と SQL Server では有効桁数や実行方法が異なるため、計算を実行する場所によって、得られる結果や動作が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="788ed-141">Because of differences in precision and execution between the CLR and SQL Server, you may receive different results or experience different behavior depending on where you perform your calculations.</span></span> <span data-ttu-id="788ed-142">LINQ to SQL クエリで実行される計算は、実際は Transact-SQL に変換されてから SQL Server データベースで実行されます。</span><span class="sxs-lookup"><span data-stu-id="788ed-142">Calculations performed in LINQ to SQL queries are actually translated to Transact-SQL and then executed on the SQL Server database.</span></span> <span data-ttu-id="788ed-143">LINQ to SQL クエリの外部で実行される計算は、CLR のコンテキスト内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="788ed-143">Calculations performed outside LINQ to SQL queries are executed within the context of the CLR.</span></span>  
  
 <span data-ttu-id="788ed-144">CLR および SQL Server 間での動作の違いの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="788ed-144">For example, the following are some differences in behavior between the CLR and SQL Server:</span></span>  
  
- <span data-ttu-id="788ed-145">SQL Server では、一部のデータ型が、CLR の対応する型のデータとは異なる順序で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="788ed-145">SQL Server orders some data types differently than data of equivalent type in the CLR.</span></span> <span data-ttu-id="788ed-146">たとえば、SQL Server の `UNIQUEIDENTIFIER` 型のデータは、CLR の <xref:System.Guid?displayProperty=nameWithType> 型のデータとは異なる順序で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="788ed-146">For example, SQL Server data of type `UNIQUEIDENTIFIER` is ordered differently than CLR data of type <xref:System.Guid?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="788ed-147">SQL Server では、一部の文字列比較操作の処理が CLR とは異なります。</span><span class="sxs-lookup"><span data-stu-id="788ed-147">SQL Server handles some string comparison operations differently than the CLR.</span></span> <span data-ttu-id="788ed-148">SQL Server での文字列比較の動作は、サーバー上の照合順序の設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="788ed-148">In SQL Server, string comparison behavior depends on the collation settings on the server.</span></span> <span data-ttu-id="788ed-149">詳細については、Microsoft SQL Server オンライン ブックの「[照合順序の使用](/previous-versions/sql/sql-server-2008-r2/ms187582(v=sql.105))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-149">For more information, see [Working with Collations](/previous-versions/sql/sql-server-2008-r2/ms187582(v=sql.105)) in the Microsoft SQL Server Books Online.</span></span>  
  
- <span data-ttu-id="788ed-150">SQL Server では、マップされている一部の関数で、CLR とは異なる値が返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="788ed-150">SQL Server may return different values for some mapped functions than the CLR.</span></span> <span data-ttu-id="788ed-151">たとえば、末尾の空白文字のみが異なる 2 つの文字列を等価関数で比較した場合、SQL Server では等しいと見なされるのに対し、CLR では等しくないと見なされます。</span><span class="sxs-lookup"><span data-stu-id="788ed-151">For example, equality functions will differ because SQL Server considers two strings to be equal if they only differ in trailing white space; whereas the CLR considers them to be not equal.</span></span>  
  
<a name="EnumMapping"></a>

## <a name="enum-mapping"></a><span data-ttu-id="788ed-152">Enum 型のマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-152">Enum Mapping</span></span>  

 <span data-ttu-id="788ed-153">LINQ to SQL では、CLR の <xref:System.Enum?displayProperty=nameWithType> 型の SQL Server 型へのマッピングが 2 種類サポートされています。</span><span class="sxs-lookup"><span data-stu-id="788ed-153">LINQ to SQL supports mapping the CLR <xref:System.Enum?displayProperty=nameWithType> type to SQL Server types in two ways:</span></span>  
  
- <span data-ttu-id="788ed-154">SQL 数値型 (`TINYINT`、`SMALLINT`、`INT`、`BIGINT`) へのマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-154">Mapping to SQL numeric types (`TINYINT`, `SMALLINT`, `INT`, `BIGINT`)</span></span>  
  
     <span data-ttu-id="788ed-155">CLR <xref:System.Enum?displayProperty=nameWithType> 型を SQL 数値型にマップすると、基になる CLR <xref:System.Enum?displayProperty=nameWithType> の整数値は SQL Server データベース列の値にマップされます。</span><span class="sxs-lookup"><span data-stu-id="788ed-155">When you map a CLR <xref:System.Enum?displayProperty=nameWithType> type to a SQL numeric type, you map the underlying integer value of the CLR <xref:System.Enum?displayProperty=nameWithType> to the value of the SQL Server database column.</span></span> <span data-ttu-id="788ed-156">たとえば、<xref:System.Enum?displayProperty=nameWithType> という名前の `DaysOfWeek` に、基になる整数値が 3 である `Tue` という名前のメンバーが含まれる場合、そのメンバーはデータベース値 3 にマップされます。</span><span class="sxs-lookup"><span data-stu-id="788ed-156">For example, if a <xref:System.Enum?displayProperty=nameWithType> named `DaysOfWeek` contains a member named `Tue` with an underlying integer value of 3, that member maps to a database value of 3.</span></span>  
  
- <span data-ttu-id="788ed-157">SQL テキスト型 (`CHAR`、`NCHAR`、`VARCHAR`、`NVARCHAR`) へのマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-157">Mapping to SQL text types (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`)</span></span>  
  
     <span data-ttu-id="788ed-158">CLR <xref:System.Enum?displayProperty=nameWithType> 型を SQL テキスト型にマップすると、CLR <xref:System.Enum?displayProperty=nameWithType> のメンバーの名前に SQL データベース値がマップされます。</span><span class="sxs-lookup"><span data-stu-id="788ed-158">When you map a CLR <xref:System.Enum?displayProperty=nameWithType> type to a SQL text type, the SQL database value is mapped to the names of the CLR <xref:System.Enum?displayProperty=nameWithType> members.</span></span> <span data-ttu-id="788ed-159">たとえば、<xref:System.Enum?displayProperty=nameWithType> という名前の `DaysOfWeek` に、基になる整数値が 3 である `Tue` という名前のメンバーが含まれる場合、このメンバーはデータベース値 `Tue` にマップされます。</span><span class="sxs-lookup"><span data-stu-id="788ed-159">For example, if a <xref:System.Enum?displayProperty=nameWithType> named `DaysOfWeek` contains a member named `Tue` with an underlying integer value of 3, that member maps to a database value of `Tue`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="788ed-160">SQL のテキスト型を CLR の <xref:System.Enum?displayProperty=nameWithType> にマップする場合は、マップされる SQL 列に <xref:System.Enum> メンバーの名前のみを含めてください。</span><span class="sxs-lookup"><span data-stu-id="788ed-160">When mapping SQL text types to a CLR <xref:System.Enum?displayProperty=nameWithType>, include only the names of the <xref:System.Enum> members in the mapped SQL column.</span></span> <span data-ttu-id="788ed-161"><xref:System.Enum> 型にマップされる SQL 列では、他の値はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="788ed-161">Other values are not supported in the <xref:System.Enum>-mapped SQL column.</span></span>  
  
 <span data-ttu-id="788ed-162">O/R デザイナーと SQLMetal コマンド ライン ツールでは、SQL の型から CLR の <xref:System.Enum> クラスへの自動的なマッピングはできません。</span><span class="sxs-lookup"><span data-stu-id="788ed-162">The O/R Designer and SQLMetal command-line tool cannot automatically map a SQL type to a CLR <xref:System.Enum> class.</span></span> <span data-ttu-id="788ed-163">DBML ファイルを O/R デザイナーと SQLMetal で使用できるようにカスタマイズして、このマッピングを明示的に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="788ed-163">You must explicitly configure this mapping by customizing a DBML file for use by the O/R Designer and SQLMetal.</span></span> <span data-ttu-id="788ed-164">カスタム型マッピングの詳細については、「[SQL と CLR のカスタム型マッピング](sql-clr-custom-type-mappings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-164">For more information about custom type mapping, see [SQL-CLR Custom Type Mappings](sql-clr-custom-type-mappings.md).</span></span>  
  
 <span data-ttu-id="788ed-165">列挙を目的とする SQL の列は、他の数値やテキストの列と型が同じであるため、これらのツールはユーザーの意図を認識できず、次の「[数値のマッピング](#NumericMapping)」と「[テキストおよび XML のマッピング](#TextMapping)」のセクションで説明するように既定のマッピングを使用します。</span><span class="sxs-lookup"><span data-stu-id="788ed-165">Because a SQL column intended for enumeration will be of the same type as other numeric and text columns; these tools will not recognize your intent and default to mapping as described in the following [Numeric Mapping](#NumericMapping) and [Text and XML Mapping](#TextMapping) sections.</span></span> <span data-ttu-id="788ed-166">DBML ファイルを使用したコード生成の詳細については、「[LINQ to SQL でのコード生成](code-generation-in-linq-to-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-166">For more information about generating code with the DBML file, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="788ed-167"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> メソッドでは、CLR の <xref:System.Enum?displayProperty=nameWithType> 型をマップするために数値型の SQL 列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="788ed-167">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a SQL column of numeric type to map a CLR <xref:System.Enum?displayProperty=nameWithType> type.</span></span>  
  
<a name="NumericMapping"></a>

## <a name="numeric-mapping"></a><span data-ttu-id="788ed-168">数値のマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-168">Numeric Mapping</span></span>  

 <span data-ttu-id="788ed-169">LINQ to SQL では、CLR と SQL Server のさまざまな数値型をマップできます。</span><span class="sxs-lookup"><span data-stu-id="788ed-169">LINQ to SQL lets you map many CLR and SQL Server numeric types.</span></span> <span data-ttu-id="788ed-170">次の表に、O/R デザイナーおよび SQLMetal でデータベースに基づいてオブジェクト モデルまたは外部マッピング ファイルを作成するときに選択される CLR 型を示します。</span><span class="sxs-lookup"><span data-stu-id="788ed-170">The following table shows the CLR types that O/R Designer and SQLMetal select when building an object model or external mapping file based on your database.</span></span>  
  
|<span data-ttu-id="788ed-171">SQL Server 型</span><span class="sxs-lookup"><span data-stu-id="788ed-171">SQL Server Type</span></span>|<span data-ttu-id="788ed-172">O/R デザイナーおよび SQLMetal で使用される既定の CLR 型マッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-172">Default CLR Type mapping used by O/R Designer and SQLMetal</span></span>|  
|---------------------|-----------------------------------------------------------------|  
|`BIT`|<xref:System.Boolean?displayProperty=nameWithType>|  
|`TINYINT`|<xref:System.Int16?displayProperty=nameWithType>|  
|`INT`|<xref:System.Int32?displayProperty=nameWithType>|  
|`BIGINT`|<xref:System.Int64?displayProperty=nameWithType>|  
|`SMALLMONEY`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`MONEY`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`DECIMAL`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`NUMERIC`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`REAL/FLOAT(24)`|<xref:System.Single?displayProperty=nameWithType>|  
|`FLOAT/FLOAT(53)`|<xref:System.Double?displayProperty=nameWithType>|  
  
 <span data-ttu-id="788ed-173">次の表に、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> メソッドで使用される既定の型マッピングを示します。既定の型マッピングでは、オブジェクト モデルまたは外部マッピング ファイルで定義された CLR 型にマップするために作成される SQL 列の型が定義されています。</span><span class="sxs-lookup"><span data-stu-id="788ed-173">The next table shows the default type mappings used by the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method to define which type of SQL columns are created to map to the CLR types defined in your object model or external mapping file.</span></span>  
  
|<span data-ttu-id="788ed-174">CLR 型</span><span class="sxs-lookup"><span data-stu-id="788ed-174">CLR Type</span></span>|<span data-ttu-id="788ed-175"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> で使用される既定の SQL Server 型</span><span class="sxs-lookup"><span data-stu-id="788ed-175">Default SQL Server Type used by <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType></span></span>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|`BIT`|  
|<xref:System.Byte?displayProperty=nameWithType>|`TINYINT`|  
|<xref:System.Int16?displayProperty=nameWithType>|`SMALLINT`|  
|<xref:System.Int32?displayProperty=nameWithType>|`INT`|  
|<xref:System.Int64?displayProperty=nameWithType>|`BIGINT`|  
|<xref:System.SByte?displayProperty=nameWithType>|`SMALLINT`|  
|<xref:System.UInt16?displayProperty=nameWithType>|`INT`|  
|<xref:System.UInt32?displayProperty=nameWithType>|`BIGINT`|  
|<xref:System.UInt64?displayProperty=nameWithType>|`DECIMAL(20)`|  
|<xref:System.Decimal?displayProperty=nameWithType>|`DECIMAL(29,4)`|  
|<xref:System.Single?displayProperty=nameWithType>|`REAL`|  
|<xref:System.Double?displayProperty=nameWithType>|`FLOAT`|  
  
 <span data-ttu-id="788ed-176">これ以外にもさまざまな数値のマッピングを選択できますが、一部のマッピングでは、データベースに対する変換操作中にオーバーフローやデータ損失の例外が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="788ed-176">There are many other numeric mappings you can choose, but some may result in overflow or data loss exceptions while translating to or from the database.</span></span> <span data-ttu-id="788ed-177">詳細については、「[型マッピングと実行時動作の関係](#BehaviorMatrix)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-177">For more information, see the [Type Mapping Run Time Behavior Matrix](#BehaviorMatrix).</span></span>  
  
### <a name="decimal-and-money-types"></a><span data-ttu-id="788ed-178">Decimal 型と Money 型</span><span class="sxs-lookup"><span data-stu-id="788ed-178">Decimal and Money Types</span></span>  

 <span data-ttu-id="788ed-179">SQL Server の `DECIMAL` 型の既定の有効桁数 (小数点の右側と左側で 18 桁) は、対応する既定の型である CLR の <xref:System.Decimal?displayProperty=nameWithType> 型の有効桁数よりはるかに少なくなっています。</span><span class="sxs-lookup"><span data-stu-id="788ed-179">The default precision of SQL Server `DECIMAL` type (18 decimal digits to the left and right of the decimal point) is much smaller than the precision of the CLR <xref:System.Decimal?displayProperty=nameWithType> type that it is paired with by default.</span></span> <span data-ttu-id="788ed-180">その結果、データベースにデータを保存するときに有効桁数が少なくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="788ed-180">This can result in precision loss when you save data to the database.</span></span> <span data-ttu-id="788ed-181">一方、SQL Server の `DECIMAL` 型に 29 桁を超える有効桁数が設定されている場合、その逆が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="788ed-181">However, just the opposite can happen if the SQL Server `DECIMAL` type is configured with greater than 29 digits of precision.</span></span> <span data-ttu-id="788ed-182">SQL Server の `DECIMAL` 型に CLR の <xref:System.Decimal?displayProperty=nameWithType> より大きい有効桁数の値が設定されていると、データベースからデータを取得するときに有効桁数が少なくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="788ed-182">When a SQL Server `DECIMAL` type has been configured with a greater precision than the CLR <xref:System.Decimal?displayProperty=nameWithType>, precision loss can occur when retrieving data from the database.</span></span>  
  
 <span data-ttu-id="788ed-183">SQL Server の `MONEY` 型と `SMALLMONEY` 型も、既定で CLR の <xref:System.Decimal?displayProperty=nameWithType> 型に対応付けられます。これらの型も有効桁数がはるかに少ないため、データベースにデータを保存するときにオーバーフローやデータ損失の例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="788ed-183">The SQL Server `MONEY` and `SMALLMONEY` types, which are also paired with the CLR <xref:System.Decimal?displayProperty=nameWithType> type by default, have a much smaller precision, which can result in overflow or data loss exceptions when saving data to the database.</span></span>  
  
<a name="TextMapping"></a>

## <a name="text-and-xml-mapping"></a><span data-ttu-id="788ed-184">テキストおよび XML のマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-184">Text and XML Mapping</span></span>  

 <span data-ttu-id="788ed-185">さまざまなテキスト ベースの型および XML 型も、LINQ to SQL を使用してマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="788ed-185">There are also many text-based and XML types that you can map with LINQ to SQL.</span></span> <span data-ttu-id="788ed-186">次の表に、O/R デザイナーおよび SQLMetal でデータベースに基づいてオブジェクト モデルまたは外部マッピング ファイルを作成するときに選択される CLR 型を示します。</span><span class="sxs-lookup"><span data-stu-id="788ed-186">The following table shows the CLR types that O/R Designer and SQLMetal select when building an object model or external mapping file based on your database.</span></span>  
  
|<span data-ttu-id="788ed-187">SQL Server 型</span><span class="sxs-lookup"><span data-stu-id="788ed-187">SQL Server Type</span></span>|<span data-ttu-id="788ed-188">O/R デザイナーおよび SQLMetal で使用される既定の CLR 型マッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-188">Default CLR Type mapping used by O/R Designer and SQLMetal</span></span>|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 <span data-ttu-id="788ed-189">次の表に、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> メソッドで使用される既定の型マッピングを示します。既定の型マッピングでは、オブジェクト モデルまたは外部マッピング ファイルで定義された CLR 型にマップするために作成される SQL 列の型が定義されています。</span><span class="sxs-lookup"><span data-stu-id="788ed-189">The next table shows the default type mappings used by the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method to define which type of SQL columns are created to map to the CLR types defined in your object model or external mapping file.</span></span>  
  
|<span data-ttu-id="788ed-190">CLR 型</span><span class="sxs-lookup"><span data-stu-id="788ed-190">CLR Type</span></span>|<span data-ttu-id="788ed-191"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> で使用される既定の SQL Server 型</span><span class="sxs-lookup"><span data-stu-id="788ed-191">Default SQL Server Type used by <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType></span></span>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<span data-ttu-id="788ed-192"><xref:System.Char?displayProperty=nameWithType>[]</span><span class="sxs-lookup"><span data-stu-id="788ed-192"><xref:System.Char?displayProperty=nameWithType>[]</span></span>|`NVARCHAR(4000)`|  
|<span data-ttu-id="788ed-193">`Parse()` および `ToString()` を実装するカスタム型</span><span class="sxs-lookup"><span data-stu-id="788ed-193">Custom type implementing `Parse()` and `ToString()`</span></span>|`NVARCHAR(MAX)`|  
  
 <span data-ttu-id="788ed-194">これ以外にもさまざまなテキスト ベースおよび XML のマッピングを選択できますが、一部のマッピングでは、データベースに対する変換操作中にオーバーフローやデータ損失の例外が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="788ed-194">There are many other text-based and XML mappings you can choose, but some may result in overflow or data loss exceptions while translating to or from the database.</span></span> <span data-ttu-id="788ed-195">詳細については、「[型マッピングと実行時動作の関係](#BehaviorMatrix)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-195">For more information, see the [Type Mapping Run Time Behavior Matrix](#BehaviorMatrix).</span></span>  
  
### <a name="xml-types"></a><span data-ttu-id="788ed-196">XML 型</span><span class="sxs-lookup"><span data-stu-id="788ed-196">XML Types</span></span>  

 <span data-ttu-id="788ed-197">SQL Server の `XML` データ型は、Microsoft SQL Server 2005 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="788ed-197">The SQL Server `XML` data type is available starting in Microsoft SQL Server 2005.</span></span> <span data-ttu-id="788ed-198">SQL Server の `XML` データ型は、<xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XDocument>、または <xref:System.String> にマップできます。</span><span class="sxs-lookup"><span data-stu-id="788ed-198">You can map the SQL Server `XML` data type to <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>, or <xref:System.String>.</span></span> <span data-ttu-id="788ed-199"><xref:System.Xml.Linq.XElement> に読み込むことができない XML フラグメントが列に格納されている場合は、列を <xref:System.String> にマップして、実行時エラーを回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="788ed-199">If the column stores XML fragments that cannot be read into <xref:System.Xml.Linq.XElement>, the column must be mapped to <xref:System.String> to avoid run-time errors.</span></span> <span data-ttu-id="788ed-200"><xref:System.String> にマップする必要がある XML フラグメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="788ed-200">XML fragments that must be mapped to <xref:System.String> include the following:</span></span>  
  
- <span data-ttu-id="788ed-201">XML 要素のシーケンス</span><span class="sxs-lookup"><span data-stu-id="788ed-201">A sequence of XML elements</span></span>  
  
- <span data-ttu-id="788ed-202">属性</span><span class="sxs-lookup"><span data-stu-id="788ed-202">Attributes</span></span>  
  
- <span data-ttu-id="788ed-203">パブリック識別子 (PI)</span><span class="sxs-lookup"><span data-stu-id="788ed-203">Public Identifiers (PI)</span></span>  
  
- <span data-ttu-id="788ed-204">コメント</span><span class="sxs-lookup"><span data-stu-id="788ed-204">Comments</span></span>  
  
 <span data-ttu-id="788ed-205"><xref:System.Xml.Linq.XElement> および <xref:System.Xml.Linq.XDocument> は、「[型マッピングと実行時動作の関係](#BehaviorMatrix)」で示したように SQL Server にマップすることができますが、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> メソッドには、これらの型に対する既定の SQL Server 型マッピングはありません。</span><span class="sxs-lookup"><span data-stu-id="788ed-205">Although you can map <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> to SQL Server as shown in the [Type Mapping Run Time Behavior Matrix](#BehaviorMatrix), the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method has no default SQL Server type mapping for these types.</span></span>  
  
### <a name="custom-types"></a><span data-ttu-id="788ed-206">カスタム型</span><span class="sxs-lookup"><span data-stu-id="788ed-206">Custom Types</span></span>  

 <span data-ttu-id="788ed-207">クラスで `Parse()` および `ToString()` が実装されている場合は、そのオブジェクトを SQL の任意のテキスト型 (`CHAR`、`NCHAR`、`VARCHAR`、`NVARCHAR`、`TEXT`、`NTEXT`、`XML`) にマップできます。</span><span class="sxs-lookup"><span data-stu-id="788ed-207">If a class implements `Parse()` and `ToString()`, you can map the object to any SQL text type (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`, `TEXT`, `NTEXT`, `XML`).</span></span> <span data-ttu-id="788ed-208">オブジェクトをデータベースに格納するには、`ToString()` から返された値をマップ先のデータベース列に送信します。</span><span class="sxs-lookup"><span data-stu-id="788ed-208">The object is stored in the database by sending the value returned by `ToString()` to the mapped database column.</span></span> <span data-ttu-id="788ed-209">オブジェクトを再構築するには、データベースから返された文字列に対して `Parse()` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="788ed-209">The object is reconstructed by invoking `Parse()` on the string returned by the database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="788ed-210">LINQ to SQL では、<xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType> の使用によるシリアル化はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="788ed-210">LINQ to SQL does not support serialization by using <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.</span></span>  
  
<a name="DateMapping"></a>

## <a name="date-and-time-mapping"></a><span data-ttu-id="788ed-211">日付および時刻のマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-211">Date and Time Mapping</span></span>  

 <span data-ttu-id="788ed-212">LINQ to SQL では、SQL Server のさまざまな日付型および時刻型をマップできます。</span><span class="sxs-lookup"><span data-stu-id="788ed-212">With LINQ to SQL, you can map many SQL Server date and time types.</span></span> <span data-ttu-id="788ed-213">次の表に、O/R デザイナーおよび SQLMetal でデータベースに基づいてオブジェクト モデルまたは外部マッピング ファイルを作成するときに選択される CLR 型を示します。</span><span class="sxs-lookup"><span data-stu-id="788ed-213">The following table shows the CLR types that O/R Designer and SQLMetal select when building an object model or external mapping file based on your database.</span></span>  
  
|<span data-ttu-id="788ed-214">SQL Server 型</span><span class="sxs-lookup"><span data-stu-id="788ed-214">SQL Server Type</span></span>|<span data-ttu-id="788ed-215">O/R デザイナーおよび SQLMetal で使用される既定の CLR 型マッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-215">Default CLR Type mapping used by O/R Designer and SQLMetal</span></span>|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 <span data-ttu-id="788ed-216">次の表に、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> メソッドで使用される既定の型マッピングを示します。既定の型マッピングでは、オブジェクト モデルまたは外部マッピング ファイルで定義された CLR 型にマップするために作成される SQL 列の型が定義されています。</span><span class="sxs-lookup"><span data-stu-id="788ed-216">The next table shows the default type mappings used by the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method to define which type of SQL columns are created to map to the CLR types defined in your object model or external mapping file.</span></span>  
  
|<span data-ttu-id="788ed-217">CLR 型</span><span class="sxs-lookup"><span data-stu-id="788ed-217">CLR Type</span></span>|<span data-ttu-id="788ed-218"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> で使用される既定の SQL Server 型</span><span class="sxs-lookup"><span data-stu-id="788ed-218">Default SQL Server Type used by <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType></span></span>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 <span data-ttu-id="788ed-219">これ以外にもさまざまな日付および時刻のマッピングを選択できますが、一部のマッピングでは、データベースに対する変換操作中にオーバーフローやデータ損失の例外が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="788ed-219">There are many other date and time mappings you can choose, but some may result in overflow or data loss exceptions while translating to or from the database.</span></span> <span data-ttu-id="788ed-220">詳細については、「[型マッピングと実行時動作の関係](#BehaviorMatrix)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-220">For more information, see the [Type Mapping Run Time Behavior Matrix](#BehaviorMatrix).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="788ed-221">SQL Server の `DATETIME2` 型、`DATETIMEOFFSET` 型、`DATE` 型、および `TIME` 型は、Microsoft SQL Server 2008 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="788ed-221">The SQL Server types `DATETIME2`, `DATETIMEOFFSET`, `DATE`, and `TIME` are available starting with Microsoft SQL Server 2008.</span></span> <span data-ttu-id="788ed-222">Microsoft .NET Framework version 3.5 SP1 以降の LINQ to SQL では、これらの新しい型へのマッピングがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="788ed-222">LINQ to SQL supports mapping to these new types starting with the .NET Framework version 3.5 SP1.</span></span>  
  
### <a name="systemdatetime"></a><span data-ttu-id="788ed-223">System.Datetime</span><span class="sxs-lookup"><span data-stu-id="788ed-223">System.Datetime</span></span>  

 <span data-ttu-id="788ed-224">CLR の <xref:System.DateTime?displayProperty=nameWithType> 型の範囲と有効桁数の値は、`DATETIME` メソッドの既定の型マッピングである SQL Server の <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 型の範囲と有効桁数より大きな値です。</span><span class="sxs-lookup"><span data-stu-id="788ed-224">The range and precision of the CLR <xref:System.DateTime?displayProperty=nameWithType> type is greater than the range and precision of the SQL Server `DATETIME` type, which is the default type mapping for the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="788ed-225">`DATETIME` の範囲外の日付に関連する例外を回避するには、Microsoft SQL Server 2008 以降で利用できる `DATETIME2` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-225">To help avoid exceptions related to dates outside the range of `DATETIME`, use `DATETIME2`, which is available starting with Microsoft SQL Server 2008.</span></span> <span data-ttu-id="788ed-226">`DATETIME2`は、CLR の <xref:System.DateTime?displayProperty=nameWithType> の範囲と精度に対応させることができます。</span><span class="sxs-lookup"><span data-stu-id="788ed-226">`DATETIME2` can match the range and precision of the CLR <xref:System.DateTime?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="788ed-227">SQL Server の日付には、CLR で十分にサポートされている機能である <xref:System.TimeZone> の概念がありません。</span><span class="sxs-lookup"><span data-stu-id="788ed-227">SQL Server dates have no concept of <xref:System.TimeZone>, a feature that is richly supported in the CLR.</span></span> <span data-ttu-id="788ed-228"><xref:System.TimeZone> の値は、元の <xref:System.TimeZone> の情報にかかわらず、<xref:System.DateTimeKind> 変換なしでそのまま保存されます。</span><span class="sxs-lookup"><span data-stu-id="788ed-228"><xref:System.TimeZone> values are saved as is to the database without <xref:System.TimeZone> conversion, regardless of the original <xref:System.DateTimeKind> information.</span></span> <span data-ttu-id="788ed-229"><xref:System.DateTime> 値がデータベースから取得される場合、その値は、<xref:System.DateTime> が <xref:System.DateTimeKind> の状態で、そのまま <xref:System.DateTimeKind.Unspecified> に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="788ed-229">When <xref:System.DateTime> values are retrieved from the database, their value is loaded as is into a <xref:System.DateTime> with a <xref:System.DateTimeKind> of <xref:System.DateTimeKind.Unspecified>.</span></span> <span data-ttu-id="788ed-230">サポートされる <xref:System.DateTime?displayProperty=nameWithType> メソッドの詳細については、「[System.DateTime メソッド](system-datetime-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-230">For more information about supported <xref:System.DateTime?displayProperty=nameWithType> methods, see [System.DateTime Methods](system-datetime-methods.md).</span></span>  
  
### <a name="systemtimespan"></a><span data-ttu-id="788ed-231">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="788ed-231">System.TimeSpan</span></span>  

 <span data-ttu-id="788ed-232">Microsoft SQL Server 2008 および .NET Framework 3.5 SP1 では、CLR の <xref:System.TimeSpan?displayProperty=nameWithType> 型を SQL Server の `TIME` 型にマップできます。</span><span class="sxs-lookup"><span data-stu-id="788ed-232">Microsoft SQL Server 2008 and the .NET Framework 3.5 SP1 let you map the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type to the SQL Server `TIME` type.</span></span> <span data-ttu-id="788ed-233">ただし、CLR の <xref:System.TimeSpan?displayProperty=nameWithType> でサポートされる範囲と SQL Server `TIME` 型でサポートされる範囲には大きな差があります。</span><span class="sxs-lookup"><span data-stu-id="788ed-233">However, there is a large difference between the range that the CLR <xref:System.TimeSpan?displayProperty=nameWithType> supports and what the SQL Server `TIME` type supports.</span></span> <span data-ttu-id="788ed-234">時間を表す 0 より小さい値または 23:59:59.9999999 より大きい値を SQL の `TIME` にマップすると、オーバーフロー例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="788ed-234">Mapping values less than 0 or greater than 23:59:59.9999999 hours to the SQL `TIME` will result in overflow exceptions.</span></span> <span data-ttu-id="788ed-235">詳細については、「[System.TimeSpan メソッド](system-timespan-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-235">For more information, see [System.TimeSpan Methods](system-timespan-methods.md).</span></span>  
  
 <span data-ttu-id="788ed-236">Microsoft SQL Server 2000 および SQL Server 2005 では、データベース フィールドを <xref:System.TimeSpan> にマップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="788ed-236">In Microsoft SQL Server 2000 and SQL Server 2005, you cannot map database fields to <xref:System.TimeSpan>.</span></span> <span data-ttu-id="788ed-237">ただし、<xref:System.TimeSpan> 値を <xref:System.TimeSpan> 減算から返したり、リテラル変数またはバインド変数として式に取り込んだりできるため、<xref:System.DateTime> の操作はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="788ed-237">However, operations on <xref:System.TimeSpan> are supported because <xref:System.TimeSpan> values can be returned from <xref:System.DateTime> subtraction or introduced into an expression as a literal or bound variable.</span></span>  
  
<a name="BinaryMapping"></a>

## <a name="binary-mapping"></a><span data-ttu-id="788ed-238">バイナリのマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-238">Binary Mapping</span></span>  

 <span data-ttu-id="788ed-239">SQL Server のさまざまな型を CLR の <xref:System.Data.Linq.Binary?displayProperty=nameWithType> 型にマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="788ed-239">There are many SQL Server types that can map to the CLR type <xref:System.Data.Linq.Binary?displayProperty=nameWithType>.</span></span> <span data-ttu-id="788ed-240">次の表に、O/R デザイナーおよび SQLMetal でデータベースに基づいてオブジェクト モデルまたは外部マッピング ファイルを作成するときに、CLR の <xref:System.Data.Linq.Binary?displayProperty=nameWithType> 型が選択される SQL Server 型を示します。</span><span class="sxs-lookup"><span data-stu-id="788ed-240">The following table shows the SQL Server types that cause O/R Designer and SQLMetal to define a CLR <xref:System.Data.Linq.Binary?displayProperty=nameWithType> type when building an object model or external mapping file based on your database.</span></span>  
  
|<span data-ttu-id="788ed-241">SQL Server 型</span><span class="sxs-lookup"><span data-stu-id="788ed-241">SQL Server Type</span></span>|<span data-ttu-id="788ed-242">O/R デザイナーおよび SQLMetal で使用される既定の CLR 型マッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-242">Default CLR Type mapping used by O/R Designer and SQLMetal</span></span>|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|<span data-ttu-id="788ed-243">`FILESTREAM` 属性を持つ `VARBINARY(MAX)`</span><span class="sxs-lookup"><span data-stu-id="788ed-243">`VARBINARY(MAX)` with the `FILESTREAM` attribute</span></span>|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 <span data-ttu-id="788ed-244">次の表に、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> メソッドで使用される既定の型マッピングを示します。既定の型マッピングでは、オブジェクト モデルまたは外部マッピング ファイルで定義された CLR 型にマップするために作成される SQL 列の型が定義されています。</span><span class="sxs-lookup"><span data-stu-id="788ed-244">The next table shows the default type mappings used by the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method to define which type of SQL columns are created to map to the CLR types defined in your object model or external mapping file.</span></span>  
  
|<span data-ttu-id="788ed-245">CLR 型</span><span class="sxs-lookup"><span data-stu-id="788ed-245">CLR Type</span></span>|<span data-ttu-id="788ed-246"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> で使用される既定の SQL Server 型</span><span class="sxs-lookup"><span data-stu-id="788ed-246">Default SQL Server Type used by <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType></span></span>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 <span data-ttu-id="788ed-247">これ以外にもさまざまなバイナリのマッピングを選択できますが、一部のマッピングでは、データベースに対する変換操作中にオーバーフローやデータ損失の例外が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="788ed-247">There are many other binary mappings you can choose, but some may result in overflow or data loss exceptions while translating to or from the database.</span></span> <span data-ttu-id="788ed-248">詳細については、「[型マッピングと実行時動作の関係](#BehaviorMatrix)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-248">For more information, see the [Type Mapping Run Time Behavior Matrix](#BehaviorMatrix).</span></span>  
  
### <a name="sql-server-filestream"></a><span data-ttu-id="788ed-249">SQL Server の FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="788ed-249">SQL Server FILESTREAM</span></span>  

 <span data-ttu-id="788ed-250">`FILESTREAM` 列の `VARBINARY(MAX)` 属性は、Microsoft SQL Server 2008 以降で使用できます。.NET Framework version 3.5 SP1 以降の LINQ to SQL では、これらの属性にマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="788ed-250">The `FILESTREAM` attribute for `VARBINARY(MAX)` columns is available starting with Microsoft SQL Server 2008; you can map to it with LINQ to SQL starting with the .NET Framework version 3.5 SP1.</span></span>  
  
 <span data-ttu-id="788ed-251">`VARBINARY(MAX)` 属性を持つ `FILESTREAM` 列を <xref:System.Data.Linq.Binary> オブジェクトにマップすることはできますが、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> メソッドを使用して `FILESTREAM` 属性を持つ列を自動的に作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="788ed-251">Although you can map `VARBINARY(MAX)` columns with the `FILESTREAM` attribute to <xref:System.Data.Linq.Binary> objects, the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method is unable to automatically create columns with the `FILESTREAM` attribute.</span></span> <span data-ttu-id="788ed-252">`FILESTREAM` について詳しくは、「[FILESTREAM の概要](/previous-versions/sql/sql-server-2008-r2/bb933993(v=sql.105))」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="788ed-252">For more information about `FILESTREAM`, see [FILESTREAM Overview](/previous-versions/sql/sql-server-2008-r2/bb933993(v=sql.105)).</span></span>  
  
<a name="BinarySerialization"></a>

### <a name="binary-serialization"></a><span data-ttu-id="788ed-253">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="788ed-253">Binary Serialization</span></span>  

 <span data-ttu-id="788ed-254">クラスが <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装している場合は、オブジェクトを SQL バイナリ フィールド (`BINARY`、`VARBINARY`、`IMAGE`) にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="788ed-254">If a class implements the <xref:System.Runtime.Serialization.ISerializable> interface, you can serialize an object to any SQL binary field (`BINARY`, `VARBINARY`, `IMAGE`).</span></span> <span data-ttu-id="788ed-255"><xref:System.Runtime.Serialization.ISerializable> インターフェイスの実装方法に従って、オブジェクトのシリアル化と逆シリアル化が行われます。</span><span class="sxs-lookup"><span data-stu-id="788ed-255">The object is serialized and deserialized according to how the <xref:System.Runtime.Serialization.ISerializable> interface is implemented.</span></span> <span data-ttu-id="788ed-256">詳しくは、「[バイナリ シリアル化](../../../../../standard/serialization/binary-serialization.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="788ed-256">For more information, see [Binary Serialization](../../../../../standard/serialization/binary-serialization.md).</span></span>
  
<a name="MiscMapping"></a>

## <a name="miscellaneous-mapping"></a><span data-ttu-id="788ed-257">その他のマッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-257">Miscellaneous Mapping</span></span>  

 <span data-ttu-id="788ed-258">ここでは、上記以外のさまざまな型について、既定の型マッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="788ed-258">The following table shows the default type mappings for some miscellaneous types that have not yet been mentioned.</span></span> <span data-ttu-id="788ed-259">次の表に、O/R デザイナーおよび SQLMetal でデータベースに基づいてオブジェクト モデルまたは外部マッピング ファイルを作成するときに選択される CLR 型を示します。</span><span class="sxs-lookup"><span data-stu-id="788ed-259">The following table shows the CLR types that O/R Designer and SQLMetal select when building an object model or external mapping file based on your database.</span></span>  
  
|<span data-ttu-id="788ed-260">SQL Server 型</span><span class="sxs-lookup"><span data-stu-id="788ed-260">SQL Server Type</span></span>|<span data-ttu-id="788ed-261">O/R デザイナーおよび SQLMetal で使用される既定の CLR 型マッピング</span><span class="sxs-lookup"><span data-stu-id="788ed-261">Default CLR Type mapping used by O/R Designer and SQLMetal</span></span>|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 <span data-ttu-id="788ed-262">次の表に、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> メソッドで使用される既定の型マッピングを示します。既定の型マッピングでは、オブジェクト モデルまたは外部マッピング ファイルで定義された CLR 型にマップするために作成される SQL 列の型が定義されています。</span><span class="sxs-lookup"><span data-stu-id="788ed-262">The next table shows the default type mappings used by the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method to define which type of SQL columns are created to map to the CLR types defined in your object model or external mapping file.</span></span>  
  
|<span data-ttu-id="788ed-263">CLR 型</span><span class="sxs-lookup"><span data-stu-id="788ed-263">CLR Type</span></span>|<span data-ttu-id="788ed-264"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> で使用される既定の SQL Server 型</span><span class="sxs-lookup"><span data-stu-id="788ed-264">Default SQL Server Type used by <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType></span></span>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 <span data-ttu-id="788ed-265">LINQ to SQL では、ここに示したその他の型に対する上記以外の型マッピングはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="788ed-265">LINQ to SQL does not support any other type mappings for these miscellaneous types.</span></span>  <span data-ttu-id="788ed-266">詳細については、「[型マッピングと実行時動作の関係](#BehaviorMatrix)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="788ed-266">For more information, see the [Type Mapping Run Time Behavior Matrix](#BehaviorMatrix).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="788ed-267">関連項目</span><span class="sxs-lookup"><span data-stu-id="788ed-267">See also</span></span>

- [<span data-ttu-id="788ed-268">属性ベースの対応付け</span><span class="sxs-lookup"><span data-stu-id="788ed-268">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="788ed-269">外部マップ</span><span class="sxs-lookup"><span data-stu-id="788ed-269">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="788ed-270">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="788ed-270">Data Types and Functions</span></span>](data-types-and-functions.md)
- [<span data-ttu-id="788ed-271">SQL と CLR の型の不一致</span><span class="sxs-lookup"><span data-stu-id="788ed-271">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)

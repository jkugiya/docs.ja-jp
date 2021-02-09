---
description: '詳細情報: Oracle REF CURSOR'
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 0a9c5e95a9f0d2da74fd6a3db19f15699a3e2787
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672453"
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="e4b00-103">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="e4b00-103">Oracle REF CURSORs</span></span>

<span data-ttu-id="e4b00-104">.NET Framework Data Provider for Oracle では、Oracle の **REF CURSOR** データ型がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e4b00-104">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="e4b00-105">データ プロバイダーを使用して Oracle REF CURSOR を操作するときは、次の動作を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4b00-105">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4b00-106">動作の中には、Microsoft OLE DB Provider for Oracle (MSDAORA) の動作と異なるものがあります。</span><span class="sxs-lookup"><span data-stu-id="e4b00-106">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
- <span data-ttu-id="e4b00-107">パフォーマンスの理由から、Data Provider for Oracle では、バインドするよう明示的に指定した場合を除き、**REF CURSOR** データ型が自動的にバインドされることはありません。これは、MSDAORA の場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="e4b00-107">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
- <span data-ttu-id="e4b00-108">データ プロバイダーでは、REF CURSOR パラメーターの指定に使用する {resultset} エスケープのような、ODBC エスケープ シーケンスはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e4b00-108">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
- <span data-ttu-id="e4b00-109">REF CURSOR を返すストアド プロシージャを実行するには、<xref:System.Data.OracleClient.OracleParameterCollection> のパラメーターで、<xref:System.Data.OracleClient.OracleType> を **Cursor** に、<xref:System.Data.OracleClient.OracleParameter.Direction%2A> を **Output** に定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4b00-109">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="e4b00-110">データ プロバイダーでは、REF CURSOR のバインドは出力パラメーターとしてのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e4b00-110">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="e4b00-111">プロバイダーは、入力パラメーターとしての REF CURSOR はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e4b00-111">The provider does not support REF CURSORs as input parameters.</span></span>  
  
- <span data-ttu-id="e4b00-112">パラメーター値からの <xref:System.Data.OracleClient.OracleDataReader> の取得はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e4b00-112">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="e4b00-113">値は、コマンドを実行すると <xref:System.DBNull> 型になります。</span><span class="sxs-lookup"><span data-stu-id="e4b00-113">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
- <span data-ttu-id="e4b00-114">REF CURSOR で動作する **CommandBehavior** 列挙値は (たとえば、<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> を呼び出すとき)、**CloseConnection** だけです。それ以外はすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="e4b00-114">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
- <span data-ttu-id="e4b00-115">**OracleDataReader** 内の REF CURSOR の順序は、**OracleParameterCollection** でのパラメーターの順序によって決まります。</span><span class="sxs-lookup"><span data-stu-id="e4b00-115">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="e4b00-116"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> プロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="e4b00-116">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
- <span data-ttu-id="e4b00-117">PL/SQL の **TABLE** データ型はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e4b00-117">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="e4b00-118">ただし、REF CURSOR は、さらに効果的です。</span><span class="sxs-lookup"><span data-stu-id="e4b00-118">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="e4b00-119">**TABLE** データ型を使用する必要がある場合は、MSDAORA と共に OLE DB .NET データ プロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="e4b00-119">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4b00-120">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e4b00-120">In This Section</span></span>  

 [<span data-ttu-id="e4b00-121">REF CURSOR の例</span><span class="sxs-lookup"><span data-stu-id="e4b00-121">REF CURSOR Examples</span></span>](ref-cursor-examples.md)  
 <span data-ttu-id="e4b00-122">次の 3 つの例を使って REF CURSOR の使い方について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4b00-122">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="e4b00-123">OracleDataReader の REF CURSOR パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b00-123">REF CURSOR Parameters in an OracleDataReader</span></span>](ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="e4b00-124">REF CURSOR パラメーターを返し、**OracleDataReader** として値を読み取る、PL/SQL のストアド プロシージャを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e4b00-124">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="e4b00-125">OracleDataReader を使用した複数の REF CURSOR からのデータの取得</span><span class="sxs-lookup"><span data-stu-id="e4b00-125">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="e4b00-126">REF CURSOR パラメーターを返し、**OracleDataReader** を使用して値を読み取る、PL/SQL のストアド プロシージャを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e4b00-126">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="e4b00-127">1 つまたは複数の REF CURSOR を使用した DataSet の値の設定</span><span class="sxs-lookup"><span data-stu-id="e4b00-127">Filling a DataSet Using One or More REF CURSORs</span></span>](filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="e4b00-128">2 つの REF CURSOR パラメーターを返し、返された行を <xref:System.Data.DataSet> に入力する、PL/SQL ストアド プロシージャを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4b00-128">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b00-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4b00-129">See also</span></span>

- [<span data-ttu-id="e4b00-130">Oracle および ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e4b00-130">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="e4b00-131">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="e4b00-131">ADO.NET Overview</span></span>](ado-net-overview.md)

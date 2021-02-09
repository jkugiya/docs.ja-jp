---
description: '詳細情報: スキーマの制限'
title: スキーマの制限
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 74ddfe5b8aaf9b8193e0c0b2a929ccde333eac26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719046"
---
# <a name="schema-restrictions"></a><span data-ttu-id="e000c-103">スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="e000c-103">Schema Restrictions</span></span>

<span data-ttu-id="e000c-104">**GetSchema** メソッドの 2 番目のオプション パラメーターは、返されるスキーマ情報の量を制限するために使用される制限で、文字列の配列として **GetSchema** メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="e000c-104">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="e000c-105">配列での位置により、渡すことができる値が決定します。これは、制限の番号に相当します。</span><span class="sxs-lookup"><span data-stu-id="e000c-105">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="e000c-106">たとえば、次の表は、.NET Framework Data Provider for SQL Server を使用して、"Tables" スキーマ コレクションによりサポートされる制限を示しています。</span><span class="sxs-lookup"><span data-stu-id="e000c-106">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="e000c-107">SQL Server スキーマ コレクションの追加の制限をこのトピックの終わりに示します。</span><span class="sxs-lookup"><span data-stu-id="e000c-107">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="e000c-108">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-108">Restriction Name</span></span>|<span data-ttu-id="e000c-109">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-109">Parameter Name</span></span>|<span data-ttu-id="e000c-110">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-110">Restriction Default</span></span>|<span data-ttu-id="e000c-111">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-111">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-112">Catalog</span><span class="sxs-lookup"><span data-stu-id="e000c-112">Catalog</span></span>|@Catalog|<span data-ttu-id="e000c-113">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e000c-113">TABLE_CATALOG</span></span>|<span data-ttu-id="e000c-114">1</span><span class="sxs-lookup"><span data-stu-id="e000c-114">1</span></span>|  
|<span data-ttu-id="e000c-115">Owner</span><span class="sxs-lookup"><span data-stu-id="e000c-115">Owner</span></span>|@Owner|<span data-ttu-id="e000c-116">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e000c-116">TABLE_SCHEMA</span></span>|<span data-ttu-id="e000c-117">2</span><span class="sxs-lookup"><span data-stu-id="e000c-117">2</span></span>|  
|<span data-ttu-id="e000c-118">テーブル</span><span class="sxs-lookup"><span data-stu-id="e000c-118">Table</span></span>|@Name|<span data-ttu-id="e000c-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-119">TABLE_NAME</span></span>|<span data-ttu-id="e000c-120">3</span><span class="sxs-lookup"><span data-stu-id="e000c-120">3</span></span>|  
|<span data-ttu-id="e000c-121">TableType</span><span class="sxs-lookup"><span data-stu-id="e000c-121">TableType</span></span>|@TableType|<span data-ttu-id="e000c-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e000c-122">TABLE_TYPE</span></span>|<span data-ttu-id="e000c-123">4</span><span class="sxs-lookup"><span data-stu-id="e000c-123">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="e000c-124">制限値の指定</span><span class="sxs-lookup"><span data-stu-id="e000c-124">Specifying Restriction Values</span></span>  

 <span data-ttu-id="e000c-125">"Tables" スキーマ コレクションの制限の 1 つを使用するには、4 つの要素を使って文字列の配列を作成してから、制限の番号と一致する要素内に値を配置します。</span><span class="sxs-lookup"><span data-stu-id="e000c-125">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="e000c-126">たとえば、**GetSchema** メソッドにより返されるテーブルを、"Sales" スキーマ内のテーブルのみに制限するには、**GetSchema** メソッドに渡す前に、配列の 2 番目の要素を "Sales" に設定します。</span><span class="sxs-lookup"><span data-stu-id="e000c-126">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e000c-127">`SqlClient` と `OracleClient` の制限のコレクションには、追加の `ParameterName` 列があります。</span><span class="sxs-lookup"><span data-stu-id="e000c-127">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="e000c-128">制限の既定の列は、下位互換性のために存在してはいますが、現在は無視されています。</span><span class="sxs-lookup"><span data-stu-id="e000c-128">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="e000c-129">制限の値を指定する場合、文字列置換ではなく、パラメーター付きのクエリを使って、SQL への注入攻撃のリスクを最小限にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e000c-129">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e000c-130">配列内の要素数は、指定したスキーマ コレクションでサポートされる制限数以下にする必要があります。そうでない場合、<xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e000c-130">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="e000c-131">制限は最大数よりも小さい場合があります。</span><span class="sxs-lookup"><span data-stu-id="e000c-131">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="e000c-132">指定されていない制限は、null (無制限) と見なされます。</span><span class="sxs-lookup"><span data-stu-id="e000c-132">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="e000c-133">.NET Framework マネージド プロバイダーでは、"Restrictions" という制限のスキーマ コレクションの名前を指定して **GetSchema** メソッドを呼び出すことにより、サポートされる制限の一覧を特定します。</span><span class="sxs-lookup"><span data-stu-id="e000c-133">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="e000c-134">これにより、コレクション名の一覧、制限の名前、既定の制限値、および制限の番号と共に、<xref:System.Data.DataTable> が返されます。</span><span class="sxs-lookup"><span data-stu-id="e000c-134">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e000c-135">例</span><span class="sxs-lookup"><span data-stu-id="e000c-135">Example</span></span>  

 <span data-ttu-id="e000c-136">.NET Framework Data Provider for the SQL Server の <xref:System.Data.SqlClient.SqlConnection> クラスの <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> メソッドを使用して、**AdventureWorks** サンプル データベースに含まれるすべてのテーブルに関するスキーマ情報を取得し、返される情報を "Sales" スキーマ内のテーブルのみに制限する方法について、いくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e000c-136">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="e000c-137">SQL Server スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="e000c-137">SQL Server Schema Restrictions</span></span>  

 <span data-ttu-id="e000c-138">次の表に、SQL Server スキーマ コレクションの制限を示します。</span><span class="sxs-lookup"><span data-stu-id="e000c-138">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="e000c-139">Users</span><span class="sxs-lookup"><span data-stu-id="e000c-139">Users</span></span>  
  
|<span data-ttu-id="e000c-140">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-140">Restriction Name</span></span>|<span data-ttu-id="e000c-141">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-141">Parameter Name</span></span>|<span data-ttu-id="e000c-142">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-142">Restriction Default</span></span>|<span data-ttu-id="e000c-143">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-143">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-144">User_Name</span><span class="sxs-lookup"><span data-stu-id="e000c-144">User_Name</span></span>|@Name|<span data-ttu-id="e000c-145">name</span><span class="sxs-lookup"><span data-stu-id="e000c-145">name</span></span>|<span data-ttu-id="e000c-146">1</span><span class="sxs-lookup"><span data-stu-id="e000c-146">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="e000c-147">データベース</span><span class="sxs-lookup"><span data-stu-id="e000c-147">Databases</span></span>  
  
|<span data-ttu-id="e000c-148">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-148">Restriction Name</span></span>|<span data-ttu-id="e000c-149">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-149">Parameter Name</span></span>|<span data-ttu-id="e000c-150">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-150">Restriction Default</span></span>|<span data-ttu-id="e000c-151">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-151">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-152">名前</span><span class="sxs-lookup"><span data-stu-id="e000c-152">Name</span></span>|@Name|<span data-ttu-id="e000c-153">名前</span><span class="sxs-lookup"><span data-stu-id="e000c-153">Name</span></span>|<span data-ttu-id="e000c-154">1</span><span class="sxs-lookup"><span data-stu-id="e000c-154">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="e000c-155">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="e000c-155">Tables</span></span>  
  
|<span data-ttu-id="e000c-156">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-156">Restriction Name</span></span>|<span data-ttu-id="e000c-157">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-157">Parameter Name</span></span>|<span data-ttu-id="e000c-158">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-158">Restriction Default</span></span>|<span data-ttu-id="e000c-159">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-159">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-160">Catalog</span><span class="sxs-lookup"><span data-stu-id="e000c-160">Catalog</span></span>|@Catalog|<span data-ttu-id="e000c-161">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e000c-161">TABLE_CATALOG</span></span>|<span data-ttu-id="e000c-162">1</span><span class="sxs-lookup"><span data-stu-id="e000c-162">1</span></span>|  
|<span data-ttu-id="e000c-163">Owner</span><span class="sxs-lookup"><span data-stu-id="e000c-163">Owner</span></span>|@Owner|<span data-ttu-id="e000c-164">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e000c-164">TABLE_SCHEMA</span></span>|<span data-ttu-id="e000c-165">2</span><span class="sxs-lookup"><span data-stu-id="e000c-165">2</span></span>|  
|<span data-ttu-id="e000c-166">テーブル</span><span class="sxs-lookup"><span data-stu-id="e000c-166">Table</span></span>|@Name|<span data-ttu-id="e000c-167">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-167">TABLE_NAME</span></span>|<span data-ttu-id="e000c-168">3</span><span class="sxs-lookup"><span data-stu-id="e000c-168">3</span></span>|  
|<span data-ttu-id="e000c-169">TableType</span><span class="sxs-lookup"><span data-stu-id="e000c-169">TableType</span></span>|@TableType|<span data-ttu-id="e000c-170">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e000c-170">TABLE_TYPE</span></span>|<span data-ttu-id="e000c-171">4</span><span class="sxs-lookup"><span data-stu-id="e000c-171">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e000c-172">列</span><span class="sxs-lookup"><span data-stu-id="e000c-172">Columns</span></span>  
  
|<span data-ttu-id="e000c-173">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-173">Restriction Name</span></span>|<span data-ttu-id="e000c-174">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-174">Parameter Name</span></span>|<span data-ttu-id="e000c-175">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-175">Restriction Default</span></span>|<span data-ttu-id="e000c-176">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-176">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-177">Catalog</span><span class="sxs-lookup"><span data-stu-id="e000c-177">Catalog</span></span>|@Catalog|<span data-ttu-id="e000c-178">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e000c-178">TABLE_CATALOG</span></span>|<span data-ttu-id="e000c-179">1</span><span class="sxs-lookup"><span data-stu-id="e000c-179">1</span></span>|  
|<span data-ttu-id="e000c-180">Owner</span><span class="sxs-lookup"><span data-stu-id="e000c-180">Owner</span></span>|@Owner|<span data-ttu-id="e000c-181">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e000c-181">TABLE_SCHEMA</span></span>|<span data-ttu-id="e000c-182">2</span><span class="sxs-lookup"><span data-stu-id="e000c-182">2</span></span>|  
|<span data-ttu-id="e000c-183">テーブル</span><span class="sxs-lookup"><span data-stu-id="e000c-183">Table</span></span>|@Table|<span data-ttu-id="e000c-184">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-184">TABLE_NAME</span></span>|<span data-ttu-id="e000c-185">3</span><span class="sxs-lookup"><span data-stu-id="e000c-185">3</span></span>|  
|<span data-ttu-id="e000c-186">Column</span><span class="sxs-lookup"><span data-stu-id="e000c-186">Column</span></span>|@Column|<span data-ttu-id="e000c-187">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-187">COLUMN_NAME</span></span>|<span data-ttu-id="e000c-188">4</span><span class="sxs-lookup"><span data-stu-id="e000c-188">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="e000c-189">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="e000c-189">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="e000c-190">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-190">Restriction Name</span></span>|<span data-ttu-id="e000c-191">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-191">Parameter Name</span></span>|<span data-ttu-id="e000c-192">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-192">Restriction Default</span></span>|<span data-ttu-id="e000c-193">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-193">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-194">Catalog</span><span class="sxs-lookup"><span data-stu-id="e000c-194">Catalog</span></span>|@Catalog|<span data-ttu-id="e000c-195">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e000c-195">TABLE_CATALOG</span></span>|<span data-ttu-id="e000c-196">1</span><span class="sxs-lookup"><span data-stu-id="e000c-196">1</span></span>|  
|<span data-ttu-id="e000c-197">Owner</span><span class="sxs-lookup"><span data-stu-id="e000c-197">Owner</span></span>|@Owner|<span data-ttu-id="e000c-198">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e000c-198">TABLE_SCHEMA</span></span>|<span data-ttu-id="e000c-199">2</span><span class="sxs-lookup"><span data-stu-id="e000c-199">2</span></span>|  
|<span data-ttu-id="e000c-200">テーブル</span><span class="sxs-lookup"><span data-stu-id="e000c-200">Table</span></span>|@Table|<span data-ttu-id="e000c-201">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-201">TABLE_NAME</span></span>|<span data-ttu-id="e000c-202">3</span><span class="sxs-lookup"><span data-stu-id="e000c-202">3</span></span>|  
|<span data-ttu-id="e000c-203">Column</span><span class="sxs-lookup"><span data-stu-id="e000c-203">Column</span></span>|@Column|<span data-ttu-id="e000c-204">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-204">COLUMN_NAME</span></span>|<span data-ttu-id="e000c-205">4</span><span class="sxs-lookup"><span data-stu-id="e000c-205">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="e000c-206">Views</span><span class="sxs-lookup"><span data-stu-id="e000c-206">Views</span></span>  
  
|<span data-ttu-id="e000c-207">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-207">Restriction Name</span></span>|<span data-ttu-id="e000c-208">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-208">Parameter Name</span></span>|<span data-ttu-id="e000c-209">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-209">Restriction Default</span></span>|<span data-ttu-id="e000c-210">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-210">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-211">Catalog</span><span class="sxs-lookup"><span data-stu-id="e000c-211">Catalog</span></span>|@Catalog|<span data-ttu-id="e000c-212">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e000c-212">TABLE_CATALOG</span></span>|<span data-ttu-id="e000c-213">1</span><span class="sxs-lookup"><span data-stu-id="e000c-213">1</span></span>|  
|<span data-ttu-id="e000c-214">Owner</span><span class="sxs-lookup"><span data-stu-id="e000c-214">Owner</span></span>|@Owner|<span data-ttu-id="e000c-215">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e000c-215">TABLE_SCHEMA</span></span>|<span data-ttu-id="e000c-216">2</span><span class="sxs-lookup"><span data-stu-id="e000c-216">2</span></span>|  
|<span data-ttu-id="e000c-217">テーブル</span><span class="sxs-lookup"><span data-stu-id="e000c-217">Table</span></span>|@Table|<span data-ttu-id="e000c-218">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-218">TABLE_NAME</span></span>|<span data-ttu-id="e000c-219">3</span><span class="sxs-lookup"><span data-stu-id="e000c-219">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="e000c-220">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="e000c-220">ViewColumns</span></span>  
  
|<span data-ttu-id="e000c-221">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-221">Restriction Name</span></span>|<span data-ttu-id="e000c-222">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-222">Parameter Name</span></span>|<span data-ttu-id="e000c-223">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-223">Restriction Default</span></span>|<span data-ttu-id="e000c-224">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-224">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-225">Catalog</span><span class="sxs-lookup"><span data-stu-id="e000c-225">Catalog</span></span>|@Catalog|<span data-ttu-id="e000c-226">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e000c-226">VIEW_CATALOG</span></span>|<span data-ttu-id="e000c-227">1</span><span class="sxs-lookup"><span data-stu-id="e000c-227">1</span></span>|  
|<span data-ttu-id="e000c-228">Owner</span><span class="sxs-lookup"><span data-stu-id="e000c-228">Owner</span></span>|@Owner|<span data-ttu-id="e000c-229">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e000c-229">VIEW_SCHEMA</span></span>|<span data-ttu-id="e000c-230">2</span><span class="sxs-lookup"><span data-stu-id="e000c-230">2</span></span>|  
|<span data-ttu-id="e000c-231">テーブル</span><span class="sxs-lookup"><span data-stu-id="e000c-231">Table</span></span>|@Table|<span data-ttu-id="e000c-232">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-232">VIEW_NAME</span></span>|<span data-ttu-id="e000c-233">3</span><span class="sxs-lookup"><span data-stu-id="e000c-233">3</span></span>|  
|<span data-ttu-id="e000c-234">Column</span><span class="sxs-lookup"><span data-stu-id="e000c-234">Column</span></span>|@Column|<span data-ttu-id="e000c-235">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-235">COLUMN_NAME</span></span>|<span data-ttu-id="e000c-236">4</span><span class="sxs-lookup"><span data-stu-id="e000c-236">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="e000c-237">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e000c-237">ProcedureParameters</span></span>  
  
|<span data-ttu-id="e000c-238">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-238">Restriction Name</span></span>|<span data-ttu-id="e000c-239">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-239">Parameter Name</span></span>|<span data-ttu-id="e000c-240">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-240">Restriction Default</span></span>|<span data-ttu-id="e000c-241">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-241">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-242">Catalog</span><span class="sxs-lookup"><span data-stu-id="e000c-242">Catalog</span></span>|@Catalog|<span data-ttu-id="e000c-243">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e000c-243">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="e000c-244">1</span><span class="sxs-lookup"><span data-stu-id="e000c-244">1</span></span>|  
|<span data-ttu-id="e000c-245">Owner</span><span class="sxs-lookup"><span data-stu-id="e000c-245">Owner</span></span>|@Owner|<span data-ttu-id="e000c-246">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e000c-246">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="e000c-247">2</span><span class="sxs-lookup"><span data-stu-id="e000c-247">2</span></span>|  
|<span data-ttu-id="e000c-248">名前</span><span class="sxs-lookup"><span data-stu-id="e000c-248">Name</span></span>|@Name|<span data-ttu-id="e000c-249">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-249">SPECIFIC_NAME</span></span>|<span data-ttu-id="e000c-250">3</span><span class="sxs-lookup"><span data-stu-id="e000c-250">3</span></span>|  
|<span data-ttu-id="e000c-251">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e000c-251">Parameter</span></span>|@Parameter|<span data-ttu-id="e000c-252">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-252">PARAMETER_NAME</span></span>|<span data-ttu-id="e000c-253">4</span><span class="sxs-lookup"><span data-stu-id="e000c-253">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e000c-254">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e000c-254">Procedures</span></span>  
  
|<span data-ttu-id="e000c-255">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-255">Restriction Name</span></span>|<span data-ttu-id="e000c-256">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-256">Parameter Name</span></span>|<span data-ttu-id="e000c-257">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-257">Restriction Default</span></span>|<span data-ttu-id="e000c-258">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-258">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-259">Catalog</span><span class="sxs-lookup"><span data-stu-id="e000c-259">Catalog</span></span>|@Catalog|<span data-ttu-id="e000c-260">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e000c-260">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="e000c-261">1</span><span class="sxs-lookup"><span data-stu-id="e000c-261">1</span></span>|  
|<span data-ttu-id="e000c-262">Owner</span><span class="sxs-lookup"><span data-stu-id="e000c-262">Owner</span></span>|@Owner|<span data-ttu-id="e000c-263">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e000c-263">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="e000c-264">2</span><span class="sxs-lookup"><span data-stu-id="e000c-264">2</span></span>|  
|<span data-ttu-id="e000c-265">名前</span><span class="sxs-lookup"><span data-stu-id="e000c-265">Name</span></span>|@Name|<span data-ttu-id="e000c-266">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-266">SPECIFIC_NAME</span></span>|<span data-ttu-id="e000c-267">3</span><span class="sxs-lookup"><span data-stu-id="e000c-267">3</span></span>|  
|<span data-ttu-id="e000c-268">種類</span><span class="sxs-lookup"><span data-stu-id="e000c-268">Type</span></span>|@Type|<span data-ttu-id="e000c-269">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e000c-269">ROUTINE_TYPE</span></span>|<span data-ttu-id="e000c-270">4</span><span class="sxs-lookup"><span data-stu-id="e000c-270">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="e000c-271">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="e000c-271">IndexColumns</span></span>  
  
|<span data-ttu-id="e000c-272">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-272">Restriction Name</span></span>|<span data-ttu-id="e000c-273">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-273">Parameter Name</span></span>|<span data-ttu-id="e000c-274">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-274">Restriction Default</span></span>|<span data-ttu-id="e000c-275">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-275">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-276">Catalog</span><span class="sxs-lookup"><span data-stu-id="e000c-276">Catalog</span></span>|@Catalog|<span data-ttu-id="e000c-277">db_name()</span><span class="sxs-lookup"><span data-stu-id="e000c-277">db_name()</span></span>|<span data-ttu-id="e000c-278">1</span><span class="sxs-lookup"><span data-stu-id="e000c-278">1</span></span>|  
|<span data-ttu-id="e000c-279">Owner</span><span class="sxs-lookup"><span data-stu-id="e000c-279">Owner</span></span>|@Owner|<span data-ttu-id="e000c-280">user_name()</span><span class="sxs-lookup"><span data-stu-id="e000c-280">user_name()</span></span>|<span data-ttu-id="e000c-281">2</span><span class="sxs-lookup"><span data-stu-id="e000c-281">2</span></span>|  
|<span data-ttu-id="e000c-282">テーブル</span><span class="sxs-lookup"><span data-stu-id="e000c-282">Table</span></span>|@Table|<span data-ttu-id="e000c-283">o.name</span><span class="sxs-lookup"><span data-stu-id="e000c-283">o.name</span></span>|<span data-ttu-id="e000c-284">3</span><span class="sxs-lookup"><span data-stu-id="e000c-284">3</span></span>|  
|<span data-ttu-id="e000c-285">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="e000c-285">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="e000c-286">x.name</span><span class="sxs-lookup"><span data-stu-id="e000c-286">x.name</span></span>|<span data-ttu-id="e000c-287">4</span><span class="sxs-lookup"><span data-stu-id="e000c-287">4</span></span>|  
|<span data-ttu-id="e000c-288">Column</span><span class="sxs-lookup"><span data-stu-id="e000c-288">Column</span></span>|@Column|<span data-ttu-id="e000c-289">c.name</span><span class="sxs-lookup"><span data-stu-id="e000c-289">c.name</span></span>|<span data-ttu-id="e000c-290">5</span><span class="sxs-lookup"><span data-stu-id="e000c-290">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="e000c-291">Indexes</span><span class="sxs-lookup"><span data-stu-id="e000c-291">Indexes</span></span>  
  
|<span data-ttu-id="e000c-292">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-292">Restriction Name</span></span>|<span data-ttu-id="e000c-293">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-293">Parameter Name</span></span>|<span data-ttu-id="e000c-294">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-294">Restriction Default</span></span>|<span data-ttu-id="e000c-295">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-295">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-296">Catalog</span><span class="sxs-lookup"><span data-stu-id="e000c-296">Catalog</span></span>|@Catalog|<span data-ttu-id="e000c-297">db_name()</span><span class="sxs-lookup"><span data-stu-id="e000c-297">db_name()</span></span>|<span data-ttu-id="e000c-298">1</span><span class="sxs-lookup"><span data-stu-id="e000c-298">1</span></span>|  
|<span data-ttu-id="e000c-299">Owner</span><span class="sxs-lookup"><span data-stu-id="e000c-299">Owner</span></span>|@Owner|<span data-ttu-id="e000c-300">user_name()</span><span class="sxs-lookup"><span data-stu-id="e000c-300">user_name()</span></span>|<span data-ttu-id="e000c-301">2</span><span class="sxs-lookup"><span data-stu-id="e000c-301">2</span></span>|  
|<span data-ttu-id="e000c-302">テーブル</span><span class="sxs-lookup"><span data-stu-id="e000c-302">Table</span></span>|@Table|<span data-ttu-id="e000c-303">o.name</span><span class="sxs-lookup"><span data-stu-id="e000c-303">o.name</span></span>|<span data-ttu-id="e000c-304">3</span><span class="sxs-lookup"><span data-stu-id="e000c-304">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="e000c-305">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="e000c-305">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="e000c-306">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-306">Restriction Name</span></span>|<span data-ttu-id="e000c-307">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-307">Parameter Name</span></span>|<span data-ttu-id="e000c-308">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-308">Restriction Default</span></span>|<span data-ttu-id="e000c-309">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-309">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-310">assembly_name</span><span class="sxs-lookup"><span data-stu-id="e000c-310">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="e000c-311">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="e000c-311">assemblies.name</span></span>|<span data-ttu-id="e000c-312">1</span><span class="sxs-lookup"><span data-stu-id="e000c-312">1</span></span>|  
|<span data-ttu-id="e000c-313">udt_name</span><span class="sxs-lookup"><span data-stu-id="e000c-313">udt_name</span></span>|@UDTName|<span data-ttu-id="e000c-314">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="e000c-314">types.assembly_class</span></span>|<span data-ttu-id="e000c-315">2</span><span class="sxs-lookup"><span data-stu-id="e000c-315">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="e000c-316">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="e000c-316">ForeignKeys</span></span>  
  
|<span data-ttu-id="e000c-317">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-317">Restriction Name</span></span>|<span data-ttu-id="e000c-318">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-318">Parameter Name</span></span>|<span data-ttu-id="e000c-319">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-319">Restriction Default</span></span>|<span data-ttu-id="e000c-320">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-320">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-321">Catalog</span><span class="sxs-lookup"><span data-stu-id="e000c-321">Catalog</span></span>|@Catalog|<span data-ttu-id="e000c-322">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e000c-322">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="e000c-323">1</span><span class="sxs-lookup"><span data-stu-id="e000c-323">1</span></span>|  
|<span data-ttu-id="e000c-324">Owner</span><span class="sxs-lookup"><span data-stu-id="e000c-324">Owner</span></span>|@Owner|<span data-ttu-id="e000c-325">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e000c-325">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="e000c-326">2</span><span class="sxs-lookup"><span data-stu-id="e000c-326">2</span></span>|  
|<span data-ttu-id="e000c-327">テーブル</span><span class="sxs-lookup"><span data-stu-id="e000c-327">Table</span></span>|@Table|<span data-ttu-id="e000c-328">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-328">TABLE_NAME</span></span>|<span data-ttu-id="e000c-329">3</span><span class="sxs-lookup"><span data-stu-id="e000c-329">3</span></span>|  
|<span data-ttu-id="e000c-330">名前</span><span class="sxs-lookup"><span data-stu-id="e000c-330">Name</span></span>|@Name|<span data-ttu-id="e000c-331">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-331">CONSTRAINT_NAME</span></span>|<span data-ttu-id="e000c-332">4</span><span class="sxs-lookup"><span data-stu-id="e000c-332">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="e000c-333">SQL Server 2008 スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="e000c-333">SQL Server 2008 Schema Restrictions</span></span>  

 <span data-ttu-id="e000c-334">次の表に、SQL Server 2008 スキーマ コレクションの制限を示します。</span><span class="sxs-lookup"><span data-stu-id="e000c-334">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="e000c-335">これらの制限は、.NET Framework 3.5 SP1 および SQL Server 2008 以降で有効です。</span><span class="sxs-lookup"><span data-stu-id="e000c-335">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="e000c-336">これらの制限は、以前のバージョンの .NET Framework および SQL Server ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e000c-336">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="e000c-337">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="e000c-337">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="e000c-338">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-338">Restriction Name</span></span>|<span data-ttu-id="e000c-339">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-339">Parameter Name</span></span>|<span data-ttu-id="e000c-340">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-340">Restriction Default</span></span>|<span data-ttu-id="e000c-341">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-341">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-342">Catalog</span><span class="sxs-lookup"><span data-stu-id="e000c-342">Catalog</span></span>|@Catalog|<span data-ttu-id="e000c-343">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e000c-343">TABLE_CATALOG</span></span>|<span data-ttu-id="e000c-344">1</span><span class="sxs-lookup"><span data-stu-id="e000c-344">1</span></span>|  
|<span data-ttu-id="e000c-345">Owner</span><span class="sxs-lookup"><span data-stu-id="e000c-345">Owner</span></span>|@Owner|<span data-ttu-id="e000c-346">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e000c-346">TABLE_SCHEMA</span></span>|<span data-ttu-id="e000c-347">2</span><span class="sxs-lookup"><span data-stu-id="e000c-347">2</span></span>|  
|<span data-ttu-id="e000c-348">テーブル</span><span class="sxs-lookup"><span data-stu-id="e000c-348">Table</span></span>|@Table|<span data-ttu-id="e000c-349">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-349">TABLE_NAME</span></span>|<span data-ttu-id="e000c-350">3</span><span class="sxs-lookup"><span data-stu-id="e000c-350">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="e000c-351">AllColumns</span><span class="sxs-lookup"><span data-stu-id="e000c-351">AllColumns</span></span>  
  
|<span data-ttu-id="e000c-352">制限の名前</span><span class="sxs-lookup"><span data-stu-id="e000c-352">Restriction Name</span></span>|<span data-ttu-id="e000c-353">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="e000c-353">Parameter Name</span></span>|<span data-ttu-id="e000c-354">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="e000c-354">Restriction Default</span></span>|<span data-ttu-id="e000c-355">制限の番号</span><span class="sxs-lookup"><span data-stu-id="e000c-355">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e000c-356">Catalog</span><span class="sxs-lookup"><span data-stu-id="e000c-356">Catalog</span></span>|@Catalog|<span data-ttu-id="e000c-357">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e000c-357">TABLE_CATALOG</span></span>|<span data-ttu-id="e000c-358">1</span><span class="sxs-lookup"><span data-stu-id="e000c-358">1</span></span>|  
|<span data-ttu-id="e000c-359">Owner</span><span class="sxs-lookup"><span data-stu-id="e000c-359">Owner</span></span>|@Owner|<span data-ttu-id="e000c-360">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e000c-360">TABLE_SCHEMA</span></span>|<span data-ttu-id="e000c-361">2</span><span class="sxs-lookup"><span data-stu-id="e000c-361">2</span></span>|  
|<span data-ttu-id="e000c-362">テーブル</span><span class="sxs-lookup"><span data-stu-id="e000c-362">Table</span></span>|@Table|<span data-ttu-id="e000c-363">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-363">TABLE_NAME</span></span>|<span data-ttu-id="e000c-364">3</span><span class="sxs-lookup"><span data-stu-id="e000c-364">3</span></span>|  
|<span data-ttu-id="e000c-365">Column</span><span class="sxs-lookup"><span data-stu-id="e000c-365">Column</span></span>|@Column|<span data-ttu-id="e000c-366">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e000c-366">COLUMN_NAME</span></span>|<span data-ttu-id="e000c-367">4</span><span class="sxs-lookup"><span data-stu-id="e000c-367">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e000c-368">関連項目</span><span class="sxs-lookup"><span data-stu-id="e000c-368">See also</span></span>

- [<span data-ttu-id="e000c-369">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="e000c-369">ADO.NET Overview</span></span>](ado-net-overview.md)

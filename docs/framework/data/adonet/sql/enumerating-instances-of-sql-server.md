---
description: '詳細情報: SQL Server のインスタンスの列挙 (ADO.NET)'
title: SQL Server のインスタンスの列挙
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: dd52142a06d5c7203eb8a2a14d0e6fc48f1e2a27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672310"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="3813f-103">SQL Server のインスタンスの列挙 (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3813f-103">Enumerating Instances of SQL Server (ADO.NET)</span></span>

<span data-ttu-id="3813f-104">SQL Server では、アプリケーションが現在のネットワーク内の SQL Server インスタンスを検索できます。</span><span class="sxs-lookup"><span data-stu-id="3813f-104">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="3813f-105"><xref:System.Data.Sql.SqlDataSourceEnumerator> クラスは、この情報をアプリケーション開発者に公開し、表示されるすべてのサーバーに関する情報を含む <xref:System.Data.DataTable> を提供します。</span><span class="sxs-lookup"><span data-stu-id="3813f-105">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="3813f-106">このときに返されるテーブルには、ユーザーが新しい接続を作成しようとして、 **[接続プロパティ]** ダイアログ ボックスで、利用可能なすべてのサーバーが含まれたドロップダウン リストを展開したときに表示されるリストと一致するサーバー インスタンスのリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3813f-106">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="3813f-107">表示される結果が完全なものであるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="3813f-107">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3813f-108">ほとんどの Windows サービスと同様に、SQL Browser サービスは必要最小限の特権で実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3813f-108">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="3813f-109">SQL Browser サービスの詳細および SQL Browser サービスの動作を管理する方法については、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3813f-109">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="3813f-110">列挙子インスタンスの取得</span><span class="sxs-lookup"><span data-stu-id="3813f-110">Retrieving an Enumerator Instance</span></span>  

 <span data-ttu-id="3813f-111">使用可能な SQL Server インスタンスに関する情報が含まれたテーブルを取得するには、まず、共有プロパティまたは静的プロパティである <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> プロパティを使用して列挙子を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3813f-111">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="3813f-112">静的インスタンスを取得したら、使用可能なサーバーに関する情報を含む <xref:System.Data.DataTable> を返す <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="3813f-112">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="3813f-113">このメソッド呼び出しから返されるテーブルには次の列が含まれ、そのすべてに `string` 値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3813f-113">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="3813f-114">Column</span><span class="sxs-lookup"><span data-stu-id="3813f-114">Column</span></span>|<span data-ttu-id="3813f-115">説明</span><span class="sxs-lookup"><span data-stu-id="3813f-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3813f-116">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="3813f-116">**ServerName**</span></span>|<span data-ttu-id="3813f-117">サーバーの名前。</span><span class="sxs-lookup"><span data-stu-id="3813f-117">Name of the server.</span></span>|  
|<span data-ttu-id="3813f-118">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="3813f-118">**InstanceName**</span></span>|<span data-ttu-id="3813f-119">サーバー インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="3813f-119">Name of the server instance.</span></span> <span data-ttu-id="3813f-120">サーバーが既定のインスタンスとして実行されている場合は空白です。</span><span class="sxs-lookup"><span data-stu-id="3813f-120">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="3813f-121">**IsClustered**</span><span class="sxs-lookup"><span data-stu-id="3813f-121">**IsClustered**</span></span>|<span data-ttu-id="3813f-122">サーバーがクラスターの一部であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="3813f-122">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="3813f-123">**Version**</span><span class="sxs-lookup"><span data-stu-id="3813f-123">**Version**</span></span>|<span data-ttu-id="3813f-124">サーバーのバージョン。</span><span class="sxs-lookup"><span data-stu-id="3813f-124">Version of the server.</span></span> <span data-ttu-id="3813f-125">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="3813f-125">For example:</span></span><br /><br /> <span data-ttu-id="3813f-126">-   9.00.x (SQL Server 2005)</span><span class="sxs-lookup"><span data-stu-id="3813f-126">-   9.00.x (SQL Server 2005)</span></span><br /><span data-ttu-id="3813f-127">-10.0.xx (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="3813f-127">-   10.0.xx (SQL Server 2008)</span></span><br /><span data-ttu-id="3813f-128">-   10.50.x (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="3813f-128">-   10.50.x (SQL Server 2008 R2)</span></span><br /><span data-ttu-id="3813f-129">-11.0.xx (SQL Server 2012)</span><span class="sxs-lookup"><span data-stu-id="3813f-129">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="3813f-130">列挙の制約</span><span class="sxs-lookup"><span data-stu-id="3813f-130">Enumeration Limitations</span></span>  

 <span data-ttu-id="3813f-131">使用可能なサーバーの一部が表示されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="3813f-131">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="3813f-132">この一覧は、タイムアウトやネットワーク トラフィックなどの要因によって異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="3813f-132">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="3813f-133">このため、2 回の連続呼び出しで一覧が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3813f-133">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="3813f-134">同じネットワーク上のサーバーのみが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="3813f-134">Only servers on the same network will be listed.</span></span> <span data-ttu-id="3813f-135">ブロードキャスト パケットは通常、ルーターをスキャンしません。あるサーバーが一覧表示されないことがあっても、複数の呼び出し間で安定しているのはこのためです。</span><span class="sxs-lookup"><span data-stu-id="3813f-135">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="3813f-136">一覧表示されたサーバーに、常に `IsClustered` やバージョンなどの追加情報があるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="3813f-136">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="3813f-137">これは、その一覧がどのように取得されたかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="3813f-137">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="3813f-138">SQL Server ブラウザー サービスを介して一覧表示されるサーバーには、名前しか一覧表示しない Windows インフラストラクチャを介して検索されたサーバーより多くの詳細情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3813f-138">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3813f-139">サーバーの列挙は、完全に信頼され、実行されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3813f-139">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="3813f-140">部分的に信頼された環境で実行されているアセンブリは、<xref:System.Data.SqlClient.SqlClientPermission> コード アクセス セキュリティ (CAS) アクセス許可がある場合でも使用できません。</span><span class="sxs-lookup"><span data-stu-id="3813f-140">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="3813f-141">SQL Server では、SQL Browser という名前の外部の Windows サービスを利用して、<xref:System.Data.Sql.SqlDataSourceEnumerator> に情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="3813f-141">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="3813f-142">このサービスは既定で有効になっていますが、管理者はそれをオフにするか、無効にして、サーバー インスタンスをこのクラスに表示しないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="3813f-142">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3813f-143">例</span><span class="sxs-lookup"><span data-stu-id="3813f-143">Example</span></span>  

 <span data-ttu-id="3813f-144">次のコンソール アプリケーションは、表示可能なすべての SQL Server インスタンスに関する情報を取得し、コンソール ウィンドウにその情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="3813f-144">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
```vb  
Imports System.Data.Sql  
  
Module Module1  
  Sub Main()  
    ' Retrieve the enumerator instance and then the data.  
    Dim instance As SqlDataSourceEnumerator = _  
     SqlDataSourceEnumerator.Instance  
    Dim table As System.Data.DataTable = instance.GetDataSources()  
  
    ' Display the contents of the table.  
    DisplayData(table)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Sub  
  
  Private Sub DisplayData(ByVal table As DataTable)  
    For Each row As DataRow In table.Rows  
      For Each col As DataColumn In table.Columns  
        Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
      Next  
      Console.WriteLine("============================")  
    Next  
  End Sub  
End Module  
```  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
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
  
## <a name="see-also"></a><span data-ttu-id="3813f-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="3813f-145">See also</span></span>

- [<span data-ttu-id="3813f-146">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3813f-146">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="3813f-147">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="3813f-147">ADO.NET Overview</span></span>](../ado-net-overview.md)

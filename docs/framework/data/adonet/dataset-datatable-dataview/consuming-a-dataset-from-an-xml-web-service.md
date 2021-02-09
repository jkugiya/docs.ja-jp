---
description: '詳細情報: XML Web サービスからの DataSet の使用'
title: XML Web サービスからの DataSet の使用
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: 3c9112d259d5a6450a968ba87b33c4072f6dc44c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725130"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="3648e-103">XML Web サービスからの DataSet の使用</span><span class="sxs-lookup"><span data-stu-id="3648e-103">Consume a DataSet from an XML web service</span></span>

<span data-ttu-id="3648e-104"><xref:System.Data.DataSet> は、非接続型デザインで設計されています。インターネットで簡単にデータを転送するのが目的の一部です。</span><span class="sxs-lookup"><span data-stu-id="3648e-104">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="3648e-105">**DataSet** は、**DataSet** の内容を XML Web サービスからクライアントに (およびその逆方向に) ストリーム転送するためのコードを追加せずに XML Web サービスへの入力または出力として指定できるという点で、"シリアル化可能" です。</span><span class="sxs-lookup"><span data-stu-id="3648e-105">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="3648e-106">**DataSet** は、DiffGram 形式を使用して暗黙に XML ストリームに変換され、ネットワーク経由で送信されます。その後、受信側で XML ストリームから **DataSet** として再構築されます。</span><span class="sxs-lookup"><span data-stu-id="3648e-106">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="3648e-107">これにより、XML Web サービスを使用してリレーショナル データを送信および返送する、簡単で柔軟性のある方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="3648e-107">This gives you a simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="3648e-108">DiffGram 形式の詳細については、「[DiffGrams](diffgrams.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3648e-108">For more information about the DiffGram format, see [DiffGrams](diffgrams.md).</span></span>  
  
 <span data-ttu-id="3648e-109">**DataSet** を使用してリレーショナル データ (変更データを含む) を転送し、更新内容を元のデータ ソースに反映させる XML Web サービスと XML Web サービスのクライアントを作成する手順を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="3648e-109">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3648e-110">入力が信頼されていない場合、XML Web サービスの呼び出しの一部として `DataSet` または `DataTable` のインスタンスを送信することは安全ではありません。</span><span class="sxs-lookup"><span data-stu-id="3648e-110">Transmitting `DataSet` or `DataTable` instances as part of XML Web service calls is not safe if the input is not trusted.</span></span> <span data-ttu-id="3648e-111">詳細については、「[DataSet と DataTable のセキュリティ ガイダンス](security-guidance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3648e-111">For more information, see [DataSet and DataTable security guidance](security-guidance.md).</span></span>
> <span data-ttu-id="3648e-112">XML Web サービスを作成する場合は、常にセキュリティへの影響を考慮することもお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3648e-112">We also recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="3648e-113">XML Web サービスのセキュリティ保護については、「[ASP.NET を使用して作成した XML Web サービスのセキュリティ](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3648e-113">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span></span>  
  
## <a name="create-an-xml-web-service"></a><span data-ttu-id="3648e-114">XML Web サービスの作成</span><span class="sxs-lookup"><span data-stu-id="3648e-114">Create an XML web service</span></span>
  
1. <span data-ttu-id="3648e-115">XML Web サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3648e-115">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="3648e-116">この例では、データ (ここでは、**Northwind** データベースの顧客リスト) を返し、元のデータ ソースに反映させるデータ更新が格納されている **DataSet** を受け取る XML Web サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3648e-116">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="3648e-117">この XML Web サービスでは 2 つのメソッドが公開されています。顧客リストを返す **GetCustomers** と、更新をデータ ソースに反映させる **UpdateCustomers** です。</span><span class="sxs-lookup"><span data-stu-id="3648e-117">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="3648e-118">この XML Web サービスは、Web サーバー上の DataSetSample.asmx というファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3648e-118">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="3648e-119">次のコードは、DataSetSample.asmx の内容の概要を示しています。</span><span class="sxs-lookup"><span data-stu-id="3648e-119">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
    ```vb  
    <% @ WebService Language = "vb" Class = "Sample" %>  
    Imports System  
    Imports System.Data  
    Imports System.Data.SqlClient  
    Imports System.Web.Services  
  
    <WebService(Namespace:="http://microsoft.com/webservices/")> _  
    Public Class Sample  
  
    Public connection As SqlConnection = New SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind")  
  
      <WebMethod( Description := "Returns Northwind Customers", EnableSession := False )> _  
      Public Function GetCustomers() As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
          "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
        Dim custDS As DataSet = New DataSet()  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
        adapter.Fill(custDS, "Customers")  
  
        Return custDS  
      End Function  
  
      <WebMethod( Description := "Updates Northwind Customers", EnableSession := False )> _  
      Public Function UpdateCustomers(custDS As DataSet) As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter()  
  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Customers (CustomerID, CompanyName) " & _  
          "Values(@CustomerID, @CompanyName)", connection)  
        adapter.InsertCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.InsertCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Customers Set CustomerID = @CustomerID, " & _  
          "CompanyName = @CompanyName WHERE CustomerID = " & _  
          @OldCustomerID", connection)  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        Dim parameter As SqlParameter = _  
          adapter.UpdateCommand.Parameters.Add( _  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Customers WHERE CustomerID = @CustomerID", _  
          connection)  
        parameter = adapter.DeleteCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.Update(custDS, "Customers")  
  
        Return custDS  
      End Function  
    End Class  
    ```  
  
    ```csharp  
    <% @ WebService Language = "C#" Class = "Sample" %>  
    using System;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Web.Services;  
  
    [WebService(Namespace="http://microsoft.com/webservices/")]  
    public class Sample  
    {  
      public SqlConnection connection = new SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind");  
  
      [WebMethod( Description = "Returns Northwind Customers", EnableSession = false )]  
      public DataSet GetCustomers()  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter(  
          "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
        DataSet custDS = new DataSet();  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
        adapter.Fill(custDS, "Customers");  
  
        return custDS;  
      }  
  
      [WebMethod( Description = "Updates Northwind Customers",  
        EnableSession = false )]  
      public DataSet UpdateCustomers(DataSet custDS)  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        adapter.InsertCommand = new SqlCommand(  
          "INSERT INTO Customers (CustomerID, CompanyName) " +  
          "Values(@CustomerID, @CompanyName)", connection);  
        adapter.InsertCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.InsertCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
  
        adapter.UpdateCommand = new SqlCommand(  
          "UPDATE Customers Set CustomerID = @CustomerID, " +  
          "CompanyName = @CompanyName WHERE CustomerID = " +  
          "@OldCustomerID", connection);  
        adapter.UpdateCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.UpdateCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
        SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.DeleteCommand = new SqlCommand(  
        "DELETE FROM Customers WHERE CustomerID = @CustomerID",  
         connection);  
        parameter = adapter.DeleteCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.Update(custDS, "Customers");  
  
        return custDS;  
      }  
    }  
    ```  
  
     <span data-ttu-id="3648e-120">代表的なシナリオでは、**UpdateCustomers** メソッドはオプティミスティック コンカレンシー違反をキャッチするように記述されます。</span><span class="sxs-lookup"><span data-stu-id="3648e-120">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="3648e-121">説明を簡単にするために、この例では UpdateCustmoers メソッドを省略しています。</span><span class="sxs-lookup"><span data-stu-id="3648e-121">For simplicity, the example does not include this.</span></span> <span data-ttu-id="3648e-122">オプティミスティック コンカレンシーについて詳しくは、「[オプティミスティック コンカレンシー](../optimistic-concurrency.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3648e-122">For more information about optimistic concurrency, see [Optimistic Concurrency](../optimistic-concurrency.md).</span></span>  
  
2. <span data-ttu-id="3648e-123">XML Web サービス プロキシを作成します。</span><span class="sxs-lookup"><span data-stu-id="3648e-123">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="3648e-124">XML Web サービスのクライアントは、公開されたメソッドを使用するために SOAP プロキシを必要とします。</span><span class="sxs-lookup"><span data-stu-id="3648e-124">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="3648e-125">このプロキシは、Visual Studio を使用して生成することができます。</span><span class="sxs-lookup"><span data-stu-id="3648e-125">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="3648e-126">Visual Studio から既存の Web サービスへの Web 参照を設定することにより、この手順で説明されているすべての動作が自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="3648e-126">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="3648e-127">プロキシ クラスを手動で作成する場合は、後述の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3648e-127">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="3648e-128">ほとんどの場合、Visual Studio による、クライアント アプリケーションのプロキシ クラスの作成で十分です。</span><span class="sxs-lookup"><span data-stu-id="3648e-128">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="3648e-129">プロキシは、Web サービス記述言語ツールを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="3648e-129">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="3648e-130">たとえば、XML Web サービスを `http://myserver/data/DataSetSample.asmx` の URL に公開する場合は、次のようなコマンドを実行して、名前空間 **WebData.DSSample** を指定した Visual Basic .NET プロキシを作成し、それをファイル sample.vb に格納します。</span><span class="sxs-lookup"><span data-stu-id="3648e-130">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="3648e-131">ファイル sample.cs に C# プロキシを作成するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3648e-131">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="3648e-132">その後、プロキシをライブラリとしてコンパイルし、XML Web サービスのクライアントにインポートします。</span><span class="sxs-lookup"><span data-stu-id="3648e-132">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="3648e-133">sample.vb に格納されている Visual Basic .NET プロキシ コードを sample.dll としてコンパイルするには次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3648e-133">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="3648e-134">sample.cs に格納されている C# プロキシ コードを sample.dll としてコンパイルするには次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3648e-134">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. <span data-ttu-id="3648e-135">XML Web サービスのクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="3648e-135">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="3648e-136">Visual Studio で Web サービスのプロキシ クラスを生成する場合は、クライアント プロジェクトを作成し、ソリューション エクスプローラー ウィンドウで、そのプロジェクトを右クリックし、 **[追加]**  >  **[サービス参照]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3648e-136">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, and then select **Add** > **Service Reference**.</span></span> <span data-ttu-id="3648e-137">**[サービス参照の追加]** ダイアログ ボックスで、 **[詳細設定]** を選択し、 **[Web 参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3648e-137">In the **Add Service Reference** dialog box, select **Advanced**, and then select **Add Web Reference**.</span></span> <span data-ttu-id="3648e-138">使用可能な Web サービスの一覧から Web サービスを選択します (ただし、Web サービスが現行ソリューション内または現在のコンピューター上で使用できない場合は、Web サービス エンドポイントのアドレスを指定する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="3648e-138">Select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint if the Web service isn't available within the current solution or on the current computer).</span></span> <span data-ttu-id="3648e-139">(上記の手順に従って) XML Web サービス プロキシを作成した場合は、それをクライアント コードにインポートし、XML Web サービスのメソッドを処理できます。</span><span class="sxs-lookup"><span data-stu-id="3648e-139">If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span>

     <span data-ttu-id="3648e-140">プロキシ ライブラリをインポートし、**GetCustomers** を呼び出して顧客リストを取得し、新しい顧客を追加した後、更新内容が格納された **DataSet** を **UpdateCustomers** に返すサンプル コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3648e-140">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="3648e-141">この例では、変更された行だけを **UpdateCustomers** に渡す必要があるため、**UpdateCustomers** には、**DataSet.GetChanges** によって返された **DataSet** が渡されます。</span><span class="sxs-lookup"><span data-stu-id="3648e-141">The example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="3648e-142">**UpdateCustomers** は解決された **DataSet** を返します。その後、この DataSet を既存の **DataSet** に **Merge** して、解決された変更と更新からの行エラー情報を取り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="3648e-142">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="3648e-143">次のコードは、Visual Studio を使用して Web 参照が作成済みで、かつ、 **[Web 参照の追加]** ダイアログ ボックスでその Web 参照の名前が DsSample に変更済みであることが前提となっています。</span><span class="sxs-lookup"><span data-stu-id="3648e-143">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
    ```vb  
    Imports System  
    Imports System.Data  
  
    Public Class Client  
  
      Public Shared Sub Main()  
        Dim proxySample As New DsSample.Sample ()  ' Proxy object.  
        Dim customersDataSet As DataSet = proxySample.GetCustomers()  
        Dim customersTable As DataTable = _  
          customersDataSet.Tables("Customers")  
  
        Dim rowAs DataRow = customersTable.NewRow()  
        row("CustomerID") = "ABCDE"  
        row("CompanyName") = "New Company Name"  
        customersTable.Rows.Add(row)  
  
        Dim updateDataSet As DataSet = _  
          proxySample.UpdateCustomers(customersDataSet.GetChanges())  
  
        customersDataSet.Merge(updateDataSet)  
        customersDataSet.AcceptChanges()  
      End Sub  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using System.Data;  
  
    public class Client  
    {  
      public static void Main()  
      {  
        Sample proxySample = new DsSample.Sample();  // Proxy object.  
        DataSet customersDataSet = proxySample.GetCustomers();  
        DataTable customersTable = customersDataSet.Tables["Customers"];  
  
        DataRow row = customersTable.NewRow();  
        row["CustomerID"] = "ABCDE";  
        row["CompanyName"] = "New Company Name";  
        customersTable.Rows.Add(row);  
  
        DataSet updateDataSet = new DataSet();  
  
        updateDataSet =
          proxySample.UpdateCustomers(customersDataSet.GetChanges());  
  
        customersDataSet.Merge(updateDataSet);  
        customersDataSet.AcceptChanges();  
      }  
    }  
    ```  
  
     <span data-ttu-id="3648e-144">プロキシ クラスを手動で作成する場合は、次の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="3648e-144">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="3648e-145">このサンプルをコンパイルするには、作成したプロキシ ライブラリ (sample.dll) および関連する .NET ライブラリを指定します。</span><span class="sxs-lookup"><span data-stu-id="3648e-145">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="3648e-146">ファイル client.vb に格納されている Visual Basic .NET バージョンのサンプルをコンパイルするには次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3648e-146">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="3648e-147">ファイル client.cs に格納されている C# バージョンのサンプルをコンパイルするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3648e-147">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3648e-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="3648e-148">See also</span></span>

- [<span data-ttu-id="3648e-149">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3648e-149">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="3648e-150">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="3648e-150">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="3648e-151">DataTables</span><span class="sxs-lookup"><span data-stu-id="3648e-151">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="3648e-152">DataAdapter からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="3648e-152">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="3648e-153">DataAdapter によるデータ ソースの更新</span><span class="sxs-lookup"><span data-stu-id="3648e-153">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="3648e-154">DataAdapter パラメーター</span><span class="sxs-lookup"><span data-stu-id="3648e-154">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- <span data-ttu-id="3648e-155">[Web サービス記述言語ツール (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3648e-155">[Web Services Description Language Tool (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span></span>
- [<span data-ttu-id="3648e-156">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="3648e-156">ADO.NET Overview</span></span>](../ado-net-overview.md)

---
description: '詳細については、「方法: WCF サービスおよびクライアントにプログラムによって探索可能な情報を追加する」を参照してください。'
title: '方法: プログラムを使用して探索可能性に WCF サービスとクライアントを追加する'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: ad192c6fcc57a36d7001f230c98b1193c42262aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793715"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="2b0ed-103">方法: プログラムを使用して探索可能性に WCF サービスとクライアントを追加する</span><span class="sxs-lookup"><span data-stu-id="2b0ed-103">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>

<span data-ttu-id="2b0ed-104">このトピックでは、Windows Communication Foundation (WCF) サービスを探索可能にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-104">This topic explains how to make a Windows Communication Foundation (WCF) service discoverable.</span></span> <span data-ttu-id="2b0ed-105">これは、 [自己ホスト](../samples/self-host.md) のサンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-105">It is based on the [Self-Host](../samples/self-host.md) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="2b0ed-106">既存の自己ホスト サービス サンプルを探索用に構成するには</span><span class="sxs-lookup"><span data-stu-id="2b0ed-106">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1. <span data-ttu-id="2b0ed-107">Visual Studio 2012 で Self-Host ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-107">Open the Self-Host solution in Visual Studio 2012.</span></span> <span data-ttu-id="2b0ed-108">このサンプルは、TechnologySamples\Basic\Service\Hosting\SelfHost ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-108">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2. <span data-ttu-id="2b0ed-109">`System.ServiceModel.Discovery.dll` への参照をサービス プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-109">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="2b0ed-110">"システム" というエラーメッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-110">You may see an error message saying "System.</span></span> <span data-ttu-id="2b0ed-111">ServiceModel.Discovery.dll またはその依存関係の1つには、プロジェクトで指定されているものより新しいバージョンの .NET Framework が必要です。 "このメッセージが表示された場合は、ソリューションエクスプローラーでプロジェクトを右クリックし、[ **プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-111">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the .NET Framework than the one specified in the project …" If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="2b0ed-112">プロジェクトの **プロパティ** ウィンドウで、 **ターゲットフレームワーク** がになっていることを確認し [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-112">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3. <span data-ttu-id="2b0ed-113">Service.cs ファイルを開き、次の `using` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-113">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. <span data-ttu-id="2b0ed-114">`Main()` メソッドの `using` ステート内で、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> インスタンスをサービス ホストに追加します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-114">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
        {  
            // Add a ServiceDiscoveryBehavior  
            serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());
  
            // ...  
        }  
    }  
    ```  
  
     <span data-ttu-id="2b0ed-115"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> は、それが適用されているサービスが探索可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-115">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5. <span data-ttu-id="2b0ed-116"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> を、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> を追加するコードの直後でサービス ホストに追加します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-116">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="2b0ed-117">このコードは、探索メッセージを標準の UDP 探索エンドポイントに送信する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-117">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="2b0ed-118">探索を使用してサービスを呼び出すクライアント アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="2b0ed-118">To create a client application that uses discovery to call the service</span></span>  
  
1. <span data-ttu-id="2b0ed-119">新しいコンソール アプリケーションを `DiscoveryClientApp` というソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-119">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2. <span data-ttu-id="2b0ed-120">`System.ServiceModel.dll` および `System.ServiceModel.Discovery.dll` への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-120">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3. <span data-ttu-id="2b0ed-121">GeneratedClient.cs ファイルおよび App.config ファイルを、既存のクライアント プロジェクトから新しい DiscoveryClientApp プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-121">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="2b0ed-122">これを行うには、 **ソリューションエクスプローラー** 内のファイルを右クリックし、[ **コピー**] を選択します。次に、 **DiscoveryClientApp** プロジェクトを選択して右クリックし、[ **貼り付け**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-122">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4. <span data-ttu-id="2b0ed-123">Program.cs を開きます。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-123">Open Program.cs.</span></span>  
  
5. <span data-ttu-id="2b0ed-124">次の `using` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-124">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. <span data-ttu-id="2b0ed-125">`FindCalculatorServiceAddress()` という静的メソッドを `Program` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-125">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="2b0ed-126">このメソッドは、探索を使用して `CalculatorService` サービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-126">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7. <span data-ttu-id="2b0ed-127">`FindCalculatorServiceAddress` メソッド内で、新しい <xref:System.ServiceModel.Discovery.DiscoveryClient> インスタンスを作成し、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> をコンストラクターに渡します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-127">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="2b0ed-128">これにより、クラスは、 <xref:System.ServiceModel.Discovery.DiscoveryClient> 標準の UDP 探索エンドポイントを使用して探索メッセージの送受信を行う必要があることが WCF に通知されます。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-128">This tells WCF that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8. <span data-ttu-id="2b0ed-129">次の行では、<xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> メソッドを呼び出し、検索対象のサービス コントラクトを含む <xref:System.ServiceModel.Discovery.FindCriteria> インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-129">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="2b0ed-130">ここでは、`ICalculator` を指定します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-130">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="2b0ed-131"><xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> への呼び出しの後で、一致するサービスが少なくとも 1 つあるかどうかを確認し、最初に一致したサービスの <xref:System.ServiceModel.EndpointAddress> を返します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-131">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="2b0ed-132">一致するサービスがない場合は `null` を返します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-132">Otherwise return `null`.</span></span>  
  
    ```csharp  
    if (findResponse.Endpoints.Count > 0)  
    {  
        return findResponse.Endpoints[0].Address;  
    }  
    else  
    {  
        return null;  
    }  
    ```  
  
10. <span data-ttu-id="2b0ed-133">`InvokeCalculatorService` という名前の静的メソッドを `Program` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-133">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="2b0ed-134">このメソッドは、`FindCalculatorServiceAddress` から返されたエンドポイント アドレスを使用して、電卓サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-134">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="2b0ed-135">`InvokeCalculatorService` メソッド内で、`CalculatorServiceClient` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-135">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="2b0ed-136">このクラスは、 [自己ホスト](../samples/self-host.md) のサンプルで定義されています。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-136">This class is defined by the [Self-Host](../samples/self-host.md) sample.</span></span> <span data-ttu-id="2b0ed-137">これは、Svcutil.exe を使用して生成されました。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-137">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="2b0ed-138">次の行では、クライアントのエンドポイント アドレスを、`FindCalculatorServiceAddress()` から返されたエンドポイント アドレスに設定します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-138">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="2b0ed-139">前の手順のコードの直後に、電卓サービスで公開されたメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-139">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
    ```csharp  
    Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
  
    // Call the Add service operation.  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    Console.WriteLine();  
  
    //Closing the client gracefully closes the connection and cleans up resources  
    client.Close();  
    ```  
  
14. <span data-ttu-id="2b0ed-140">`Main()` クラスの `Program` メソッドにコードを追加して、`FindCalculatorServiceAddress` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-140">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="2b0ed-141">次の行では、`InvokeCalculatorService()` を呼び出し、`FindCalculatorServiceAddress()` から返されたエンドポイント アドレスを渡します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-141">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="2b0ed-142">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="2b0ed-142">To test the application</span></span>  
  
1. <span data-ttu-id="2b0ed-143">権限のレベルが高いコマンド プロンプトを開き、Service.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-143">Open an elevated command prompt and run Service.exe.</span></span>  
  
2. <span data-ttu-id="2b0ed-144">コマンド プロンプトを開き、Discoveryclientapp.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-144">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3. <span data-ttu-id="2b0ed-145">Service.exe からの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-145">The output from service.exe should look like the following output.</span></span>  
  
    ```output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4. <span data-ttu-id="2b0ed-146">Discoveryclientapp.exe からの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-146">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="2b0ed-147">例</span><span class="sxs-lookup"><span data-stu-id="2b0ed-147">Example</span></span>  

 <span data-ttu-id="2b0ed-148">このサンプルで使用されているコード全体の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-148">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="2b0ed-149">このコードは [自己ホスト](../samples/self-host.md) のサンプルに基づいているため、変更されたファイルのみが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-149">Because this code is based on the [Self-Host](../samples/self-host.md) sample, only those files that are changed are listed.</span></span> <span data-ttu-id="2b0ed-150">Self-Host サンプルの詳細については、「 [セットアップ手順](../samples/set-up-instructions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b0ed-150">For more information about the Self-Host sample, see [Setup Instructions](../samples/set-up-instructions.md).</span></span>  
  
```csharp  
// Service.cs  
using System;  
using System.Configuration;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.ServiceModel.Samples  
{  
    // See SelfHost sample for service contract and implementation  
    // ...  
  
        // Host the service within this EXE console application.  
        public static void Main()  
        {  
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
            {  
                // Add the ServiceDiscoveryBehavior to make the service discoverable  
                serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
                serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
                // Open the ServiceHost to create listeners and start listening for messages.  
                serviceHost.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
            }  
        }  
    }  
}  
```  
  
```csharp  
// Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
using Microsoft.ServiceModel.Samples;  
using System.Text;  
  
namespace DiscoveryClientApp  
{  
    class Program  
    {  
        static EndpointAddress FindCalculatorServiceAddress()  
        {  
            // Create DiscoveryClient  
            DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
            // Find ICalculatorService endpoints
            FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
  
            if (findResponse.Endpoints.Count > 0)  
            {  
                return findResponse.Endpoints[0].Address;  
            }  
            else  
            {  
                return null;  
            }  
        }  
  
        static void InvokeCalculatorService(EndpointAddress endpointAddress)  
        {  
            // Create a client  
            CalculatorClient client = new CalculatorClient();  
  
            // Connect to the discovered service endpoint  
            client.Endpoint.Address = endpointAddress;  
  
            Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
  
            // Call the Add service operation.  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
            Console.WriteLine();  
  
            //Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
        }  
        static void Main(string[] args)  
        {  
            EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
  
            if (endpointAddress != null)  
            {  
                InvokeCalculatorService(endpointAddress);  
            }  
  
            Console.WriteLine("Press <ENTER> to exit.");  
            Console.ReadLine();  
  
        }  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="2b0ed-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b0ed-151">See also</span></span>

- [<span data-ttu-id="2b0ed-152">WCF Discovery の概要</span><span class="sxs-lookup"><span data-stu-id="2b0ed-152">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="2b0ed-153">WCF Discovery オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="2b0ed-153">WCF Discovery Object Model</span></span>](wcf-discovery-object-model.md)

---
description: '詳細については、「方法: 探索プロキシに登録する探索可能なサービスを実装する」を参照してください。'
title: '方法: 探索プロキシで登録される探索可能なサービスの実装する'
ms.date: 03/30/2017
ms.assetid: eb275bc1-535b-44c8-b9f3-0b75e9aa473b
ms.openlocfilehash: 71991de6b7fd0180d4f87c2bfc48e99dc398fa53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802958"
---
# <a name="how-to-implement-a-discoverable-service-that-registers-with-the-discovery-proxy"></a><span data-ttu-id="32010-103">方法: 探索プロキシで登録される探索可能なサービスの実装する</span><span class="sxs-lookup"><span data-stu-id="32010-103">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>

<span data-ttu-id="32010-104">これは、探索プロキシの実装方法に関する 4 つのトピックのうちの 2 番目のトピックです。</span><span class="sxs-lookup"><span data-stu-id="32010-104">This topic is the second of four topics that discusses how to implement a discovery proxy.</span></span> <span data-ttu-id="32010-105">前のトピック「 [方法: 探索プロキシを実装](how-to-implement-a-discovery-proxy.md)する」では、探索プロキシを実装しています。</span><span class="sxs-lookup"><span data-stu-id="32010-105">In the previous topic, [How to: Implement a Discovery Proxy](how-to-implement-a-discovery-proxy.md), you implemented a discovery proxy.</span></span> <span data-ttu-id="32010-106">このトピックでは、アナウンスメッセージ (および) を探索プロキシに送信する WCF サービスを作成し `Hello` `Bye` ます。これにより、探索プロキシに登録および登録解除が行われます。</span><span class="sxs-lookup"><span data-stu-id="32010-106">In this topic, you create a WCF service that sends announcement messages (`Hello` and `Bye`) to the discovery proxy, causing it to register and unregister itself with the discovery proxy.</span></span>

### <a name="to-define-the-service-contract"></a><span data-ttu-id="32010-107">サービス コントラクトを定義するには</span><span class="sxs-lookup"><span data-stu-id="32010-107">To define the service contract</span></span>

1. <span data-ttu-id="32010-108">新しいコンソール アプリケーション プロジェクトを、`DiscoveryProxyExample` という `Service` ソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="32010-108">Add a new console application project to the `DiscoveryProxyExample` solution called `Service`.</span></span>

2. <span data-ttu-id="32010-109">次のアセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="32010-109">Add references to the following assemblies:</span></span>

    1. <span data-ttu-id="32010-110">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="32010-110">System.ServiceModel</span></span>

    2. <span data-ttu-id="32010-111">System.ServiceModel.Discovery</span><span class="sxs-lookup"><span data-stu-id="32010-111">System.ServiceModel.Discovery</span></span>

3. <span data-ttu-id="32010-112">新しいクラスを `CalculatorService` プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="32010-112">Add a new class to the project called `CalculatorService`.</span></span>

4. <span data-ttu-id="32010-113">次の using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="32010-113">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    ```

5. <span data-ttu-id="32010-114">CalculatorService.cs でサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="32010-114">Within CalculatorService.cs, define the service contract.</span></span>

    ```csharp
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }
    ```

6. <span data-ttu-id="32010-115">また、CalculatorService.cs でサービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="32010-115">Also within CalculatorService.cs, implement the service contract.</span></span>

    ```csharp
    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
    ```

### <a name="to-host-the-service"></a><span data-ttu-id="32010-116">サービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="32010-116">To host the service</span></span>

1. <span data-ttu-id="32010-117">プロジェクトの作成時に生成された Program.cs ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="32010-117">Open the Program.cs file that was generated when you created the project.</span></span>

2. <span data-ttu-id="32010-118">次の using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="32010-118">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="32010-119">`Main()` メソッド内に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="32010-119">Within the `Main()` method, add the following code:</span></span>

    ```csharp
    // Define the base address of the service
    Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
    // Define the endpoint address where announcement messages will be sent
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

    // Create the service host
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
    try
    {
        // Add a service endpoint
        ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
            new NetTcpBinding(), string.Empty);

        // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
        AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
            new EndpointAddress(announcementEndpointAddress));

        // Create a ServiceDiscoveryBehavior and add the announcement endpoint
        ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
        serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

        // Add the ServiceDiscoveryBehavior to the service host to make the service discoverable
        serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

        // Start listening for messages
        serviceHost.Open();

        Console.WriteLine("Calculator Service started at {0}", baseAddress);
        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate the service.");
        Console.WriteLine();
        Console.ReadLine();

        serviceHost.Close();
    }
    catch (CommunicationException e)
    {
        Console.WriteLine(e.Message);
    }
    catch (TimeoutException e)
    {
        Console.WriteLine(e.Message);
    }

    if (serviceHost.State != CommunicationState.Closed)
    {
        Console.WriteLine("Aborting the service...");
        serviceHost.Abort();
    }
    ```

<span data-ttu-id="32010-120">これで、探索サービスの実装が完了しました。</span><span class="sxs-lookup"><span data-stu-id="32010-120">You have completed implementing a discoverable service.</span></span> <span data-ttu-id="32010-121">[「方法: 探索プロキシを使用してサービスを検索するクライアントアプリケーションを実装](client-app-discovery-proxy-to-find-a-service.md)する」に進みます。</span><span class="sxs-lookup"><span data-stu-id="32010-121">Continue on to [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](client-app-discovery-proxy-to-find-a-service.md).</span></span>

## <a name="example"></a><span data-ttu-id="32010-122">例</span><span class="sxs-lookup"><span data-stu-id="32010-122">Example</span></span>

 <span data-ttu-id="32010-123">このトピックで使用するコード全体の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="32010-123">This is the full listing of the code used in this topic.</span></span>

```csharp
// CalculatorService.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;

namespace Microsoft.Samples.Discovery
{
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }

    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
  
        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```csharp
// Program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Description;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
            try
            {
                ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
                    new NetTcpBinding(), string.Empty);

                // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
                    new EndpointAddress(announcementEndpointAddress));

                ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
                serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

                // Make the service discoverable
                serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

                serviceHost.Open();

                Console.WriteLine("Calculator Service started at {0}", baseAddress);
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                serviceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (serviceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                serviceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="32010-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="32010-124">See also</span></span>

- [<span data-ttu-id="32010-125">WCF Discovery</span><span class="sxs-lookup"><span data-stu-id="32010-125">WCF Discovery</span></span>](wcf-discovery.md)
- [<span data-ttu-id="32010-126">方法: 探索プロキシを実装する</span><span class="sxs-lookup"><span data-stu-id="32010-126">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="32010-127">方法: 探索プロキシを使用してサービスを検索するクライアント アプリケーションを実装する</span><span class="sxs-lookup"><span data-stu-id="32010-127">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)

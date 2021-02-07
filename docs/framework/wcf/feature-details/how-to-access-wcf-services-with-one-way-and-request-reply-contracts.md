---
description: '詳細については、「方法: One-Way と Request-Reply のコントラクトを使用して WCF サービスにアクセスする」を参照してください。'
title: '方法 : 一方向コントラクトと要求/応答コントラクトを使用して WCF サービスにアクセスする'
ms.date: 03/30/2017
ms.assetid: 7e10d3a5-fcf4-4a4b-a8d6-92ee2c988b3b
ms.openlocfilehash: b8dc63b8f3e12b4322bae97f202a8c59a29637f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742759"
---
# <a name="how-to-access-wcf-services-with-one-way-and-request-reply-contracts"></a><span data-ttu-id="f8a4d-103">方法 : 一方向コントラクトと要求/応答コントラクトを使用して WCF サービスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="f8a4d-103">How to: Access WCF Services with One-Way and Request-Reply Contracts</span></span>

<span data-ttu-id="f8a4d-104">次の手順では、一方向コントラクトと要求/応答コントラクトを定義し、双方向通信パターンを使用しない Windows Communication Foundation (WCF) サービスにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-104">The following procedures describe how to access a Windows Communication Foundation (WCF) service that defines a one-way contract and a request-reply contract and that does not use the duplex communication pattern.</span></span>  
  
### <a name="to-define-the-service"></a><span data-ttu-id="f8a4d-105">サービスを定義するには</span><span class="sxs-lookup"><span data-stu-id="f8a4d-105">To define the service</span></span>  
  
1. <span data-ttu-id="f8a4d-106">サービス コントラクトを宣言します。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-106">Declare the service contract.</span></span> <span data-ttu-id="f8a4d-107">一方向の操作の場合は `IsOneWay` 内で `true` が <xref:System.ServiceModel.OperationContractAttribute> に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-107">The operations that are to be one-way must have `IsOneWay` set to `true` within the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="f8a4d-108">次のコードは、`IOneWayCalculator`、`Add`、`Subtract`、および `Multiply` に対して一方向の操作を行う `Divide` コントラクトを宣言します。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-108">The following code declares the `IOneWayCalculator` contract that has one-way operations for `Add`, `Subtract`, `Multiply`, and `Divide`.</span></span> <span data-ttu-id="f8a4d-109">また、`SayHello` という要求応答操作も定義します。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-109">It also defines a request response operation called `SayHello`.</span></span>  
  
    ```csharp  
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface IOneWayCalculator  
    {  
        [OperationContract(IsOneWay = true)]  
        void Add(double n1, double n2);  
        [OperationContract(IsOneWay = true)]  
        void Subtract(double n1, double n2);  
        [OperationContract(IsOneWay = true)]  
        void Multiply(double n1, double n2);  
        [OperationContract(IsOneWay = true)]  
        void Divide(double n1, double n2);  
        [OperationContract]  
        string SayHello(string name);  
    }  
    ```  
  
2. <span data-ttu-id="f8a4d-110">サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-110">Implement the service contract.</span></span> <span data-ttu-id="f8a4d-111">次のコードは `IOnewayCalculator` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-111">The following code implements the `IOnewayCalculator` interface.</span></span>  
  
    ```csharp  
    [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.PerCall)]  
    public class CalculatorService : IOneWayCalculator  
    {  
        public void Add(double n1, double n2)  
        {  
           double result = n1 + n2;  
           Console.WriteLine("Add({0},{1}) = {2} ", n1, n2, result);  
        }  
  
        public void Subtract(double n1, double n2)  
        {  
           double result = n1 - n2;  
           Console.WriteLine("Subtract({0},{1}) = {2}", n1, n2, result);  
        }  
  
        public void Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Multiply({0},{1}) = {2}", n1, n2, result);  
        }  
  
        public void Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Divide({0},{1}) = {2}", n1, n2, result);  
        }  
  
        public string SayHello(string name)  
        {  
            Console.WriteLine("SayHello({0})", name);  
            return "Hello " + name;  
        }  
    }  
    ```  
  
3. <span data-ttu-id="f8a4d-112">コンソール アプリケーションでサービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-112">Host the service in a console application.</span></span> <span data-ttu-id="f8a4d-113">次のコードはサービスをホストする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-113">The following code shows how to host the service.</span></span>  
  
    ```csharp  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
       // Define the base address for the service.  
       Uri baseAddress = new Uri("http://localhost:8000/servicemodelsamples/service");  
  
       // Create a ServiceHost for the CalculatorService type and provide the base address.  
       using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
       {  
            // Add an endpoint using the IOneWayCalculator contract and the WSHttpBinding  
            serviceHost.AddServiceEndpoint(typeof(IOneWayCalculator), new WSHttpBinding(), "");  
  
          // Turn on the metadata behavior, this allows svcutil to get metadata for the service.  
          ServiceMetadataBehavior smb = (ServiceMetadataBehavior) serviceHost.Description.Behaviors.Find<ServiceMetadataBehavior>();  
          if (smb == null)  
          {  
                smb = new ServiceMetadataBehavior();  
                smb.HttpGetEnabled = true;  
                serviceHost.Description.Behaviors.Add(smb);  
          }  
  
          // Open the ServiceHostBase to create listeners and start listening for messages.  
          serviceHost.Open();  
  
          // The service can now be accessed.  
          Console.WriteLine("The service is ready.");  
          Console.WriteLine("Press <ENTER> to terminate service.");  
          Console.WriteLine();  
          Console.ReadLine();  
        }  
    }  
    ```  
  
### <a name="to-access-the-service"></a><span data-ttu-id="f8a4d-114">サービスにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="f8a4d-114">To access the service</span></span>  
  
1. <span data-ttu-id="f8a4d-115">次のサンプルコードに示すように、servicemodel metadata utility tool ( [Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) を実行して、メタデータ交換エンドポイントアドレスを使用して、サービスのクライアントクラスを作成します。 `Svcutil http://localhost:8000/Service` Servicemodel metadata [utility tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) は、インターフェイスとクラスのセットを生成します。次のサンプルコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-115">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) using the metadata exchange endpoint address to create the client class for the service using the following command line: `Svcutil http://localhost:8000/Service` The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) generates a set of interfaces and classes, as shown in the following sample code.</span></span>  
  
    ```csharp  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
    [System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.ServiceModel.Samples", ConfigurationName="IOneWayCalculator")]  
    public interface IOneWayCalculator  
    {  
  
        [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.ServiceModel.Samples/IOneWayCalculator/Add")]  
        void Add(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.ServiceModel.Samples/IOneWayCalculator/Subtract")]  
        void Subtract(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.ServiceModel.Samples/IOneWayCalculator/Multiply")]  
        void Multiply(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.ServiceModel.Samples/IOneWayCalculator/Divide")]  
        void Divide(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/IOneWayCalculator/SayHello", ReplyAction="http://Microsoft.ServiceModel.Samples/IOneWayCalculator/SayHelloResponse")]  
        string SayHello(string name);  
    }  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
    public interface IOneWayCalculatorChannel : IOneWayCalculator, System.ServiceModel.IClientChannel  
    {  
    }  
  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
    public partial class OneWayCalculatorClient : System.ServiceModel.ClientBase<IOneWayCalculator>, IOneWayCalculator  
    {  
  
        public OneWayCalculatorClient()  
        {  
        }  
  
        public OneWayCalculatorClient(string endpointConfigurationName) :
                base(endpointConfigurationName)  
        {  
        }  
  
        public OneWayCalculatorClient(string endpointConfigurationName, string remoteAddress) :
                base(endpointConfigurationName, remoteAddress)  
        {  
        }  
  
        public OneWayCalculatorClient(string endpointConfigurationName, System.ServiceModel.EndpointAddress remoteAddress) :
                base(endpointConfigurationName, remoteAddress)  
        {  
        }  
  
        public OneWayCalculatorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress remoteAddress) :
                base(binding, remoteAddress)  
        {  
        }  
  
        public void Add(double n1, double n2)  
        {  
            base.Channel.Add(n1, n2);  
        }  
  
        public void Subtract(double n1, double n2)  
        {  
            base.Channel.Subtract(n1, n2);  
        }  
  
        public void Multiply(double n1, double n2)  
        {  
            base.Channel.Multiply(n1, n2);  
        }  
  
        public void Divide(double n1, double n2)  
        {  
            base.Channel.Divide(n1, n2);  
        }  
  
        public string SayHello(string name)  
        {  
            return base.Channel.SayHello(name);  
        }  
    }  
    ```  
  
     <span data-ttu-id="f8a4d-116">`IOneWayCalculator` インターフェイスでは、一方向サービス操作の <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 属性が `true` に設定されており、要求応答サービス操作の属性は既定値である `false` に設定されていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-116">Notice in the `IOneWayCalculator` interface that the one-way service operations have the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> attribute set to `true` and the request-reply service operation has the attribute set to the default value, `false`.</span></span> <span data-ttu-id="f8a4d-117">また、`OneWayCalculatorClient` クラスにも注目してください。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-117">Also notice the `OneWayCalculatorClient` class.</span></span> <span data-ttu-id="f8a4d-118">これはサービスを呼び出すために使用するクラスです。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-118">This is the class that you will use to call the service.</span></span>  
  
2. <span data-ttu-id="f8a4d-119">クライアント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-119">Create the client object.</span></span>  
  
    ```csharp  
    // Create a client  
    WSHttpBinding binding = new WSHttpBinding();  
    EndpointAddress epAddress = new EndpointAddress("http://localhost:8000/servicemodelsamples/service");  
    OneWayCalculatorClient client = new OneWayCalculatorClient(binding, epAddress);  
    ```  
  
3. <span data-ttu-id="f8a4d-120">サービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-120">Call service operations.</span></span>  
  
    ```csharp  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1})", value1, value2);  
  
    // Call the Subtract service operation.  
    value1 = 145.00D;  
    value2 = 76.54D;  
    client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1})", value1, value2);  
  
    // Call the Multiply service operation.  
    value1 = 9.00D;  
    value2 = 81.25D;  
    client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1})", value1, value2);  
  
    // Call the Divide service operation.  
    value1 = 22.00D;  
    value2 = 7.00D;  
    client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1})", value1, value2);  
  
    // Call the SayHello service operation  
    string name = "World";  
    string response = client.SayHello(name);  
    Console.WriteLine("SayHello([0])", name);  
    Console.WriteLine("SayHello() returned: " + response);  
    ```  
  
4. <span data-ttu-id="f8a4d-121">クライアントを閉じて接続を終了し、リソースをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-121">Close the client to close connections and clean up resources.</span></span>  
  
    ```csharp  
    //Closing the client gracefully closes the connection and cleans up resources  
    client.Close();  
    ```  
  
## <a name="example"></a><span data-ttu-id="f8a4d-122">例</span><span class="sxs-lookup"><span data-stu-id="f8a4d-122">Example</span></span>  

 <span data-ttu-id="f8a4d-123">このトピックで使用されているコードの完全な一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f8a4d-123">The following is a complete listing of the code used  in this topic.</span></span>  
  
```csharp  
// Service.cs  
using System;  
using System.Configuration;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Microsoft.ServiceModel.Samples  
{  
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface IOneWayCalculator  
    {  
        [OperationContract(IsOneWay = true)]  
        void Add(double n1, double n2);  
        [OperationContract(IsOneWay = true)]  
        void Subtract(double n1, double n2);  
        [OperationContract(IsOneWay = true)]  
        void Multiply(double n1, double n2);  
        [OperationContract(IsOneWay = true)]  
        void Divide(double n1, double n2);  
        [OperationContract]  
        string SayHello(string name);  
    }  
  
    // Service class which implements the service contract.  
    // Added code to write output to the console window  
    [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.PerCall)]  
    public class CalculatorService : IOneWayCalculator  
    {  
        public void Add(double n1, double n2)  
        {  
            double result = n1 + n2;  
            Console.WriteLine("Add({0},{1}) = {2} ", n1, n2, result);  
        }  
  
        public void Subtract(double n1, double n2)  
        {  
            double result = n1 - n2;  
            Console.WriteLine("Subtract({0},{1}) = {2}", n1, n2, result);  
        }  
  
        public void Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Multiply({0},{1}) = {2}", n1, n2, result);  
        }  
  
        public void Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Divide({0},{1}) = {2}", n1, n2, result);  
        }  
  
        public string SayHello(string name)  
        {  
            Console.WriteLine("SayHello({0})", name);  
            return "Hello " + name;  
        }  
  
        // Host the service within this EXE console application.  
        public static void Main()  
        {  
            // Define the base address for the service.  
            Uri baseAddress = new Uri("http://localhost:8000/servicemodelsamples/service");  
  
            // Create a ServiceHost for the CalculatorService type and provide the base address.  
            using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
            {  
                // Add an endpoint using the IOneWayCalculator contract and the WSHttpBinding  
                serviceHost.AddServiceEndpoint(typeof(IOneWayCalculator), new WSHttpBinding(), "");  
  
                // Turn on the metadata behavior, this allows svcutil to get metadata for the service.  
                ServiceMetadataBehavior smb = (ServiceMetadataBehavior) serviceHost.Description.Behaviors.Find<ServiceMetadataBehavior>();  
                if (smb == null)  
                {  
                    smb = new ServiceMetadataBehavior();  
                    smb.HttpGetEnabled = true;  
                    serviceHost.Description.Behaviors.Add(smb);  
                }  
  
                // Open the ServiceHostBase to create listeners and start listening for messages.  
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
// client.cs  
using System;  
using System.ServiceModel;  
  
namespace Microsoft.ServiceModel.Samples  
{  
    //The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
    //Client implementation code.  
    class Client  
    {  
        static void Main()  
        {  
            // Create a client  
            WSHttpBinding binding = new WSHttpBinding();  
            EndpointAddress epAddress = new EndpointAddress("http://localhost:8000/servicemodelsamples/service");  
            OneWayCalculatorClient client = new OneWayCalculatorClient(binding, epAddress);  
  
            // Call the Add service operation.  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
            client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1})", value1, value2);  
  
            // Call the Subtract service operation.  
            value1 = 145.00D;  
            value2 = 76.54D;  
            client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1})", value1, value2);  
  
            // Call the Multiply service operation.  
            value1 = 9.00D;  
            value2 = 81.25D;  
            client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1})", value1, value2);  
  
            // Call the Divide service operation.  
            value1 = 22.00D;  
            value2 = 7.00D;  
            client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1})", value1, value2);  
  
            // Call the SayHello service operation  
            string name = "World";  
            string response = client.SayHello(name);  
            Console.WriteLine("SayHello([0])", name);  
            Console.WriteLine("SayHello() returned: " + response);  
            //Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8a4d-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8a4d-124">See also</span></span>

- [<span data-ttu-id="f8a4d-125">一方向サービス</span><span class="sxs-lookup"><span data-stu-id="f8a4d-125">One-Way Services</span></span>](one-way-services.md)

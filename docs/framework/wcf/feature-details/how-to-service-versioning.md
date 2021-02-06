---
description: '詳細については、「方法: サービスのバージョン管理」を参照してください。'
title: '方法: サービスのバージョン管理'
ms.date: 03/30/2017
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
ms.openlocfilehash: d32ea2051783ccaec7a66bfffada7f08887f8559
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643229"
---
# <a name="how-to-service-versioning"></a><span data-ttu-id="fb9e7-103">方法: サービスのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="fb9e7-103">How To: Service Versioning</span></span>

<span data-ttu-id="fb9e7-104">このトピックでは、メッセージを同じサービスの異なるバージョンにルーティングするルーティング構成を作成するために必要な、基本的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-104">This topic outlines the basic steps required to create a routing configuration that routes messages to different versions of the same service.</span></span> <span data-ttu-id="fb9e7-105">この例では、電卓サービスの 2 つのバージョン `roundingCalc` (v1) および `regularCalc` (v2) にメッセージがルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-105">In this example, messages are routed to two different versions of a calculator service, `roundingCalc` (v1) and `regularCalc` (v2).</span></span> <span data-ttu-id="fb9e7-106">これらの実装は両方とも同じ操作をサポートしますが、古い方のサービス `roundingCalc` では、戻る前にすべての計算を最も近い整数値に丸めます。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-106">Both implementations support the same operations; however the older service, `roundingCalc`, rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="fb9e7-107">クライアント アプリケーションは、新しい方の `regularCalc` サービスを使用するかどうかを示すことが可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-107">A client application must be able to indicate whether to use the newer `regularCalc` service.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="fb9e7-108">メッセージをサービスの特定のバージョンにルーティングするには、ルーティング サービスで、メッセージの内容に基づいて、そのメッセージの転送先を特定できることが必要です。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-108">In order to route a message to a specific service version, the Routing Service must be able to determine the message destination based on the message content.</span></span> <span data-ttu-id="fb9e7-109">次に示す手法では、クライアントがメッセージ ヘッダーに情報を挿入することでバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-109">In the method demonstrated below, the client will specify the version by inserting information into a message header.</span></span> <span data-ttu-id="fb9e7-110">サービスのバージョンを指定するいくつかの手法では、クライアントが追加データを渡す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-110">There are methods of service versioning that do not require clients to pass additional data.</span></span> <span data-ttu-id="fb9e7-111">たとえば、サービスの最新のバージョン、または最も互換性のあるバージョンにメッセージをルーティングしたり、ルーターが標準の SOAP エンベロープの一部を使用したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-111">For example, a message could be routed to the most recent or most compatible version of a service or the router could use a part of the standard SOAP envelope.</span></span>  
  
 <span data-ttu-id="fb9e7-112">次の操作が両方のサービスによって公開されます。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-112">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="fb9e7-113">追加</span><span class="sxs-lookup"><span data-stu-id="fb9e7-113">Add</span></span>  
  
- <span data-ttu-id="fb9e7-114">減算</span><span class="sxs-lookup"><span data-stu-id="fb9e7-114">Subtract</span></span>  
  
- <span data-ttu-id="fb9e7-115">乗算</span><span class="sxs-lookup"><span data-stu-id="fb9e7-115">Multiply</span></span>  
  
- <span data-ttu-id="fb9e7-116">除算</span><span class="sxs-lookup"><span data-stu-id="fb9e7-116">Divide</span></span>  
  
 <span data-ttu-id="fb9e7-117">両方のサービス実装が同じ操作を処理し、返すデータを除いて基本的に同一であるため、クライアント アプリケーションから送信されるメッセージに含まれる基本データでは、要求をルーティングする方法を特定できません。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-117">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="fb9e7-118">たとえば、両方のサービスの既定のアクションが同じであるために、アクション フィルターを使用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-118">For example, Action filters cannot be used because the default actions for both services are the same.</span></span>  
  
 <span data-ttu-id="fb9e7-119">この問題は、いくつかの方法で解決できます。たとえば、ルーター上でサービスの各バージョン用に特定のエンドポイントを公開したり、メッセージにカスタム ヘッダー要素を追加してサービスのバージョンを示したりできます。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-119">This can be resolved in several ways, such as exposing a specific endpoint on the router for each version of the service or adding a custom header element to the message to indicate service version.</span></span>  <span data-ttu-id="fb9e7-120">どちらの方法でも、受信メッセージをサービスの特定のバージョンに一意にルーティングできますが、異なるサービス バージョンの要求を区別するには、一意のメッセージ コンテンツを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-120">Each of these approaches allows you to uniquely route incoming messages to a specific version of the service, but utilizing unique message content is the preferred method of differentiating between requests for different service versions.</span></span>  
  
 <span data-ttu-id="fb9e7-121">この例では、クライアント アプリケーションがカスタム ヘッダー CalcVer を要求メッセージに追加します。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-121">In this example, the client application adds the ‘CalcVer’ custom header to the request message.</span></span> <span data-ttu-id="fb9e7-122">このヘッダーには、メッセージのルーティング先となるサービスのバージョンを示す値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-122">This header will contain a value that indicates the version of the service that the message should be routed to.</span></span> <span data-ttu-id="fb9e7-123">値が 1 の場合は roundingCalc サービス、値が 2 の場合は regularCalc サービスが、メッセージを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-123">A value of ‘1’ indicates that the message must be processed by the roundingCalc service, while a value of ‘2’ indicates the regularCalc service.</span></span> <span data-ttu-id="fb9e7-124">これにより、クライアント アプリケーションは、サービスのどちらのバージョンでメッセージが処理されるかを直接制御できます。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-124">This allows the client application to directly control which version of the service will process the message.</span></span>  <span data-ttu-id="fb9e7-125">カスタム ヘッダーはメッセージ内に含まれる値であるため、1 つのエンドポイントを使用して、サービスの両方のバージョン宛てのメッセージを受信できます。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-125">Since the custom header is a value contained within the message, you can use one endpoint to receive messages destined for both versions of the service.</span></span> <span data-ttu-id="fb9e7-126">クライアント アプリケーションで次のコードを使用して、このカスタム ヘッダーをメッセージに追加できます。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-126">The following code can be used in the client application to add this custom header to the message:</span></span>  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a><span data-ttu-id="fb9e7-127">サービスのバージョン管理の実装</span><span class="sxs-lookup"><span data-stu-id="fb9e7-127">Implement Service Versioning</span></span>  
  
1. <span data-ttu-id="fb9e7-128">サービスによって公開されるサービス エンドポイントを指定することによって、ルーティング サービスの基本的な構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-128">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="fb9e7-129">次の例では、メッセージの受信に使用される、単一のサービス エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-129">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="fb9e7-130">また、`roundingCalc` (v1) サービスおよび `regularCalc` (v2) サービスへのメッセージ送信に使用する、クライアント エンドポイントも定義します。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-130">It also defines the client endpoints which will be used to send messages to the `roundingCalc` (v1) and the `regularCalc` (v2) services.</span></span>  
  
    ```xml  
    <services>  
        <service behaviorConfiguration="routingConfiguration"  
                 name="System.ServiceModel.Routing.RoutingService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost/routingservice/router" />  
            </baseAddresses>  
          </host>  
          <!--Set up the inbound endpoint for the Routing Service-->  
          <endpoint address="calculator"  
                    binding="wsHttpBinding"  
                    name="routerEndpoint"  
                    contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="http://localhost:8080/servicemodelsamples/service/"  
                    binding="wsHttpBinding"  
                    contract="*" />  
        </client>  
    ```  
  
2. <span data-ttu-id="fb9e7-131">送信先エンドポイントにメッセージをルーティングするのに使用するフィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-131">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="fb9e7-132">この例では、XPath フィルターを使用して "CalcVer" カスタムヘッダーの値を検出し、メッセージのルーティング先のバージョンを決定します。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-132">For this example, the XPath filter is used to detect the value of the "CalcVer" custom header to determine which version the message should be routed to.</span></span> <span data-ttu-id="fb9e7-133">XPath フィルターは、"CalcVer" ヘッダーが含まれていないメッセージを検出するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-133">An XPath filter is also used to detect messages that do not contain the "CalcVer" header.</span></span> <span data-ttu-id="fb9e7-134">次の例では、必要なフィルターおよび名前空間のテーブルを定義します。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-134">The following example defines the required filters and namespace table.</span></span>  
  
    ```xml  
    <!-- use the namespace table element to define a prefix for our custom namespace-->  
    <namespaceTable>  
      <add prefix="custom" namespace="http://my.custom.namespace/"/>  
    </namespaceTable>  
    <filters>  
      <!--define the different message filters-->  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 2-->  
      <filter name="XPathFilterRegular" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '2'"/>  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 1-->  
      <filter name="XPathFilterRounding" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '1'"/>  
       <!--define an xpath message filter to look for  
           messages that do not contain the custom header-->  
       <filter name="XPathFilterNoHeader" filterType="XPath"  
               filterData="count(sm:header()/custom:CalcVer)=0"/>  
    </filters>
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="fb9e7-135">S12 名前空間プレフィックスは、既定で名前空間テーブルに定義され、名前空間を表し `http://www.w3.org/2003/05/soap-envelope` ます。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-135">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
3. <span data-ttu-id="fb9e7-136">各フィルターをクライアント エンドポイントと関連付けるフィルター テーブルを定義します。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-136">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="fb9e7-137">メッセージの "CalcVer" ヘッダーに値1が含まれている場合は、regularCalc サービスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-137">If the message contains the "CalcVer" header with a value of 1, it will be sent to the regularCalc service.</span></span> <span data-ttu-id="fb9e7-138">ヘッダーに値 2 が含まれる場合は、roundingCalc サービスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-138">If the header contains a value of 2, it will be sent to the roundingCalc service.</span></span> <span data-ttu-id="fb9e7-139">ヘッダーがない場合、メッセージは regularCalc にルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-139">If no header is present, the message will be routed to the regularCalc.</span></span>  
  
     <span data-ttu-id="fb9e7-140">次のコードでは、フィルター テーブルを定義し、前に定義されたフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-140">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <!--look for the custom header = 1, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
          <!--look for the custom header = 2, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
          <!--look for the absence of the custom header, and if  
              it is not present, assume the v1 endpoint-->  
          <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="fb9e7-141">フィルター テーブルに含まれているフィルターと照合して受信メッセージを評価するには、ルーティング動作を使用して、フィルター テーブルをサービス エンドポイントと関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-141">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="fb9e7-142">次の例は、 `filterTable1` サービスエンドポイントとの関連付けを示しています。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-142">The following example demonstrates associating `filterTable1` with the service endpoints:</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="fb9e7-143">例</span><span class="sxs-lookup"><span data-stu-id="fb9e7-143">Example</span></span>  

 <span data-ttu-id="fb9e7-144">構成ファイル全体の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-144">The following is a complete listing of the configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="http://localhost:8080/servicemodelsamples/service/"  
                binding="wsHttpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 2-->  
        <filter name="XPathFilterRegular" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '2'"/>  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 1-->  
        <filter name="XPathFilterRounding" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '1'"/>  
        <!--define an xpath message filter to look for  
            messages that do not contain the custom header-->  
        <filter name="XPathFilterNoHeader" filterType="XPath"  
                filterData="count(sm:header()/custom:CalcVer)=0"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filters to the message filter table-->  
            <!--look for the custom header = 1, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
            <!--look for the custom header = 2, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
            <!--look for the absence of the custom header, and if  
                it is not present, assume the v1 endpoint-->  
            <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="fb9e7-145">例</span><span class="sxs-lookup"><span data-stu-id="fb9e7-145">Example</span></span>  

 <span data-ttu-id="fb9e7-146">クライアント アプリケーションの全体の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fb9e7-146">The following is a complete listing of the client application.</span></span>  
  
```csharp  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    //The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
    //Client implementation code.  
    class Client  
    {  
        static void Main()  
        {  
            //Print out the welcome text  
            Console.WriteLine("This sample routes the Calculator Sample through the new WCF RoutingService");  
            Console.WriteLine("Wait for all the services to indicate that they've started, then press");  
            Console.WriteLine("<ENTER> to start the client.");  
  
            while (Console.ReadLine() != "quit")  
            {  
                //Offer the Address configuration for the client  
                Console.WriteLine("");  
                Console.WriteLine("Welcome to the Calculator Client!");  
  
                EndpointAddress epa;  
                //set the default address as the general router endpoint  
                epa = new EndpointAddress("http://localhost/routingservice/router/calculator");  
  
                //set up the CalculatorClient with the EndpointAddress, the WSHttpBinding, and the ICalculator contract  
                //We use the WSHttpBinding so that the outgoing has a message envelope, which we'll manipulate in a minute  
                CalculatorClient client = new CalculatorClient(new WSHttpBinding(), epa);  
                //client.Endpoint.Contract = ContractDescription.GetContract(typeof(ICalculator));  
  
                //Ask the customer if they want to add a custom header to the outgoing message.  
                //The Router will look for this header, and if so ignore the endpoint the message was  
                //received on, and instead direct the message to the RoundingCalcService.  
                Console.WriteLine("");  
                Console.WriteLine("Which calculator service should be used?");  
                Console.WriteLine("Enter 1 for the rounding calculator, 2 for the regular calculator.");  
                Console.WriteLine("[1] or [2]?");  
  
                string header = Console.ReadLine();  
  
                //get the current operationContextScope from the client's inner channel  
                using (OperationContextScope ocs = new OperationContextScope((client.InnerChannel)))  
                {  
                    //get the outgoing message headers element (collection) from the context  
                    MessageHeaders messageHeadersElement = OperationContext.Current.OutgoingMessageHeaders;  
  
                    //if they wanted to create the header, go ahead and add it to the outgoing message  
                    if (header != null && (header=="1" || header=="2"))  
                    {  
                        //create a new header "RoundingCalculator", no specific namespace, and set the value to
                        //the value of header.  
                        //the Routing Service will look for this header in order to determine if the message  
                        //should be routed to the RoundingCalculator  
                        messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", header));  
                    }  
                    else //incorrect choice, no header added  
                    {  
                        Console.WriteLine("Incorrect value entered, not adding a header");  
                    }  
  
                        //call the client operations  
                        CallClient(client);  
                }  
  
                //close the client to clean it up  
                client.Close();  
                Console.WriteLine();  
                Console.WriteLine("Press <ENTER> to run the client again or type 'quit' to quit.");  
            }  
        }  
  
        private static void CallClient(CalculatorClient client)  
        {  
            Console.WriteLine("");  
            Console.WriteLine("Sending!");  
            // Call the Add service operation.  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            value1 = 145.00D;  
            value2 = 76.54D;  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            value1 = 9.00D;  
            value2 = 81.25D;  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            value1 = 22.00D;  
            value2 = 7.00D;  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb9e7-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb9e7-147">See also</span></span>

- [<span data-ttu-id="fb9e7-148">ルーティング サービス</span><span class="sxs-lookup"><span data-stu-id="fb9e7-148">Routing Services</span></span>](../samples/routing-services.md)

---
description: '詳細については、「方法: サービスデータのパーティション分割」を参照してください。'
title: '方法: サービス データのパーティション分割'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: fd40ee37a80a8d5039231c6efe6369006022afad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643242"
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="7a3db-103">方法: サービス データのパーティション分割</span><span class="sxs-lookup"><span data-stu-id="7a3db-103">How To: Service Data Partitioning</span></span>

<span data-ttu-id="7a3db-104">このトピックでは、メッセージを同じ送信先サービスの複数のインスタンスにパーティション分割するのに必要な、基本的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a3db-104">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="7a3db-105">サービス データのパーティション分割は、一般的に、優れた品質のサービスを提供するためにサービスを拡張する必要がある場合や、さまざまな顧客からの要求を特定の方法で処理する必要がある場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a3db-105">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="7a3db-106">たとえば、高い値または "Gold" の顧客からのメッセージは、標準の顧客からのメッセージよりも高い優先順位で処理する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="7a3db-106">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="7a3db-107">この例では、メッセージが regularCalc サービスの 2 つのインスタンスの 1 つにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="7a3db-107">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="7a3db-108">サービスの両方のインスタンスは同じですが、calculator1 エンドポイントで表されるサービスは、重要な顧客から受け取ったメッセージを処理し、calculator 2 エンドポイントは、その他の顧客からのメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="7a3db-108">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="7a3db-109">クライアントから送信されたメッセージには、どちらのサービス インスタンスにメッセージをルーティングする必要があるかを識別するのに使用できる一意のデータはありません。</span><span class="sxs-lookup"><span data-stu-id="7a3db-109">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="7a3db-110">各クライアントが特定の送信先サービスにデータをルーティングできるようにするため、メッセージの受信に使用される 2 つのサービス エンドポイントを実装します。</span><span class="sxs-lookup"><span data-stu-id="7a3db-110">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a3db-111">この例では、特定のエンドポイントを使用してデータをパーティション分割しますが、ヘッダーや本文データなど、メッセージ自体に含まれている情報を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="7a3db-111">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="7a3db-112">サービス データのパーティション分割の実装</span><span class="sxs-lookup"><span data-stu-id="7a3db-112">Implement Service Data Partitioning</span></span>  
  
1. <span data-ttu-id="7a3db-113">サービスによって公開されるサービス エンドポイントを指定することによって、ルーティング サービスの基本的な構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="7a3db-113">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="7a3db-114">次の例では、メッセージの受信に使用する、2 つのサービス エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="7a3db-114">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="7a3db-115">また、regularCalc サービス インスタンスへのメッセージ送信に使用する、クライアント エンドポイントも定義します。</span><span class="sxs-lookup"><span data-stu-id="7a3db-115">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
       </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
        <endpoint name="CalcEndpoint1"  
                  address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
  
        <endpoint name="CalcEndpoint2"  
                  address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
     </client>  
    ```  
  
2. <span data-ttu-id="7a3db-116">送信先エンドポイントにメッセージをルーティングするのに使用するフィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="7a3db-116">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="7a3db-117">この例では、EndpointName フィルターを使用して、どのサービス エンドポイントがメッセージを受信したかを判断します。</span><span class="sxs-lookup"><span data-stu-id="7a3db-117">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="7a3db-118">次の例では、必要なルーティング セクションおよびフィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="7a3db-118">The following example defines the necessary routing section and filters.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the different message filters-->  
      <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
      <filter name="HighPriority" filterType="EndpointName"  
              filterData="calculator1Endpoint"/>  
      <filter name="NormalPriority" filterType="EndpointName"  
              filterData="calculator2Endpoint"/>  
    </filters>  
    ```  
  
3. <span data-ttu-id="7a3db-119">各フィルターをクライアント エンドポイントと関連付けるフィルター テーブルを定義します。</span><span class="sxs-lookup"><span data-stu-id="7a3db-119">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="7a3db-120">この例では、メッセージの受信に使用された特定のエンドポイントに基づいて、メッセージがルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="7a3db-120">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="7a3db-121">メッセージは 2 つのフィルターのどちらかにのみ一致するため、フィルターが評価される順序をフィルターの優先順位で制御する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7a3db-121">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="7a3db-122">次のコードでは、フィルター テーブルを定義し、前に定義されたフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="7a3db-122">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="7a3db-123">受信メッセージをテーブルに含まれているフィルターと照合して評価するには、ルーティング動作を使用して、フィルター テーブルをサービス エンドポイントと関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a3db-123">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="7a3db-124">次の例は、"filterTable1" をサービスエンドポイントに関連付ける方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7a3db-124">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="7a3db-125">例</span><span class="sxs-lookup"><span data-stu-id="7a3db-125">Example</span></span>  

 <span data-ttu-id="7a3db-126">構成ファイル全体の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7a3db-126">The following is a complete listing of the configuration file.</span></span>  
  
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
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
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
      <endpoint name="CalcEndpoint1"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="CalcEndpoint2"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
  
      <filters>  
        <!--define the different message filters-->  
        <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
        <filter name="HighPriority" filterType="EndpointName"  
                filterData="calculator1Endpoint"/>  
        <filter name="NormalPriority" filterType="EndpointName"  
                filterData="calculator2Endpoint"/>  
      </filters>  
  
      <filterTables>  
        <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
          <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
        </filterTable>  
      </filterTables>  
  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a3db-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a3db-127">See also</span></span>

- [<span data-ttu-id="7a3db-128">ルーティング サービス</span><span class="sxs-lookup"><span data-stu-id="7a3db-128">Routing Services</span></span>](../samples/routing-services.md)

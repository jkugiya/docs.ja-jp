---
description: '詳細については、「方法: エラー処理」を参照してください。'
title: '方法: エラー処理'
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 1d385070e4cc0d55bc3327114baf4e4ff543171f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704655"
---
# <a name="how-to-error-handling"></a><span data-ttu-id="abbab-103">方法: エラー処理</span><span class="sxs-lookup"><span data-stu-id="abbab-103">How To: Error Handling</span></span>

<span data-ttu-id="abbab-104">ここでは、エラー処理を使用するルーティング構成の作成に必要な基本的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="abbab-104">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="abbab-105">この例では、メッセージは送信先エンドポイントにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="abbab-105">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="abbab-106">ネットワークまたは通信関係の障害 (<xref:System.ServiceModel.CommunicationException>) のために、メッセージを配信できない場合、そのメッセージは代替エンドポイントに再送信されます。</span><span class="sxs-lookup"><span data-stu-id="abbab-106">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="abbab-107">ネットワーク障害をシミュレートするために、この例で使用される送信先エンドポイントには、誤ったアドレスが格納されています。</span><span class="sxs-lookup"><span data-stu-id="abbab-107">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="abbab-108">指定したアドレスをリッスンするサービスがないため、このエンドポイントにルーティングされるメッセージはエラーになります。</span><span class="sxs-lookup"><span data-stu-id="abbab-108">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>

> [!NOTE]
> <span data-ttu-id="abbab-109">このトピックの例では、タイムアウト設定について明示的に説明していませんが、エラー処理を使用する際には、この点を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abbab-109">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="abbab-110">エラーが発生すると、クライアントが応答を受け取る前に、追加の遅延が発生します。</span><span class="sxs-lookup"><span data-stu-id="abbab-110">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="abbab-111">これは、ルーティング サービスがエラーを受信し、そのメッセージをバックアップ エンドポイントに送信しようとするためです。</span><span class="sxs-lookup"><span data-stu-id="abbab-111">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="abbab-112">プライマリおよびバックアップの送信先エンドポイントに関連付けられたタイムアウト値が大きい場合は、クライアントでの遅延が大きくなることがあります。これは、メッセージが、バックアップ リスト内の複数のエンドポイントをフェールオーバーした後に、正常に送信されるためです。</span><span class="sxs-lookup"><span data-stu-id="abbab-112">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>
>
> <span data-ttu-id="abbab-113">ルーティング サービスが受ける遅延は、最大の場合、フィルターと関連付けられたすべてのエンドポイントのタイムアウト値の合計となる可能性があるため、これに応じて、クライアントで予測されるタイムアウト値を増やすことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="abbab-113">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>

### <a name="implement-error-handling"></a><span data-ttu-id="abbab-114">エラー処理の実装</span><span class="sxs-lookup"><span data-stu-id="abbab-114">Implement Error Handling</span></span>

1. <span data-ttu-id="abbab-115">サービスによって公開されるサービス エンドポイントを指定することによって、ルーティング サービスの基本的な構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="abbab-115">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="abbab-116">次の例では、メッセージの受信に使用される、単一のサービス エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="abbab-116">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="abbab-117">また、メッセージ送信に使用する deadDestination および realDestination クライアント エンドポイントも定義します。</span><span class="sxs-lookup"><span data-stu-id="abbab-117">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="abbab-118">deadDestination エンドポイントには、実行中のサービスを参照していないアドレスが格納されており、このエンドポイントへのメッセージ送信時のネットワーク障害をシミュレートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="abbab-118">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>

    ```xml
    <services>
      <service behaviorConfiguration="routingConfiguration"
               name="System.ServiceModel.Routing.RoutingService">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost/routingservice/" />
          </baseAddresses>
        </host>
        <!-- Create the Routing Service endpoint -->
        <endpoint address="router"
                  binding="basicHttpBinding"
                  name="RoutingServiceEndpoint"
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>
    </services>

    <!-- Create the destination endpoints that we want to send to -->
    <client>
      <!-- Create a dummy endpoint that we know will be down -->
      <endpoint name="deadDestination"
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"
                binding="netTcpBinding"
                contract="*" />

      <!-- Now create the real service endpoint -->
      <endpoint name="realDestination"
                address="net.tcp://localhost:8080/servicemodelsamples/service"
                binding="netTcpBinding"
                contract="*" />
    </client>
    ```

2. <span data-ttu-id="abbab-119">送信先エンドポイントにメッセージをルーティングするのに使用するフィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="abbab-119">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="abbab-120">この例では、ルーティング サービスが受信するすべてのメッセージと照合するために MatchAll フィルターを使用します。</span><span class="sxs-lookup"><span data-stu-id="abbab-120">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. <span data-ttu-id="abbab-121">バックアップ エンドポイント リストを定義します。このリストには、プライマリ送信先エンドポイントへの送信時にネットワークまたは通信の障害が発生した場合に、メッセージの送信先となるエンドポイントを格納します。</span><span class="sxs-lookup"><span data-stu-id="abbab-121">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="abbab-122">次の例では、1 つのエンドポイントを格納しているバックアップ リストを定義します。ただし、複数のエンドポイントを 1 つのバックアップ リストに指定できます。</span><span class="sxs-lookup"><span data-stu-id="abbab-122">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>

     <span data-ttu-id="abbab-123">バックアップ リストに複数のエンドポイントが格納されている場合、ネットワークまたは通信の障害が発生すると、ルーティング サービスでは、そのリスト内の最初のエンドポイントにメッセージを送信しようとします。</span><span class="sxs-lookup"><span data-stu-id="abbab-123">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="abbab-124">このエンドポイントへの送信時にネットワークまたは通信の障害が発生した場合、そのルーティング サービスでは、そのリスト内の次のエンドポイントにメッセージを送信しようとします。</span><span class="sxs-lookup"><span data-stu-id="abbab-124">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="abbab-125">このサービスは、メッセージが正常に送信されるか、すべてのバックアップ エンドポイントがネットワークまたは通信関連のエラーを返すか、メッセージが送信されてエンドポイントがネットワーク以外で通信関連以外のエラーを返すまで、このバックアップ エンドポイント リスト内の各エンドポイントにメッセージの送信を続けます。</span><span class="sxs-lookup"><span data-stu-id="abbab-125">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. <span data-ttu-id="abbab-126">フィルターを deadDestination エンドポイントおよびバックアップ エンドポイント リストと関連付けるフィルター テーブルを定義します。</span><span class="sxs-lookup"><span data-stu-id="abbab-126">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="abbab-127">まず、ルーティング サービスは、このフィルターに関連付けられた送信先エンドポイントにメッセージを送信しようとします。</span><span class="sxs-lookup"><span data-stu-id="abbab-127">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="abbab-128">deadDestination エンドポイントには、実行中のサービスを参照していないアドレスが格納されているため、これはネットワーク エラーになります。</span><span class="sxs-lookup"><span data-stu-id="abbab-128">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="abbab-129">次に、ルーティングサービスは、backupEndpointList で指定されたエンドポイントにメッセージを送信しようとします。</span><span class="sxs-lookup"><span data-stu-id="abbab-129">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointList.</span></span>

    ```xml
    <filterTables>
            <!-- Set up the Routing Service's Message Filter Table -->
            <filterTable name="filterTable1">
                <!-- Add an entity that maps the MatchAllMessageFilter to the dead destination -->
                <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
                <!-- Listed in the backupEndpointList -->
                <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
            </filterTable>
          </filterTables>
    ```

5. <span data-ttu-id="abbab-130">受信メッセージをフィルター テーブルに含まれているフィルターと照合して評価するには、ルーティング動作を使用して、フィルター テーブルをサービス エンドポイントと関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="abbab-130">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="abbab-131">次の例は、"filterTable1" をサービスエンドポイントに関連付ける方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="abbab-131">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>

    ```xml
    <behaviors>
      <serviceBehaviors>
        <!-- Set up the Routing Behavior -->
        <behavior name="routingConfiguration">
          <routing filterTableName="filterTable1" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    ```

## <a name="example"></a><span data-ttu-id="abbab-132">例</span><span class="sxs-lookup"><span data-stu-id="abbab-132">Example</span></span>

<span data-ttu-id="abbab-133">構成ファイルの完全な一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="abbab-133">The following is a complete listing of the configuration file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<!-- Copyright (c) Microsoft Corporation.  All Rights Reserved. -->
<configuration>
  <system.serviceModel>
    <services>
      <service behaviorConfiguration="routingConfiguration"
               name="System.ServiceModel.Routing.RoutingService">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost/routingservice/" />
          </baseAddresses>
        </host>
        <!-- Create the Routing Service endpoint -->
        <endpoint address="router"
                  binding="basicHttpBinding"
                  name="RoutingServiceEndpoint"
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <!-- Set up the Routing Behavior -->
        <behavior name="routingConfiguration">
          <routing filterTableName="filterTable1" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <!-- Create the destination endpoints that we want to send to -->
    <client>
      <!-- Create a dummy endpoint that we know will be down -->
      <endpoint name="deadDestination"
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"
                binding="netTcpBinding"
                contract="*" />

      <!-- Now create the real service endpoint -->
      <endpoint name="realDestination"
                address="net.tcp://localhost:8080/servicemodelsamples/service"
                binding="netTcpBinding"
                contract="*" />
    </client>
    <routing>
      <filters>
        <!-- Create a MatchAll filter which will catch all messages -->
        <filter name="MatchAllFilter1" filterType="MatchAll" />
      </filters>
      <filterTables>
        <!-- Set up the Routing Service's Message Filter Table -->
        <filterTable name="filterTable1">
            <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->
            <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
            <!-- Listed in the backupEndpointList -->
            <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
        </filterTable>
      </filterTables>
      <!-- Create the backup endpoint list -->
      <backupLists>
        <backupList name="backupEndpointList">
            <add endpointName="realDestination" />
        </backupList>
      </backupLists>
      </routing>
  </system.serviceModel>
</configuration>
```

---
description: '詳細情報: SqlCommand の実行と SqlNotificationRequest'
title: SqlCommand の実行と SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: d3e82022794aa67d4bd20223cac852097f2be9dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767051"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="166c0-103">SqlCommand の実行と SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="166c0-103">SqlCommand Execution with a SqlNotificationRequest</span></span>

<span data-ttu-id="166c0-104">サーバーからフェッチした後で、データが変更される場合があります。当然、もう一度クエリを実行すると、前回とは異なる結果セットが得られます。<xref:System.Data.SqlClient.SqlCommand> を適切に構成することで、このような場合に通知を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="166c0-104">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="166c0-105">この機能は、サーバー上でカスタムの通知キューを使用する場合や、実際のオブジェクトを保持しない場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="166c0-105">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>

## <a name="creating-the-notification-request"></a><span data-ttu-id="166c0-106">通知要求の作成</span><span class="sxs-lookup"><span data-stu-id="166c0-106">Creating the Notification Request</span></span>

<span data-ttu-id="166c0-107"><xref:System.Data.Sql.SqlNotificationRequest> オブジェクトを使用して通知要求を作成し、それを `SqlCommand` オブジェクトにバインドできます。</span><span class="sxs-lookup"><span data-stu-id="166c0-107">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="166c0-108">要求を作成したら、`SqlNotificationRequest` オブジェクトは不要になります。</span><span class="sxs-lookup"><span data-stu-id="166c0-108">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="166c0-109">キューに対して任意の通知を照会し、適切に応答することができます。</span><span class="sxs-lookup"><span data-stu-id="166c0-109">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="166c0-110">通知は、アプリケーションがシャットダウンされ、その後再起動された場合でも発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="166c0-110">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>

<span data-ttu-id="166c0-111">コマンドに通知を関連付けて実行した場合、元の結果セットになんらかの変更が生じると、通知要求で構成した SQL Server キューにメッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="166c0-111">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>

<span data-ttu-id="166c0-112">SQL Server のキューをポーリングしメッセージを解釈する方法は、アプリケーションごとに固有なものになります。</span><span class="sxs-lookup"><span data-stu-id="166c0-112">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="166c0-113">アプリケーションは、メッセージの内容に基づいてキューのポーリングと応答を行います。</span><span class="sxs-lookup"><span data-stu-id="166c0-113">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>

> [!NOTE]
> <span data-ttu-id="166c0-114"><xref:System.Data.SqlClient.SqlDependency> と共に SQL Server 通知要求を使用する場合は、既定のサービス名を使用するのではなく、独自のキュー名を作成してください。</span><span class="sxs-lookup"><span data-stu-id="166c0-114">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>

<span data-ttu-id="166c0-115"><xref:System.Data.Sql.SqlNotificationRequest> に対応する新しいクライアント側セキュリティ要素はありません。</span><span class="sxs-lookup"><span data-stu-id="166c0-115">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="166c0-116">これはそもそもサーバー機能であり、ユーザーが通知を要求するために保持する必要がある特権はサーバーによって作成されています。</span><span class="sxs-lookup"><span data-stu-id="166c0-116">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>

### <a name="example"></a><span data-ttu-id="166c0-117">例</span><span class="sxs-lookup"><span data-stu-id="166c0-117">Example</span></span>

<span data-ttu-id="166c0-118">次のコード フラグメントは、<xref:System.Data.Sql.SqlNotificationRequest> を作成し、それを <xref:System.Data.SqlClient.SqlCommand> に関連付ける方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="166c0-118">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>

```vb
' Assume connection is an open SqlConnection.
' Create a new SqlCommand object.
Dim command As New SqlCommand( _
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)

' Create a SqlNotificationRequest object.
Dim notifcationRequest As New SqlNotificationRequest()
notificationRequest.id = "NotificationID"
notificationRequest.Service = "mySSBQueue"

' Associate the notification request with the command.
command.Notification = notificationRequest
' Execute the command.
command.ExecuteReader()
' Process the DataReader.
' You can use Transact-SQL syntax to periodically poll the
' SQL Server queue to see if you have a new message.
```

```csharp
// Assume connection is an open SqlConnection.
// Create a new SqlCommand object.
SqlCommand command=new SqlCommand(
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);

// Create a SqlNotificationRequest object.
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="see-also"></a><span data-ttu-id="166c0-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="166c0-119">See also</span></span>

- [<span data-ttu-id="166c0-120">SQL Server のクエリ通知</span><span class="sxs-lookup"><span data-stu-id="166c0-120">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="166c0-121">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="166c0-121">ADO.NET Overview</span></span>](../ado-net-overview.md)

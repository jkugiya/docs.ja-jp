---
description: '詳細情報: 接続イベント'
title: 接続イベント
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: fcf131e41ce90db11e84fd241744e348f4ca739e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663808"
---
# <a name="connection-events"></a><span data-ttu-id="cd294-103">接続イベント</span><span class="sxs-lookup"><span data-stu-id="cd294-103">Connection Events</span></span>

<span data-ttu-id="cd294-104">すべての .NET Framework データ プロバイダーには、データ ソースから情報メッセージを取得したり、**Connection** の状態の変化を確認したりするために使用できる 2 つのイベントを持った **Connection** オブジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="cd294-104">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="cd294-105">**Connection** オブジェクトのイベントを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="cd294-105">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="cd294-106">event</span><span class="sxs-lookup"><span data-stu-id="cd294-106">Event</span></span>|<span data-ttu-id="cd294-107">説明</span><span class="sxs-lookup"><span data-stu-id="cd294-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd294-108">**InfoMessage**</span><span class="sxs-lookup"><span data-stu-id="cd294-108">**InfoMessage**</span></span>|<span data-ttu-id="cd294-109">データ ソースから情報メッセージが返されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="cd294-109">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="cd294-110">情報メッセージはデータ ソースからのメッセージであり、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="cd294-110">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="cd294-111">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="cd294-111">**StateChange**</span></span>|<span data-ttu-id="cd294-112">**Connection** の状態が変化したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="cd294-112">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="cd294-113">InfoMessage イベントの使用</span><span class="sxs-lookup"><span data-stu-id="cd294-113">Working with the InfoMessage Event</span></span>  

 <span data-ttu-id="cd294-114"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> イベントを使用して、SQL Server データ ソースから警告や情報メッセージを取得できます。</span><span class="sxs-lookup"><span data-stu-id="cd294-114">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="cd294-115">重大度レベルが 11 から 16 のエラーがデータ ソースから返されると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="cd294-115">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="cd294-116"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントを使用して、エラーに関連付けられていないメッセージをデータ ソースから取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="cd294-116">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="cd294-117">Microsoft SQL Server の場合は、重大度レベルが 10 以下のエラーは情報メッセージと見なされ、<xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントでキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="cd294-117">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="cd294-118">詳しくは、「[データベース エンジン エラーの重大度](/sql/relational-databases/errors-events/database-engine-error-severities)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cd294-118">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="cd294-119"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントは <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> オブジェクトを受け取り、その **Errors** プロパティにはデータ ソースからのメッセージのコレクションが格納されています。</span><span class="sxs-lookup"><span data-stu-id="cd294-119">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="cd294-120">このコレクションの中の **Error** オブジェクトにエラー番号、メッセージ テキスト、およびエラーの原因を問い合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="cd294-120">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="cd294-121">.NET Framework Data Provider for SQL Server には、データベースの詳細情報、ストアド プロシージャ、およびメッセージ送信元の行番号も含まれます。</span><span class="sxs-lookup"><span data-stu-id="cd294-121">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="cd294-122">例</span><span class="sxs-lookup"><span data-stu-id="cd294-122">Example</span></span>  

 <span data-ttu-id="cd294-123"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントのイベント ハンドラーを追加する方法を次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="cd294-123">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="cd294-124">InfoMessages としてのエラー処理</span><span class="sxs-lookup"><span data-stu-id="cd294-124">Handling Errors as InfoMessages</span></span>  

 <span data-ttu-id="cd294-125"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントは通常、サーバーが情報メッセージまたは警告メッセージを送信した場合に限り発生します。</span><span class="sxs-lookup"><span data-stu-id="cd294-125">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="cd294-126">ただし、実際にエラーが発生した場合は、サーバーの操作を開始した **ExecuteNonQuery** メソッドまたは **ExecuteReader** メソッドの実行は停止され、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="cd294-126">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="cd294-127">サーバーでエラーが発生してもコマンド内の残りのステートメントの処理を続行する場合は、<xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> の <xref:System.Data.SqlClient.SqlConnection> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="cd294-127">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="cd294-128">このように設定すると、エラーが発生したとき、接続は例外をスローして処理を中断する代わりに、<xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="cd294-128">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="cd294-129">クライアント アプリケーションは、このイベントを処理し、エラーに応答できます。</span><span class="sxs-lookup"><span data-stu-id="cd294-129">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd294-130">重大度レベルが 17 以上のエラーが発生すると、サーバーのコマンド処理が停止します。このエラーは、例外として処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd294-130">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="cd294-131">この場合、<xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントによるエラー処理の方法にかかわらず例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="cd294-131">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="cd294-132">StateChange イベントの使用</span><span class="sxs-lookup"><span data-stu-id="cd294-132">Working with the StateChange Event</span></span>  

 <span data-ttu-id="cd294-133">**StateChange** イベントは、**Connection** の状態が変化したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="cd294-133">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="cd294-134">**StateChange** イベントは、**OriginalState** プロパティと **CurrentState** プロパティを使用して、**Connection** の状態の変化を判別できる <xref:System.Data.StateChangeEventArgs> を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="cd294-134">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="cd294-135">**OriginalState** プロパティは、**Connection** の状態が変更される前の状態を示す <xref:System.Data.ConnectionState> 列挙型です。</span><span class="sxs-lookup"><span data-stu-id="cd294-135">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="cd294-136">**CurrentState** は、**Connection** の状態が変更された後の状態を示す <xref:System.Data.ConnectionState> 列挙型です。</span><span class="sxs-lookup"><span data-stu-id="cd294-136">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="cd294-137">**StateChange** イベントを使用して **Connection** の状態が変化したときにコンソールにメッセージを出力するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cd294-137">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd294-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd294-138">See also</span></span>

- [<span data-ttu-id="cd294-139">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="cd294-139">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="cd294-140">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="cd294-140">ADO.NET Overview</span></span>](ado-net-overview.md)

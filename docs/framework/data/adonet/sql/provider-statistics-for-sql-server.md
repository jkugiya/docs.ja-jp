---
description: '詳細情報: SQL Server のプロバイダー統計情報'
title: SQL Server のプロバイダー統計情報
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: ece5a6214d438ecac64e8738755d5fb5d0ed7245
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767597"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="621e1-103">SQL Server のプロバイダー統計情報</span><span class="sxs-lookup"><span data-stu-id="621e1-103">Provider Statistics for SQL Server</span></span>

<span data-ttu-id="621e1-104">.NET Framework version 2.0 以降では、.NET Framework Data Provider for SQL Server によって実行時の統計がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="621e1-104">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="621e1-105">統計情報を有効にするには、有効な接続オブジェクトを作成した後で、<xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> プロパティを `True` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="621e1-105">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="621e1-106">統計情報が有効になったら、<xref:System.Data.SqlClient.SqlConnection> オブジェクトの <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> メソッドを使用して、<xref:System.Collections.IDictionary> 参照を取得することにより、それらを "特定の時点のスナップショット" として確認できます。</span><span class="sxs-lookup"><span data-stu-id="621e1-106">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="621e1-107">名前と値のペアの辞書エントリのセットとしてリストを列挙します。</span><span class="sxs-lookup"><span data-stu-id="621e1-107">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="621e1-108">これらの名前と値のペアは順不同です。</span><span class="sxs-lookup"><span data-stu-id="621e1-108">These name/value pairs are unordered.</span></span> <span data-ttu-id="621e1-109">カウンターはいつでも、<xref:System.Data.SqlClient.SqlConnection> オブジェクトの <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> メソッドを呼び出してリセットできます。</span><span class="sxs-lookup"><span data-stu-id="621e1-109">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="621e1-110">統計情報の収集が有効にされていない場合、例外は生成されません。</span><span class="sxs-lookup"><span data-stu-id="621e1-110">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="621e1-111">さらに、最初に <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> を呼び出すことなく <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> が呼び出された場合、取得される値は各エントリの初期値になります。</span><span class="sxs-lookup"><span data-stu-id="621e1-111">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="621e1-112">統計を有効にし、アプリケーションをしばらく実行してから統計を無効にした場合、取得される値には、統計を無効にした時点までに収集された値が反映されます。</span><span class="sxs-lookup"><span data-stu-id="621e1-112">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="621e1-113">すべての統計情報の値は、接続ごとに収集されます。</span><span class="sxs-lookup"><span data-stu-id="621e1-113">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="621e1-114">使用できる統計情報の値</span><span class="sxs-lookup"><span data-stu-id="621e1-114">Statistical Values Available</span></span>  

 <span data-ttu-id="621e1-115">現在、Microsoft SQL Server プロバイダーから使用できる項目は 18 種類あります。</span><span class="sxs-lookup"><span data-stu-id="621e1-115">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="621e1-116">使用できる項目の数を確認するには、<xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> により返される <xref:System.Collections.IDictionary> インターフェイス参照の **Count** プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="621e1-116">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="621e1-117">プロバイダーの統計情報のカウンターはすべて、64 ビット幅である共通言語ランタイムの <xref:System.Int64> 型 (C# と Visual Basic の場合は **long**) を使用します。</span><span class="sxs-lookup"><span data-stu-id="621e1-117">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="621e1-118">**int64** データ型の最大値は、**int64.MaxValue** フィールドにより定義されているように、((2^63)-1)) です。</span><span class="sxs-lookup"><span data-stu-id="621e1-118">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="621e1-119">カウンターの値がこの最大値に達すると、正確であると見なされなくなります。</span><span class="sxs-lookup"><span data-stu-id="621e1-119">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="621e1-120">つまり、**int64.MaxValue**-1((2^63)-2) は、事実上、すべての統計情報について有効な値の最大値になります。</span><span class="sxs-lookup"><span data-stu-id="621e1-120">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="621e1-121">返される統計の数、名前、および順序は将来変更される可能性があるため、プロバイダー統計情報を返す場合には、辞書を使用します。</span><span class="sxs-lookup"><span data-stu-id="621e1-121">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="621e1-122">アプリケーションでは、辞書にある特定の値に依存しないようにする必要がありますが、その値が存在するかどうかを確認し、それに応じて分岐する必要があります。</span><span class="sxs-lookup"><span data-stu-id="621e1-122">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="621e1-123">次の表では、使用可能な現在の統計情報の値が説明されています。</span><span class="sxs-lookup"><span data-stu-id="621e1-123">The following table describes the current statistical values available.</span></span> <span data-ttu-id="621e1-124">個々の値のキー名は、Microsoft .NET Framework の地域別バージョン全体でローカライズされているわけではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="621e1-124">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="621e1-125">キー名</span><span class="sxs-lookup"><span data-stu-id="621e1-125">Key Name</span></span>|<span data-ttu-id="621e1-126">説明</span><span class="sxs-lookup"><span data-stu-id="621e1-126">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="621e1-127">アプリケーションがプロバイダーの使用を開始し、統計情報が有効になった後に、SQL Server からプロバイダーが受信した表形式データ ストリーム (TDS) パケットの数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-127">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="621e1-128">統計が有効になった後にプロバイダーから SQL Server に送信された TDS パケットの数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-128">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="621e1-129">大規模なコマンドでは、複数のバッファーが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="621e1-129">Large commands can require multiple buffers.</span></span> <span data-ttu-id="621e1-130">たとえば、大規模なコマンドがサーバーに送信され、6 個のパケットが必要な場合、`ServerRoundtrips` は 1 ずつ増え、`BuffersSent` は 6 ずつ増えます。</span><span class="sxs-lookup"><span data-stu-id="621e1-130">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="621e1-131">アプリケーションがプロバイダーの使用を開始し、統計情報が有効になった後に、SQL Server からプロバイダーが受信した TDS パケット内のデータのバイト数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-131">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="621e1-132">アプリケーションがプロバイダーの使用を開始し、統計情報が有効になった後に、TDS パケットで SQL Server に送信されるデータのバイト数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-132">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="621e1-133">統計情報が有効になった後に接続が開かれている時間 (ミリ秒) を示します (接続が開かれる前に統計情報が有効になっていた場合は、合計接続時間を示します)。</span><span class="sxs-lookup"><span data-stu-id="621e1-133">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="621e1-134">アプリケーションがプロバイダーの使用を開始し、統計情報が有効になった後に、接続経由でカーソルが開かれた回数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-134">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="621e1-135">SELECT ステートメントから返された読み取り専用/順方向専用の結果は、カーソルとは見なされないため、このカウンターには影響しません。</span><span class="sxs-lookup"><span data-stu-id="621e1-135">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="621e1-136">統計情報が有効になってから、プロバイダーが処理に費やした累計時間 (ミリ秒) を返します。この時間には、サーバーからの応答を待つために費やされた時間と、プロバイダー自体がコードを実行するために費やした時間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="621e1-136">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="621e1-137">タイミング コードが含まれるクラスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="621e1-137">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="621e1-138">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="621e1-138">SqlConnection</span></span><br /><br /> <span data-ttu-id="621e1-139">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="621e1-139">SqlCommand</span></span><br /><br /> <span data-ttu-id="621e1-140">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="621e1-140">SqlDataReader</span></span><br /><br /> <span data-ttu-id="621e1-141">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="621e1-141">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="621e1-142">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="621e1-142">SqlTransaction</span></span><br /><br /> <span data-ttu-id="621e1-143">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="621e1-143">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="621e1-144">パフォーマンスが重視されるメンバーをできるだけ小規模に保つため、次のメンバーは時刻指定されません。</span><span class="sxs-lookup"><span data-stu-id="621e1-144">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="621e1-145">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="621e1-145">SqlDataReader</span></span><br /><br /> <span data-ttu-id="621e1-146">this[] operator (all overloads)</span><span class="sxs-lookup"><span data-stu-id="621e1-146">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="621e1-147">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="621e1-147">GetBoolean</span></span><br /><br /> <span data-ttu-id="621e1-148">GetChar</span><span class="sxs-lookup"><span data-stu-id="621e1-148">GetChar</span></span><br /><br /> <span data-ttu-id="621e1-149">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="621e1-149">GetDateTime</span></span><br /><br /> <span data-ttu-id="621e1-150">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="621e1-150">GetDecimal</span></span><br /><br /> <span data-ttu-id="621e1-151">GetDouble</span><span class="sxs-lookup"><span data-stu-id="621e1-151">GetDouble</span></span><br /><br /> <span data-ttu-id="621e1-152">GetFloat</span><span class="sxs-lookup"><span data-stu-id="621e1-152">GetFloat</span></span><br /><br /> <span data-ttu-id="621e1-153">GetGuid</span><span class="sxs-lookup"><span data-stu-id="621e1-153">GetGuid</span></span><br /><br /> <span data-ttu-id="621e1-154">GetInt16</span><span class="sxs-lookup"><span data-stu-id="621e1-154">GetInt16</span></span><br /><br /> <span data-ttu-id="621e1-155">GetInt32</span><span class="sxs-lookup"><span data-stu-id="621e1-155">GetInt32</span></span><br /><br /> <span data-ttu-id="621e1-156">GetInt64</span><span class="sxs-lookup"><span data-stu-id="621e1-156">GetInt64</span></span><br /><br /> <span data-ttu-id="621e1-157">GetName</span><span class="sxs-lookup"><span data-stu-id="621e1-157">GetName</span></span><br /><br /> <span data-ttu-id="621e1-158">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="621e1-158">GetOrdinal</span></span><br /><br /> <span data-ttu-id="621e1-159">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="621e1-159">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="621e1-160">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="621e1-160">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="621e1-161">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="621e1-161">GetSqlByte</span></span><br /><br /> <span data-ttu-id="621e1-162">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="621e1-162">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="621e1-163">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="621e1-163">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="621e1-164">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="621e1-164">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="621e1-165">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="621e1-165">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="621e1-166">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="621e1-166">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="621e1-167">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="621e1-167">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="621e1-168">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="621e1-168">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="621e1-169">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="621e1-169">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="621e1-170">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="621e1-170">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="621e1-171">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="621e1-171">GetSqlString</span></span><br /><br /> <span data-ttu-id="621e1-172">GetString</span><span class="sxs-lookup"><span data-stu-id="621e1-172">GetString</span></span><br /><br /> <span data-ttu-id="621e1-173">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="621e1-173">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="621e1-174">アプリケーションがプロバイダーの使用を開始し、統計情報が有効になった後に、接続経由で実行された INSERT、DELETE、および UPDATE ステートメントの合計数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-174">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="621e1-175">アプリケーションがプロバイダーの使用を開始し、統計情報が有効になった後に、接続経由で実行された INSERT、DELETE、および UPDATE ステートメントによって影響を受ける行の合計数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-175">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="621e1-176">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後にプロバイダーがサーバーからの応答を待つために費やした累計時間 (ミリ秒) を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-176">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="621e1-177">アプリケーションがプロバイダーの使用を開始し、統計情報が有効になった後に、接続経由で実行された準備済みコマンドの数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-177">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="621e1-178">アプリケーションがプロバイダーの使用を開始し、統計情報が有効になった後に、接続経由で準備されたステートメントの数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-178">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="621e1-179">アプリケーションがプロバイダーの使用を開始し、統計情報が有効になった後に、接続経由で実行された SELECT ステートメントの数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-179">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="621e1-180">これには、カーソルから行を取得するための FETCH ステートメントが含まれ、<xref:System.Data.SqlClient.SqlDataReader> の末尾に達したときに SELECT ステートメントの数が更新されます。</span><span class="sxs-lookup"><span data-stu-id="621e1-180">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="621e1-181">アプリケーションがプロバイダーの使用を開始し、統計情報が有効になった後に、選択された行の数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-181">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="621e1-182">この数には、SQL ステートメントによって生成されたすべての行が反映され、呼び出し元によって実際に使用されなかった行も含まれます。</span><span class="sxs-lookup"><span data-stu-id="621e1-182">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="621e1-183">たとえば、結果セット全体を読み取る前にデータ リーダーを終了しても、数には影響しません。</span><span class="sxs-lookup"><span data-stu-id="621e1-183">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="621e1-184">これには、FETCH ステートメントによってカーソルから取得された行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="621e1-184">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="621e1-185">アプリケーションがプロバイダーの使用を開始し、統計情報が有効になった後に、接続によってコマンドがサーバーに送信され、応答が返された回数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-185">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="621e1-186">アプリケーションがプロバイダーの使用を開始し、統計情報が有効になった後に、使用された結果セットの数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-186">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="621e1-187">たとえば、これにはクライアントに返される結果セットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="621e1-187">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="621e1-188">カーソルの場合、各フェッチまたはブロックフェッチ操作は、独立した結果セットと見なされます。</span><span class="sxs-lookup"><span data-stu-id="621e1-188">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="621e1-189">アプリケーションがプロバイダーの使用を開始し、統計情報が有効になった後に、ロールバックを含む開始されたユーザー トランザクションの数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-189">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="621e1-190">自動コミットをオンにして接続が実行されている場合、各コマンドはトランザクションと見なされます。</span><span class="sxs-lookup"><span data-stu-id="621e1-190">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="621e1-191">このカウンターでは、後でトランザクションがコミットされるか、ロール バックされるかに関係なく、BEGIN TRAN ステートメントが実行されるとすぐにトランザクション数が増えます。</span><span class="sxs-lookup"><span data-stu-id="621e1-191">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="621e1-192">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて準備解除された、ステートメントの数を返します。</span><span class="sxs-lookup"><span data-stu-id="621e1-192">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="621e1-193">値の取得</span><span class="sxs-lookup"><span data-stu-id="621e1-193">Retrieving a Value</span></span>  

 <span data-ttu-id="621e1-194">次のコンソール アプリケーションは、接続で統計情報を有効にして、4 つの各統計情報の値を取得し、コンソール ウィンドウに出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="621e1-194">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="621e1-195">次の例では、SQL Server に含まれるサンプルの **AdventureWorks** データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="621e1-195">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="621e1-196">サンプル コードに示されている接続文字列は、データベースがローカル コンピューターにインストールされ、使用可能であることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="621e1-196">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="621e1-197">必要に応じて、お使いの環境に合わせて接続文字列を変更してください。</span><span class="sxs-lookup"><span data-stu-id="621e1-197">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="621e1-198">すべての値の取得</span><span class="sxs-lookup"><span data-stu-id="621e1-198">Retrieving All Values</span></span>  

 <span data-ttu-id="621e1-199">次のコンソール アプリケーションは、接続で統計情報を有効にし、使用可能なすべての統計情報の値を列挙子を使って取得して、コンソール ウィンドウに出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="621e1-199">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="621e1-200">次の例では、SQL Server に含まれるサンプルの **AdventureWorks** データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="621e1-200">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="621e1-201">サンプル コードに示されている接続文字列は、データベースがローカル コンピューターにインストールされ、使用可能であることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="621e1-201">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="621e1-202">必要に応じて、お使いの環境に合わせて接続文字列を変更してください。</span><span class="sxs-lookup"><span data-stu-id="621e1-202">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="621e1-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="621e1-203">See also</span></span>

- [<span data-ttu-id="621e1-204">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="621e1-204">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="621e1-205">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="621e1-205">ADO.NET Overview</span></span>](../ado-net-overview.md)

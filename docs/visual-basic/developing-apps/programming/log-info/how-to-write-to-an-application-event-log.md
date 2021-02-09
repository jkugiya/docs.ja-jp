---
description: '詳細情報: 方法:アプリケーション イベント ログに書き込む (Visual Basic)'
title: '方法: アプリケーション イベント ログに書き込む'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: ea53ff84f1fcf175912e35eb7433ece26886cf44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797290"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="499b1-103">方法: アプリケーション イベント ログに書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="499b1-103">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="499b1-104">`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報を書き込めます。</span><span class="sxs-lookup"><span data-stu-id="499b1-104">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="499b1-105">この例では、 `My.Application.Log` がアプリケーション イベント ログにトレース情報を書き込むようにイベント ログ リスナーを構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="499b1-105">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="499b1-106">セキュリティ ログに書き込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="499b1-106">You cannot write to the Security log.</span></span> <span data-ttu-id="499b1-107">システム ログに書き込むためには、LocalSystem または Administrator アカウントのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="499b1-107">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="499b1-108">イベント ログを参照するには、 **サーバー エクスプローラー** または **Windows イベント ビューアー** を使用できます。</span><span class="sxs-lookup"><span data-stu-id="499b1-108">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="499b1-109">詳細については、「 [.NET Framework の ETW イベント](../../../../framework/performance/etw-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="499b1-109">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

## <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="499b1-110">イベント ログ リスナーを追加および構成するには</span><span class="sxs-lookup"><span data-stu-id="499b1-110">To add and configure the event log listener</span></span>

1. <span data-ttu-id="499b1-111">**ソリューション エクスプローラー** で app.config を右クリックし、 **[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="499b1-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="499b1-112">\- または</span><span class="sxs-lookup"><span data-stu-id="499b1-112">\- or -</span></span>

    <span data-ttu-id="499b1-113">app.config ファイルがない場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="499b1-113">If there is no app.config file,</span></span>

    1. <span data-ttu-id="499b1-114">**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="499b1-114">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="499b1-115">**[新しい項目の追加]** ダイアログ ボックスで、 **[アプリケーション構成ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="499b1-115">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="499b1-116">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="499b1-116">Click **Add**.</span></span>

2. <span data-ttu-id="499b1-117">アプリケーション構成ファイルで `<listeners>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="499b1-117">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="499b1-118">`<listeners>` セクションは、最上位の `<source>` セクションに入れ子になった `<system.diagnostics>` セクションにさらに入れ子になっている、名前属性が "DefaultSource" の `<configuration>` セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="499b1-118">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="499b1-119">その `<listeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="499b1-119">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="499b1-120">最上位の `<sharedListeners>` セクション内の `<system.diagnostics>` セクションで、 `<configuration>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="499b1-120">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="499b1-121">その `<sharedListeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="499b1-121">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="499b1-122">`APPLICATION_NAME` をアプリケーションの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="499b1-122">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="499b1-123">通常、アプリケーションがイベント ログに書き込むのはエラーのみです。</span><span class="sxs-lookup"><span data-stu-id="499b1-123">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="499b1-124">ログ出力のフィルター処理の詳細については、「 [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="499b1-124">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md).</span></span>

## <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="499b1-125">イベント情報をイベント ログに書き込むには</span><span class="sxs-lookup"><span data-stu-id="499b1-125">To write event information to the event log</span></span>

<span data-ttu-id="499b1-126">`My.Application.Log.WriteEntry` メソッドまたは `My.Application.Log.WriteException` メソッドを使用して、イベント ログに情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="499b1-126">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="499b1-127">詳しくは、「[方法: ログ メッセージを書き込む](how-to-write-log-messages.md)」および「[方法: 例外をログに記録する](how-to-log-exceptions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="499b1-127">For more information, see [How to: Write Log Messages](how-to-write-log-messages.md) and [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

<span data-ttu-id="499b1-128">アセンブリに対してイベント ログ リスナーを設定すると、そのアセンブリで `My.Application.Log` が書き込んだすべてのメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="499b1-128">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="499b1-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="499b1-129">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="499b1-130">アプリケーション ログの使用</span><span class="sxs-lookup"><span data-stu-id="499b1-130">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="499b1-131">方法: 例外をログに記録する</span><span class="sxs-lookup"><span data-stu-id="499b1-131">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="499b1-132">チュートリアル: My.Application.Log による情報の書き込み先の確認</span><span class="sxs-lookup"><span data-stu-id="499b1-132">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)

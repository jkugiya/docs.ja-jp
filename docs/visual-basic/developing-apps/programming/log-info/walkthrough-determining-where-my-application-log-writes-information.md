---
description: '詳細情報: チュートリアル: My.Application.Log による情報の書き込み先の確認 (Visual Basic)'
title: My.Application.Log による情報の書き込み先の確認
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: 4ddb5777bcbdde07069efd2fd3a66f0c220ee135
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792285"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="66d3c-103">チュートリアル: My.Application.Log による情報の書き込み先の確認 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66d3c-103">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="66d3c-104">`My.Application.Log` オブジェクトは、複数のログ リスナーに情報を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-104">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="66d3c-105">ログ リスナーは、コンピューターの構成ファイルで設定し、アプリケーションの構成ファイルでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-105">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="66d3c-106">このトピックでは、既定の設定について、およびアプリケーションの設定を確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="66d3c-106">This topic describes the default settings and how to determine the settings for your application.</span></span>

<span data-ttu-id="66d3c-107">既定の出力場所について詳しくは、「[アプリケーション ログの使用](working-with-application-logs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66d3c-107">For more information about the default output locations, see [Working with Application Logs](working-with-application-logs.md).</span></span>

### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="66d3c-108">My.Application.Log のリスナーを確認するには</span><span class="sxs-lookup"><span data-stu-id="66d3c-108">To determine the listeners for My.Application.Log</span></span>

1. <span data-ttu-id="66d3c-109">アセンブリの構成ファイルを見つけます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-109">Locate the assembly's configuration file.</span></span> <span data-ttu-id="66d3c-110">アセンブリを開発中の段階では、**ソリューション エクスプローラー** から Visual Studio の app.config にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-110">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="66d3c-111">開発が終了すると、構成ファイルはアセンブリの名前に ".config" を付け加えたファイル名で、アセンブリと同じディレクトリに配置されています。</span><span class="sxs-lookup"><span data-stu-id="66d3c-111">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="66d3c-112">アセンブリによっては、構成ファイルがない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="66d3c-112">Not every assembly has a configuration file.</span></span>

    <span data-ttu-id="66d3c-113">構成ファイルは XML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="66d3c-113">The configuration file is an XML file.</span></span>

2. <span data-ttu-id="66d3c-114">`<listeners>` セクション内にある、 `<source>` 属性が "DefaultSource" の `name` セクションで、 `<sources>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-114">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="66d3c-115">`<sources>` セクションは、最上位の `<system.diagnostics>` セクション内の `<configuration>` セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="66d3c-115">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

    <span data-ttu-id="66d3c-116">これらのセクションがない場合には、 `My.Application.Log` のログ リスナーは、コンピューターの構成ファイルで設定されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="66d3c-116">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="66d3c-117">以下の手順は、コンピューターの構成ファイルの定義を確認する方法の説明です。</span><span class="sxs-lookup"><span data-stu-id="66d3c-117">The following steps describe how to determine what the computer configuration file defines:</span></span>

    1. <span data-ttu-id="66d3c-118">コンピューターの machine.config ファイルを見つけます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-118">Locate the computer's machine.config file.</span></span> <span data-ttu-id="66d3c-119">通常は、*SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* ディレクトリにあります。`SystemRoot` はオペレーティング システム ディレクトリであり、`frameworkVersion` は .NET Framework のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="66d3c-119">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the .NET Framework.</span></span>

        <span data-ttu-id="66d3c-120">machine.config の設定は、アプリケーションの構成ファイルでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-120">The settings in machine.config can be overridden by an application's configuration file.</span></span>

        <span data-ttu-id="66d3c-121">以下に示すオプションの要素が存在しない場合には、自分で作成できます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-121">If the optional elements listed below do not exist, you can create them.</span></span>

    2. <span data-ttu-id="66d3c-122">最上位の `<listeners>` セクション内にある `<source>` セクション内の `name` セクションで、 `<sources>` 属性が "DefaultSource" の `<system.diagnostics>` セクション内の `<configuration>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-122">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

        <span data-ttu-id="66d3c-123">これらのセクションがない場合、 `My.Application.Log` にあるのは既定のログ リスナーのみです。</span><span class="sxs-lookup"><span data-stu-id="66d3c-123">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>

3. <span data-ttu-id="66d3c-124"><`listeners>` セクションで <`add>` 要素を見つけます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-124">Locate the <`add>` elements in the <`listeners>` section.</span></span>

     <span data-ttu-id="66d3c-125">これらの要素は、名前付きのログ リスナーを `My.Application.Log` のソースに追加します。</span><span class="sxs-lookup"><span data-stu-id="66d3c-125">These elements add the named log listeners to `My.Application.Log` source.</span></span>

4. <span data-ttu-id="66d3c-126">最上位の `<add>` セクション内にある `<sharedListeners>` セクション内の `<system.diagnostics>` セクションで、ログ リスナーの名前の `<configuration>` 要素を見つけます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-126">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="66d3c-127">多くの型の共有リスナーでは、リスナーがデータを書き込む先は、リスナーの初期化データで指定されています。</span><span class="sxs-lookup"><span data-stu-id="66d3c-127">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>

    - <span data-ttu-id="66d3c-128"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> リスナーは、導入部で説明したように、ファイル ログに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-128">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>

    - <span data-ttu-id="66d3c-129"><xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> リスナーは、 `initializeData` パラメーターで指定された、コンピューターのイベント ログに情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-129">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="66d3c-130">イベント ログを参照するには、 **サーバー エクスプローラー** または **Windows イベント ビューアー** を使用できます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-130">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="66d3c-131">詳細については、「 [.NET Framework の ETW イベント](../../../../framework/performance/etw-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66d3c-131">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

    - <span data-ttu-id="66d3c-132"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> リスナーおよび <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> リスナーは、 `initializeData` パラメーターで指定されたファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-132">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="66d3c-133"><xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> リスナーは、コマンド ライン コンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="66d3c-133">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>

    - <span data-ttu-id="66d3c-134">他の型のログ リスナーが情報を書き込む先については、その型のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="66d3c-134">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="66d3c-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="66d3c-135">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [<span data-ttu-id="66d3c-136">アプリケーション ログの使用</span><span class="sxs-lookup"><span data-stu-id="66d3c-136">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="66d3c-137">方法: 例外をログに記録する</span><span class="sxs-lookup"><span data-stu-id="66d3c-137">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="66d3c-138">方法: ログ メッセージを書き込む</span><span class="sxs-lookup"><span data-stu-id="66d3c-138">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="66d3c-139">チュートリアル: My.Application.Log による情報の書き込み先の変更</span><span class="sxs-lookup"><span data-stu-id="66d3c-139">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="66d3c-140">.NET Framework の ETW イベント</span><span class="sxs-lookup"><span data-stu-id="66d3c-140">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)
- [<span data-ttu-id="66d3c-141">トラブルシューティング : ログ リスナー</span><span class="sxs-lookup"><span data-stu-id="66d3c-141">Troubleshooting: Log Listeners</span></span>](troubleshooting-log-listeners.md)

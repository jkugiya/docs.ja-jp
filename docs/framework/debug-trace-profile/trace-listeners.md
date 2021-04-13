---
title: トレース リスナー
description: .NET 内で送信されたトレース メッセージを収集して記録するためのメカニズムであるトレース リスナーについて調べます。 リスナーでは、メッセージが収集、格納、およびルーティングされます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Listener object types
- listeners
- Trace class, listeners
- trace listeners, about trace listeners
- Listeners collection
- trace listeners
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 444b0d33-67ea-4c36-9e94-79c50f839025
ms.openlocfilehash: 8cd79d21d66d23f834b7ef0012d8360884028ac6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238120"
---
# <a name="trace-listeners"></a><span data-ttu-id="c30fa-104">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="c30fa-104">Trace Listeners</span></span>

<span data-ttu-id="c30fa-105">**Trace**、**Debug**、および <xref:System.Diagnostics.TraceSource> を使用するときには、送信されたメッセージを収集して記録するための機構が必要です。</span><span class="sxs-lookup"><span data-stu-id="c30fa-105">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="c30fa-106">トレース メッセージは *リスナー* によって受け取られます。</span><span class="sxs-lookup"><span data-stu-id="c30fa-106">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="c30fa-107">リスナーの目的は、トレース メッセージの収集、格納、およびルーティングを行うことです。</span><span class="sxs-lookup"><span data-stu-id="c30fa-107">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="c30fa-108">リスナーにより、トレース出力が適切な場所 (ログ、ウィンドウ、またはテキスト ファイル) に送られます。</span><span class="sxs-lookup"><span data-stu-id="c30fa-108">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="c30fa-109">リスナーは、**Debug**、**Trace**、および <xref:System.Diagnostics.TraceSource> の各クラスで使用できます。それらのクラスからも出力を各種のリスナー オブジェクトに送ることができます。</span><span class="sxs-lookup"><span data-stu-id="c30fa-109">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="c30fa-110">一般的に使用される定義済みのリスナーは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c30fa-110">The following are the commonly used predefined listeners:</span></span>  
  
- <span data-ttu-id="c30fa-111"><xref:System.Diagnostics.TextWriterTraceListener> は、<xref:System.IO.TextWriter> クラスのインスタンスまたは <xref:System.IO.Stream> クラスの任意の対象に出力をリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="c30fa-111">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="c30fa-112">また、コンソールまたはファイルに書き込むこともできます (これらは <xref:System.IO.Stream> クラスなので)。</span><span class="sxs-lookup"><span data-stu-id="c30fa-112">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
- <span data-ttu-id="c30fa-113"><xref:System.Diagnostics.EventLogTraceListener> は、出力をイベント ログにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="c30fa-113">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
- <span data-ttu-id="c30fa-114"><xref:System.Diagnostics.DefaultTraceListener> は、**Write** メッセージと **WriteLine** メッセージを **OutputDebugString** と **Debugger.Log** メソッドに出力します。</span><span class="sxs-lookup"><span data-stu-id="c30fa-114">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="c30fa-115">Visual Studio では、これによってデバッグ メッセージが [出力] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c30fa-115">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="c30fa-116">**Fail** メッセージと、失敗した **Assert** メッセージも **OutputDebugString** Windows API と **Debugger.Log** メソッドに出力され、これらはメッセージ ボックスとしても表示されます。</span><span class="sxs-lookup"><span data-stu-id="c30fa-116">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="c30fa-117">**DefaultTraceListener** はすべての `Listeners` コレクションに自動的に取り込まれる唯一のリスナーであるため、この動作は **Debug** メッセージと **Trace** メッセージの既定の動作になります。</span><span class="sxs-lookup"><span data-stu-id="c30fa-117">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
- <span data-ttu-id="c30fa-118"><xref:System.Diagnostics.ConsoleTraceListener> は、トレース出力またはデバッグ出力を、標準出力と標準エラー出力ストリームのいずれかに転送します。</span><span class="sxs-lookup"><span data-stu-id="c30fa-118">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
- <span data-ttu-id="c30fa-119"><xref:System.Diagnostics.DelimitedListTraceListener> は、トレース出力またはデバッグ出力を、テキスト ライター (ストリーム ライターなど) またはストリーム (ファイル ストリームなど) に送ります。</span><span class="sxs-lookup"><span data-stu-id="c30fa-119">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="c30fa-120">トレース出力は、<xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> プロパティによって指定された区切り記号を使用する、区切られたテキスト形式です。</span><span class="sxs-lookup"><span data-stu-id="c30fa-120">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
- <span data-ttu-id="c30fa-121"><xref:System.Diagnostics.XmlWriterTraceListener> は、トレース出力またはデバッグ出力を、XML でエンコードされたデータとして <xref:System.IO.TextWriter> または <xref:System.IO.Stream> (<xref:System.IO.FileStream> など) に送ります。</span><span class="sxs-lookup"><span data-stu-id="c30fa-121">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="c30fa-122"><xref:System.Diagnostics.DefaultTraceListener> 以外のリスナーが **Debug** 出力、**Trace** 出力、および <xref:System.Diagnostics.TraceSource> 出力を受け取るようにする場合は、目的のリスナーを `Listeners` コレクションに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c30fa-122">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="c30fa-123">詳細については、「[方法 : トレース リスナーを作成し初期化する](how-to-create-and-initialize-trace-listeners.md)」と「[方法 : TraceSource とフィルターをトレース リスナーと共に使用する](how-to-use-tracesource-and-filters-with-trace-listeners.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c30fa-123">For more information, see [How to: Create and Initialize Trace Listeners](how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="c30fa-124">**Listeners** コレクションのすべてのリスナーは、トレース出力のメソッドから同じメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c30fa-124">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="c30fa-125">たとえば、**TextWriterTraceListener** と **EventLogTraceListener** という 2 つのリスナーを設定したとします。</span><span class="sxs-lookup"><span data-stu-id="c30fa-125">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="c30fa-126">各リスナーは同一のメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c30fa-126">Each listener receives the same message.</span></span> <span data-ttu-id="c30fa-127">この場合、**TextWriterTraceListener** はストリームに出力を送り、**EventLogTraceListener** はイベント ログに出力を送るなどの動作が可能です。</span><span class="sxs-lookup"><span data-stu-id="c30fa-127">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="c30fa-128">出力を **Listeners** コレクションに送る方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="c30fa-128">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
```vb  
' Use this example when debugging.  
Debug.WriteLine("Error in Widget 42")  
' Use this example when tracing.  
Trace.WriteLine("Error in Widget 42")  
```  
  
```csharp  
// Use this example when debugging.  
System.Diagnostics.Debug.WriteLine("Error in Widget 42");  
// Use this example when tracing.  
System.Diagnostics.Trace.WriteLine("Error in Widget 42");  
```  
  
 <span data-ttu-id="c30fa-129">デバッグとトレースは、同じ **Listeners** コレクションを共有しています。したがって、リスナー オブジェクトをアプリケーションの **Debug.Listeners** コレクションに追加した場合、そのリスナー オブジェクトは **Trace.Listeners** コレクションにも追加されます。</span><span class="sxs-lookup"><span data-stu-id="c30fa-129">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="c30fa-130">トレース情報をコンソールに送る場合のリスナーの使用方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="c30fa-130">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="c30fa-131">開発者が定義するリスナー</span><span class="sxs-lookup"><span data-stu-id="c30fa-131">Developer-Defined Listeners</span></span>  

 <span data-ttu-id="c30fa-132">**TraceListener** 基底クラスから継承することにより、独自のリスナーを定義し、カスタマイズされたメソッドで既存のメソッドをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="c30fa-132">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="c30fa-133">開発者が定義するリスナーの作成については、「.NET Framework リファレンス」の「<xref:System.Diagnostics.TraceListener>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c30fa-133">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c30fa-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="c30fa-134">See also</span></span>

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="c30fa-135">アプリケーションのトレースとインストルメント</span><span class="sxs-lookup"><span data-stu-id="c30fa-135">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="c30fa-136">トレース スイッチ</span><span class="sxs-lookup"><span data-stu-id="c30fa-136">Trace Switches</span></span>](trace-switches.md)

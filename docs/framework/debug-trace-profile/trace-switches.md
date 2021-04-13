---
title: トレース スイッチ
description: トレース出力を有効または無効にしたり、フィルター処理したりできるトレース スイッチについて調べます。 .NET には、BooleanSwitch、TraceSwitch、および SourceSwitch クラスが用意されています。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], trace switches
- trace switches, about trace switches
- tracing [.NET Framework], level of detail
- switches, trace
- trace switches
- trace switches, creating custom
ms.assetid: 8ab913aa-f400-4406-9436-f45bc6e54fbe
ms.openlocfilehash: dfbff0a78b3c6c1318224ccc9608c1b816f9d5f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238055"
---
# <a name="trace-switches"></a><span data-ttu-id="d5f4c-104">トレース スイッチ</span><span class="sxs-lookup"><span data-stu-id="d5f4c-104">Trace Switches</span></span>

<span data-ttu-id="d5f4c-105">トレース スイッチを使用すると、トレース出力を有効/無効にしたり、トレースの出力をフィルター処理したりできます。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-105">Trace switches enable you to enable, disable, and filter tracing output.</span></span> <span data-ttu-id="d5f4c-106">トレース スイッチは、コードに存在すれるオブジェクトであり、.config ファイルによって外部的に設定できます。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-106">They are objects that exist in your code and can be configured externally through the .config file.</span></span> <span data-ttu-id="d5f4c-107">.NET Framework に用意されたトレース スイッチには、 <xref:System.Diagnostics.BooleanSwitch> クラス、 <xref:System.Diagnostics.TraceSwitch> クラス、および <xref:System.Diagnostics.SourceSwitch> クラスの 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-107">There are three types of trace switches provided in the .NET Framework: the <xref:System.Diagnostics.BooleanSwitch> class, the <xref:System.Diagnostics.TraceSwitch> class, and the <xref:System.Diagnostics.SourceSwitch> class.</span></span> <span data-ttu-id="d5f4c-108"><xref:System.Diagnostics.BooleanSwitch> クラスは、トグル スイッチとして機能し、各種のトレース ステートメントを有効にしたり無効にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-108">The <xref:System.Diagnostics.BooleanSwitch> class acts as a toggle switch, either enabling or disabling a variety of trace statements.</span></span> <span data-ttu-id="d5f4c-109"><xref:System.Diagnostics.TraceSwitch> クラスと <xref:System.Diagnostics.SourceSwitch> クラスを使用すると、特定のトレース レベルごとにトレース スイッチを有効にすることができます。これにより、該当するレベルおよびそれ以下のすべてのレベルに対して指定された <xref:System.Diagnostics.Trace> メッセージまたは <xref:System.Diagnostics.TraceSource> メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-109">The <xref:System.Diagnostics.TraceSwitch> and <xref:System.Diagnostics.SourceSwitch> classes allow you to enable a trace switch for a particular tracing level so that the <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.TraceSource> messages specified for that level and all levels below it appear.</span></span> <span data-ttu-id="d5f4c-110">スイッチを無効にした場合、トレース メッセージは表示されません。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-110">If you disable the switch, the trace messages will not appear.</span></span> <span data-ttu-id="d5f4c-111">すべてのクラスは、他のユーザー定義のスイッチと同様に、どちらも **Switch** という抽象 ( **MustInherit**) クラスから派生したクラスです。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-111">All these classes derive from the abstract (**MustInherit**) class **Switch**, as should any user-developed switches.</span></span>  
  
 <span data-ttu-id="d5f4c-112">トレース スイッチは情報のフィルター処理に役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-112">Trace switches can be useful for filtering information.</span></span> <span data-ttu-id="d5f4c-113">たとえば、データ アクセス モジュールではすべてのトレース メッセージを表示し、アプリケーションの他の部分ではエラー メッセージだけを表示できます。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-113">For example, you might want to see every tracing message in a data access module, but only error messages in the rest of the application.</span></span> <span data-ttu-id="d5f4c-114">この場合は、データ アクセス モジュールに対してトレース スイッチを 1 つ使用し、アプリケーションの他の部分に対してスイッチを 1 つ使用します。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-114">In that case, you would use one trace switch for the data access module and one switch for the rest of the application.</span></span> <span data-ttu-id="d5f4c-115">.config ファイルの構成でスイッチを適切に設定することにより、受け取るトレース メッセージの種類を制御できます。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-115">By using the .config file to configure the switches to the appropriate settings, you could control what types of trace message you received.</span></span> <span data-ttu-id="d5f4c-116">詳細については、「[方法 : トレース スイッチを作成、初期化、および構成する](how-to-create-initialize-and-configure-trace-switches.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-116">For more information, see [How to: Create, Initialize and Configure Trace Switches](how-to-create-initialize-and-configure-trace-switches.md).</span></span>  
  
 <span data-ttu-id="d5f4c-117">一般に、配置されたアプリケーションはスイッチが無効にされた状態で実行されるため、ユーザーにとって意味のないトレース メッセージが画面に表示されたり、アプリケーションの実行ごとにログ ファイルに書き込んだりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-117">Typically, a deployed application is executed with its switches disabled, so that users need not observe a lot of irrelevant trace messages appearing on a screen or filling up a log file as the application runs.</span></span> <span data-ttu-id="d5f4c-118">アプリケーションの実行時に問題が発生した場合は、アプリケーションを中断し、スイッチを有効にしてからアプリケーションを再起動します。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-118">If a problem arises during application execution, you can stop the application, enable the switches, and restart the application.</span></span> <span data-ttu-id="d5f4c-119">これにより、トレース メッセージが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-119">Then the tracing messages will be displayed.</span></span>  
  
 <span data-ttu-id="d5f4c-120">スイッチを使用するには、まず、 **BooleanSwitch** クラス、 **TraceSwitch** クラス、または開発者が定義したスイッチ クラスからスイッチ オブジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-120">To use a switch you must first create a switch object from a **BooleanSwitch** class, a **TraceSwitch** class, or a developer-defined switch class.</span></span> <span data-ttu-id="d5f4c-121">開発者定義スイッチの作成方法については、「.NET Framework リファレンス」の「 <xref:System.Diagnostics.Switch> クラス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-121">For more information about creating developer-defined switches, see the <xref:System.Diagnostics.Switch> class in the .NET Framework reference.</span></span> <span data-ttu-id="d5f4c-122">次に、スイッチ オブジェクトを使用するタイミングを指定する構成値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-122">Then you set a configuration value that specifies when the switch object is to be used.</span></span> <span data-ttu-id="d5f4c-123">その後で、スイッチ オブジェクトの設定を各種の **Trace** (または **Debug**) トレース メソッドでテストします。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-123">You then test the setting of the switch object in various **Trace** (or **Debug**) tracing methods.</span></span>  
  
## <a name="trace-levels"></a><span data-ttu-id="d5f4c-124">トレース レベル</span><span class="sxs-lookup"><span data-stu-id="d5f4c-124">Trace Levels</span></span>  

 <span data-ttu-id="d5f4c-125">**TraceSwitch** を使用するときには、いくつかの付加的な考慮事項があります。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-125">When you use **TraceSwitch**, there are additional considerations.</span></span> <span data-ttu-id="d5f4c-126">**TraceSwitch** オブジェクトには、スイッチを特定のレベル以上として設定するかどうかを示す **Boolean** 値を返す、4 つのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-126">A **TraceSwitch** object has four properties that return **Boolean** values indicating whether the switch is set to at least a particular level:</span></span>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="d5f4c-127">レベルを使用することにより、受け取るトレース情報を問題解決に必要な情報だけに制限できます。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-127">Levels allow you to limit the amount of tracing information you receive to only that information needed to solve a problem.</span></span> <span data-ttu-id="d5f4c-128">トレース スイッチを適切なトレース レベルに設定したり構成したりして、トレース出力に必要な詳細レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-128">You specify the level of detail you want in your tracing output by setting and configuring trace switches to the appropriate trace level.</span></span> <span data-ttu-id="d5f4c-129">エラー メッセージ、警告メッセージ、情報メッセージ、または詳細トレース メッセージを受け取ることができます。また、メッセージを一切受け取らないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-129">You can receive error messages, warning messages, informational messages, verbose tracing messages, or no message at all.</span></span>  
  
 <span data-ttu-id="d5f4c-130">各レベルに関連付けるメッセージの種類は、すべて開発者が指定します。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-130">It is entirely up to you to decide what kind of message to associate with each level.</span></span> <span data-ttu-id="d5f4c-131">トレース メッセージの内容は、通常、各レベルに関連付けた内容に依存しますが、レベルごとに動作の違いを設定できます。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-131">Typically, the content of tracing messages depends on what you associate with each level, but you determine the differences between levels.</span></span> <span data-ttu-id="d5f4c-132">たとえば、レベル 3 (**Info**) の問題については詳細な説明を提供するが、レベル 1 (**Error**) の問題についてはエラー参照番号だけを提供する場合があります。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-132">You might want to provide detailed descriptions of a problem at level 3 (**Info**), for example, but provide only an error reference number at level 1 (**Error**).</span></span> <span data-ttu-id="d5f4c-133">アプリケーションで最適な動作を得ることができるスキームは、独自に判断してください。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-133">It is entirely up to you to decide what scheme works best in your application.</span></span>  
  
 <span data-ttu-id="d5f4c-134">これらのプロパティは、 **TraceLevel** 列挙型の値 1 から 4 に対応します。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-134">These properties correspond to the values 1 through 4 of the **TraceLevel** enumeration.</span></span> <span data-ttu-id="d5f4c-135">**TraceLevel** 列挙型のレベルとそれぞれの値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-135">The following table lists the levels of the **TraceLevel** enumeration and their values.</span></span>  
  
|<span data-ttu-id="d5f4c-136">列挙値</span><span class="sxs-lookup"><span data-stu-id="d5f4c-136">Enumerated value</span></span>|<span data-ttu-id="d5f4c-137">整数値</span><span class="sxs-lookup"><span data-stu-id="d5f4c-137">Integer value</span></span>|<span data-ttu-id="d5f4c-138">表示されるメッセージ (または指定された出力対象に書き込まれるメッセージ) の種類</span><span class="sxs-lookup"><span data-stu-id="d5f4c-138">Type of message displayed (or written to a specified output target)</span></span>|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|<span data-ttu-id="d5f4c-139">オフ</span><span class="sxs-lookup"><span data-stu-id="d5f4c-139">Off</span></span>|<span data-ttu-id="d5f4c-140">0</span><span class="sxs-lookup"><span data-stu-id="d5f4c-140">0</span></span>|<span data-ttu-id="d5f4c-141">なし</span><span class="sxs-lookup"><span data-stu-id="d5f4c-141">None</span></span>|  
|<span data-ttu-id="d5f4c-142">エラー</span><span class="sxs-lookup"><span data-stu-id="d5f4c-142">Error</span></span>|<span data-ttu-id="d5f4c-143">1</span><span class="sxs-lookup"><span data-stu-id="d5f4c-143">1</span></span>|<span data-ttu-id="d5f4c-144">エラー メッセージのみ</span><span class="sxs-lookup"><span data-stu-id="d5f4c-144">Only error messages</span></span>|  
|<span data-ttu-id="d5f4c-145">警告</span><span class="sxs-lookup"><span data-stu-id="d5f4c-145">Warning</span></span>|<span data-ttu-id="d5f4c-146">2</span><span class="sxs-lookup"><span data-stu-id="d5f4c-146">2</span></span>|<span data-ttu-id="d5f4c-147">警告メッセージとエラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="d5f4c-147">Warning messages and error messages</span></span>|  
|<span data-ttu-id="d5f4c-148">Info</span><span class="sxs-lookup"><span data-stu-id="d5f4c-148">Info</span></span>|<span data-ttu-id="d5f4c-149">3</span><span class="sxs-lookup"><span data-stu-id="d5f4c-149">3</span></span>|<span data-ttu-id="d5f4c-150">通知メッセージ、警告メッセージ、およびエラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="d5f4c-150">Informational messages, warning messages, and error messages</span></span>|  
|<span data-ttu-id="d5f4c-151">"詳細"</span><span class="sxs-lookup"><span data-stu-id="d5f4c-151">Verbose</span></span>|<span data-ttu-id="d5f4c-152">4</span><span class="sxs-lookup"><span data-stu-id="d5f4c-152">4</span></span>|<span data-ttu-id="d5f4c-153">詳細メッセージ、情報メッセージ、警告メッセージ、およびエラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="d5f4c-153">Verbose messages, informational messages, warning messages, and error messages</span></span>|  
  
 <span data-ttu-id="d5f4c-154">**TraceSwitch** のプロパティは、スイッチの最大トレース レベルを示します。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-154">The **TraceSwitch** properties indicate the maximum trace level for the switch.</span></span> <span data-ttu-id="d5f4c-155">つまり、指定されたレベルとそれ以下のすべてのレベルについて、トレース情報が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-155">That is, tracing information is written for the level specified as well as for all lower levels.</span></span> <span data-ttu-id="d5f4c-156">たとえば、 **TraceInfo** が **true** の場合、 **TraceError** と **TraceWarning** も **true** になりますが、 **TraceVerbose** は **false** になることがあります。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-156">For example, if **TraceInfo** is **true**, then **TraceError** and **TraceWarning** are also **true** but **TraceVerbose** might well be **false**.</span></span>  
  
 <span data-ttu-id="d5f4c-157">これらのプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-157">These properties are read-only.</span></span> <span data-ttu-id="d5f4c-158">**TraceSwitch** オブジェクトは、 **TraceLevel** プロパティの設定時にこれらのプロパティを自動的に設定します。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-158">The **TraceSwitch** object automatically sets them when the **TraceLevel** property is set.</span></span> <span data-ttu-id="d5f4c-159">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-159">For example:</span></span>  
  
```vb  
Dim myTraceSwitch As New TraceSwitch("SwitchOne", "The first switch")  
myTraceSwitch.Level = TraceLevel.Info  
' This message box displays true, because setting the level to  
' TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString())  
' This messagebox displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString())  
```  
  
```csharp  
System.Diagnostics.TraceSwitch myTraceSwitch =
   new System.Diagnostics.TraceSwitch("SwitchOne", "The first switch");  
myTraceSwitch.Level = System.Diagnostics.TraceLevel.Info;  
// This message box displays true, because setting the level to
// TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString());  
// This message box displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString());  
```  
  
## <a name="developer-defined-switches"></a><span data-ttu-id="d5f4c-160">開発者が定義するスイッチ</span><span class="sxs-lookup"><span data-stu-id="d5f4c-160">Developer-Defined Switches</span></span>  

 <span data-ttu-id="d5f4c-161">**BooleanSwitch** と **TraceSwitch** を指定する以外に、 **Switch** クラスから継承される独自のスイッチを定義して、カスタマイズしたメソッドで基本クラスのメソッドをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-161">In addition to providing **BooleanSwitch** and **TraceSwitch**, you can define your own switches by inheriting from the **Switch** class and overriding the base class methods with customized methods.</span></span> <span data-ttu-id="d5f4c-162">開発者定義スイッチの作成方法については、「.NET Framework リファレンス」の「 <xref:System.Diagnostics.Switch> クラス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5f4c-162">For more information about creating developer-defined switches, see the <xref:System.Diagnostics.Switch> class in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5f4c-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5f4c-163">See also</span></span>

- [<span data-ttu-id="d5f4c-164">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="d5f4c-164">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="d5f4c-165">方法 : アプリケーション コードにトレース ステートメントを追加する</span><span class="sxs-lookup"><span data-stu-id="d5f4c-165">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="d5f4c-166">アプリケーションのトレースとインストルメント</span><span class="sxs-lookup"><span data-stu-id="d5f4c-166">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)

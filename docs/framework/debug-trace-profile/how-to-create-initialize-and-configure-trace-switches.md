---
title: '方法: トレース スイッチを作成、初期化、および構成する'
description: .NET 内で System.Diagnostics.BooleanSwitch および System.Diagnostics.TraceSwitch クラスを使用して、トレース スイッチを作成、初期化、構成します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
ms.openlocfilehash: 4e8c076645f19e197ea820c052b20d5dde5e7565
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272255"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="1cce3-103">方法: トレース スイッチを作成、初期化、および構成する</span><span class="sxs-lookup"><span data-stu-id="1cce3-103">How to: Create, Initialize and Configure Trace Switches</span></span>

<span data-ttu-id="1cce3-104">トレース スイッチを使用すると、トレース出力を有効/無効にしたり、トレースの出力をフィルター処理したりできます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-104">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>

## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="1cce3-105">トレース スイッチの作成と初期化</span><span class="sxs-lookup"><span data-stu-id="1cce3-105">Creating and initializing a trace switch</span></span>  

 <span data-ttu-id="1cce3-106">トレース スイッチを使用するには、まずトレース スイッチを作成し、コード内に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1cce3-106">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="1cce3-107">事前定義されている 2 つのクラスからスイッチ オブジェクトを作成することができます。それは、<xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> クラスと <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> クラスです。</span><span class="sxs-lookup"><span data-stu-id="1cce3-107">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="1cce3-108">トレース メッセージを表示させるかどうかのみ処理すればよい場合は <xref:System.Diagnostics.BooleanSwitch> を使用し、トレースのレベルを区別する必要がある場合は <xref:System.Diagnostics.TraceSwitch> を使用します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-108">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="1cce3-109"><xref:System.Diagnostics.TraceSwitch> を使用する場合は、独自のデバッグ メッセージを定義して、それらのメッセージを異なるトレース レベルに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-109">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="1cce3-110">どちらの種類のスイッチも、トレースまたはデバッグの両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-110">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="1cce3-111">既定では、<xref:System.Diagnostics.BooleanSwitch> は無効に設定され、<xref:System.Diagnostics.TraceSwitch> はレベル <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType> に設定されています。</span><span class="sxs-lookup"><span data-stu-id="1cce3-111">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1cce3-112">トレース スイッチは、それらを使用する可能性のあるコードの任意の部分に作成して配置することができます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-112">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="1cce3-113">トレース レベルやその他の構成オプションをコード内に設定することもできますが、構成ファイルを使用してスイッチの状態を管理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1cce3-113">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="1cce3-114">これは、構成システムでスイッチの構成を管理したほうが柔軟性が高く、アプリケーションを再コンパイルしないでもさまざまなスイッチのオン/オフを切り替えたりレベルを変更したりできるからです。</span><span class="sxs-lookup"><span data-stu-id="1cce3-114">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="1cce3-115">トレース スイッチを作成し、初期化するには</span><span class="sxs-lookup"><span data-stu-id="1cce3-115">To create and initialize a trace switch</span></span>  
  
1. <span data-ttu-id="1cce3-116">スイッチを型 <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> または型 <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> のいずれかに定義し、スイッチの名前と説明を設定します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-116">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2. <span data-ttu-id="1cce3-117">トレース スイッチを構成します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-117">Configure your trace switch.</span></span> <span data-ttu-id="1cce3-118">詳細については、「[トレース スイッチの構成](#configure)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1cce3-118">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="1cce3-119">次のコードでは、それぞれの種類のスイッチを 1 つずつ作成します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-119">The following code creates two switches, one of each type:</span></span>  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =
       new System.Diagnostics.TraceSwitch("General",
       "Entire application");  
    ```  
  
<a name="configure"></a>

## <a name="configuring-trace-switches"></a><span data-ttu-id="1cce3-120">トレース スイッチの構成</span><span class="sxs-lookup"><span data-stu-id="1cce3-120">Configuring trace switches</span></span>  

 <span data-ttu-id="1cce3-121">アプリケーションを配布した後も、引き続き、アプリケーション内のトレース スイッチを構成することによりトレース出力を有効/無効にできます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-121">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="1cce3-122">この場合、"スイッチを構成する" とは、初期化された後に外部ソースからその値を変更することを意味します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-122">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="1cce3-123">構成ファイルを使用してスイッチ オブジェクトの値を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-123">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="1cce3-124">トレース スイッチを構成すると、スイッチのオン/オフの切り替えやレベル設定を行えるほか、リスナーに引き渡すメッセージの量と種類を決定できます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-124">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="1cce3-125">スイッチは、.config ファイルを使用して構成されています。</span><span class="sxs-lookup"><span data-stu-id="1cce3-125">Your switches are configured using the .config file.</span></span> <span data-ttu-id="1cce3-126">Web アプリケーションでは、これは、プロジェクトに関連付けられた Web.config ファイルです。</span><span class="sxs-lookup"><span data-stu-id="1cce3-126">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="1cce3-127">Windows アプリケーションでは、このファイルは、(アプリケーション名).exe.config という名前です。配置されたアプリケーションでは、このファイルは実行可能ファイルと同じフォルダーになければなりません。</span><span class="sxs-lookup"><span data-stu-id="1cce3-127">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="1cce3-128">アプリケーションが、スイッチのインスタンスを作成するコードを初めて実行したときに、構成ファイルを確認して名前付きのスイッチに関するトレース レベルの情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-128">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="1cce3-129">トレース システムが特定のスイッチに関して構成ファイルを調べるのは、アプリケーションが初めてスイッチを作成するとき 1 回のみです。</span><span class="sxs-lookup"><span data-stu-id="1cce3-129">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="1cce3-130">配置されたアプリケーションでは、アプリケーションが実行されていないときにスイッチ オブジェクトを再構成することによりトレース コードを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-130">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="1cce3-131">この手順は、通常、スイッチ オブジェクトのオン/オフの切り替えやトレース レベルの変更を行った後、アプリケーションを再起動します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-131">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="1cce3-132">スイッチのインスタンスを作成するときに、*displayName* 引数と *description* 引数の 2 つを指定することで、インスタンスを初期化することもできます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-132">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="1cce3-133">コンストラクターの *displayName* 引数は、<xref:System.Diagnostics.Switch> クラス インスタンスの <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-133">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="1cce3-134">*displayName* は .config ファイルでスイッチを構成するために使用されている名前です。*description* 引数は、スイッチとそれがコントロールするメッセージについて簡単な説明を返します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-134">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="1cce3-135">構成するスイッチの名前を指定するだけでなく、スイッチの値も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1cce3-135">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="1cce3-136">この値は整数です。</span><span class="sxs-lookup"><span data-stu-id="1cce3-136">This value is an Integer.</span></span> <span data-ttu-id="1cce3-137"><xref:System.Diagnostics.BooleanSwitch> では、値 0 が **オフ** に相当し、0 以外の値が **オン** に相当します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-137">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="1cce3-138"><xref:System.Diagnostics.TraceSwitch> では、0、1、2、3、および 4 が、それぞれ **オフ**、**エラー**、**警告**、**情報**、および **詳細** に相当します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-138">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="1cce3-139">4 より大きい数値は **詳細** として扱われ、0 より小さい数値は **オフ** として扱われます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-139">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1cce3-140">.NET Framework バージョン 2.0 では、スイッチの値を指定するためにテキストを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-140">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="1cce3-141">たとえば、<xref:System.Diagnostics.BooleanSwitch> に対して `true` を指定したり、<xref:System.Diagnostics.TraceSwitch> に対して列挙値のテキスト形式である `Error` を指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-141">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="1cce3-142">`<add name="myTraceSwitch" value="Error" />` という行は、`<add name="myTraceSwitch" value="1" />` と同じです。</span><span class="sxs-lookup"><span data-stu-id="1cce3-142">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="1cce3-143">エンドユーザーがアプリケーションのトレース スイッチを構成できるようにするため、アプリケーションのスイッチに関する詳細なドキュメントを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1cce3-143">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="1cce3-144">どのスイッチで何を制御するのか、およびスイッチのオン/オフを切り替える方法について詳しく説明してください。</span><span class="sxs-lookup"><span data-stu-id="1cce3-144">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="1cce3-145">また、.config ファイルのコメントに適切なヘルプを記載して、エンド ユーザーに提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1cce3-145">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="1cce3-146">トレース スイッチを構成する</span><span class="sxs-lookup"><span data-stu-id="1cce3-146">To configure trace switches</span></span>  
  
1. <span data-ttu-id="1cce3-147">トレース スイッチを使用するには、「[Creating and initializing a trace switch](#create)」(トレース スイッチの作成と初期化) のセクションで説明されているように、まず、それらを作成してコードに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1cce3-147">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2. <span data-ttu-id="1cce3-148">プロジェクトに構成ファイル (app.config または Web.config) が含まれない場合は、**[プロジェクト]** メニューから **[新しい項目の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-148">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    - <span data-ttu-id="1cce3-149">**Visual Basic:\*\*\*\*[新しい項目の追加]** ダイアログ ボックスで **[アプリケーション構成ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-149">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="1cce3-150">アプリケーション構成ファイルが作成され、開かれます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-150">The application configuration file is created and opened.</span></span> <span data-ttu-id="1cce3-151">これは、XML ドキュメントであり、ルート要素は `<configuration>.` です。</span><span class="sxs-lookup"><span data-stu-id="1cce3-151">This is an XML document whose root element is `<configuration>.`</span></span>  
  
    - <span data-ttu-id="1cce3-152">**Visual C# :\*\*\*\*[新しい項目の追加]** ダイアログ ボックスで **[XML ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-152">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="1cce3-153">このファイルに **app.config** という名前を付けます。XML エディターで、XML 宣言の後に次の XML を追加します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-153">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="1cce3-154">プロジェクトをコンパイルすると、app.config ファイルがプロジェクトの出力フォルダーにコピーされ、名前が *applicationname*.exe.config に変更されます。</span><span class="sxs-lookup"><span data-stu-id="1cce3-154">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3. <span data-ttu-id="1cce3-155">`<configuration>` タグの後、かつ `</configuration>` タグの前に、スイッチを構成する適切な XML を追加します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-155">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="1cce3-156">次の例では、**DisplayName** プロパティに `DataMessageSwitch` を設定した **BooleanSwitch** と、**DisplayName** プロパティに `TraceLevelSwitch` を設定した **TraceSwitch** を示します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-156">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="1cce3-157">この構成では、両方のスイッチがオフになっています。</span><span class="sxs-lookup"><span data-stu-id="1cce3-157">In this configuration, both switches are off.</span></span>  
  
4. <span data-ttu-id="1cce3-158">**BooleanSwitch** (前の例の `DataMessagesSwitch` など) をオンにする必要がある場合は、**Value** を 0 以外の任意の整数に変更します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-158">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5. <span data-ttu-id="1cce3-159">**TraceSwitch** (前の例の `TraceLevelSwitch` など) をオンにする必要がある場合は、**Value** を適切なレベル設定 (1 から 4) に変更します。</span><span class="sxs-lookup"><span data-stu-id="1cce3-159">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6. <span data-ttu-id="1cce3-160">.config ファイルにコメントを追加して、スイッチを適切に構成するためにどの値を変更すればよいかをエンドユーザーが明確に理解できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1cce3-160">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="1cce3-161">次の例は、コメントを含む、最終的なコードを示しています。</span><span class="sxs-lookup"><span data-stu-id="1cce3-161">The following example shows how the final code, including comments, might look:</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1cce3-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cce3-162">See also</span></span>

- [<span data-ttu-id="1cce3-163">アプリケーションのトレースとインストルメント</span><span class="sxs-lookup"><span data-stu-id="1cce3-163">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="1cce3-164">方法 : アプリケーション コードにトレース ステートメントを追加する</span><span class="sxs-lookup"><span data-stu-id="1cce3-164">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="1cce3-165">トレース スイッチ</span><span class="sxs-lookup"><span data-stu-id="1cce3-165">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="1cce3-166">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="1cce3-166">Trace and Debug Settings Schema</span></span>](../configure-apps/file-schema/trace-debug/index.md)

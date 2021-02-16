---
description: '詳細情報: チュートリアル: Windows API の呼び出し (Visual Basic)'
title: 'チュートリアル: Windows API の呼び出し'
ms.date: 07/20/2015
helpviewer_keywords:
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls [Visual Basic], walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement [Visual Basic], declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
ms.openlocfilehash: 9ffe89cabade780dbe1ced189a92c37e822c59e9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427259"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a><span data-ttu-id="4f54f-103">チュートリアル: Windows API の呼び出し (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f54f-103">Walkthrough: Calling Windows APIs (Visual Basic)</span></span>

<span data-ttu-id="4f54f-104">Windows API は、Windows オペレーティング システムの一部であるダイナミック リンク ライブラリ (DLL) です。</span><span class="sxs-lookup"><span data-stu-id="4f54f-104">Windows APIs are dynamic-link libraries (DLLs) that are part of the Windows operating system.</span></span> <span data-ttu-id="4f54f-105">独自の同等のプロシージャを記述することが困難な場合は、これらを使用してタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-105">You use them to perform tasks when it is difficult to write equivalent procedures of your own.</span></span> <span data-ttu-id="4f54f-106">たとえば、Windows には `FlashWindowEx` という名前の関数が用意されていて、これを使用すると、アプリケーションのタイトル バーを交互に明るい色合いと暗い色合いにすることができます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-106">For example, Windows provides a function named `FlashWindowEx` that lets you make the title bar for an application alternate between light and dark shades.</span></span>  
  
 <span data-ttu-id="4f54f-107">ご自身のコードで Windows API を使用する利点は、既に記述され、使用されるのを待っている便利な関数が多数含まれているため、開発時間を節約できることです。</span><span class="sxs-lookup"><span data-stu-id="4f54f-107">The advantage of using Windows APIs in your code is that they can save development time because they contain dozens of useful functions that are already written and waiting to be used.</span></span> <span data-ttu-id="4f54f-108">欠点として、Windows API は処理が容易でなく、問題が発生したときに困難な状況になることがあります。</span><span class="sxs-lookup"><span data-stu-id="4f54f-108">The disadvantage is that Windows APIs can be difficult to work with and unforgiving when things go wrong.</span></span>  
  
 <span data-ttu-id="4f54f-109">Windows API は、相互運用性の特別なカテゴリを表しています。</span><span class="sxs-lookup"><span data-stu-id="4f54f-109">Windows APIs represent a special category of interoperability.</span></span> <span data-ttu-id="4f54f-110">Windows API にマネージド コードは使用されておらず、組み込みのタイプ ライブラリはありません。また、使用するデータ型は Visual Studio で使用するものとは異なります。</span><span class="sxs-lookup"><span data-stu-id="4f54f-110">Windows APIs do not use managed code, do not have built-in type libraries, and use data types that are different than those used with Visual Studio.</span></span> <span data-ttu-id="4f54f-111">これらの違いにより、また、Windows API は COM オブジェクトではないことから、Windows API および .NET Framework との相互運用性は、プラットフォーム呼び出し (PInvoke) を使用して実現されます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-111">Because of these differences, and because Windows APIs are not COM objects, interoperability with Windows APIs and the .NET Framework is performed using platform invoke, or PInvoke.</span></span> <span data-ttu-id="4f54f-112">プラットフォーム呼び出しは、DLL に実装されたアンマネージド関数をマネージド コードから呼び出すことを可能にするサービスです。</span><span class="sxs-lookup"><span data-stu-id="4f54f-112">Platform invoke is a service that enables managed code to call unmanaged functions implemented in DLLs.</span></span> <span data-ttu-id="4f54f-113">詳細については、「[アンマネージド DLL 関数の処理](../../../framework/interop/consuming-unmanaged-dll-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f54f-113">For more information, see [Consuming Unmanaged DLL Functions](../../../framework/interop/consuming-unmanaged-dll-functions.md).</span></span> <span data-ttu-id="4f54f-114">Visual Basic で PInvoke を使用するには、`Declare` ステートメントを使用するか、`DllImport` 属性を空のプロシージャに適用します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-114">You can use PInvoke in Visual Basic by using either the `Declare` statement or applying the `DllImport` attribute to an empty procedure.</span></span>  
  
 <span data-ttu-id="4f54f-115">Windows API 呼び出しは、過去においては Visual Basic プログラミングの重要な部分でしたが、Visual Basic .NET ではほとんど必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4f54f-115">Windows API calls were an important part of Visual Basic programming in the past, but are seldom necessary with Visual Basic .NET.</span></span> <span data-ttu-id="4f54f-116">可能な限り、Windows API 呼び出しではなく .NET Framework のマネージド コードを使用してタスクを実行するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="4f54f-116">Whenever possible, you should use managed code from the .NET Framework to perform tasks, instead of Windows API calls.</span></span> <span data-ttu-id="4f54f-117">このチュートリアルでは、Windows API を使用することが必要な場合のために、情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-117">This walkthrough provides information for those situations in which using Windows APIs is necessary.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a><span data-ttu-id="4f54f-118">Declare を使用した API 呼び出し</span><span class="sxs-lookup"><span data-stu-id="4f54f-118">API Calls Using Declare</span></span>  

 <span data-ttu-id="4f54f-119">Windows API を呼び出す最も一般的な方法は、`Declare` ステートメントを使用することです。</span><span class="sxs-lookup"><span data-stu-id="4f54f-119">The most common way to call Windows APIs is by using the `Declare` statement.</span></span>  
  
### <a name="to-declare-a-dll-procedure"></a><span data-ttu-id="4f54f-120">DLL プロシージャを宣言するには</span><span class="sxs-lookup"><span data-stu-id="4f54f-120">To declare a DLL procedure</span></span>  
  
1. <span data-ttu-id="4f54f-121">呼び出す関数の名前と引数、引数の型、戻り値、さらに、その関数を含む DLL の名前と場所を特定します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-121">Determine the name of the function you want to call, plus its arguments, argument types, and return value, as well as the name and location of the DLL that contains it.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4f54f-122">Windows API の詳細については、プラットフォーム SDK Windows API の Win32 SDK ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f54f-122">For complete information about the Windows APIs, see the Win32 SDK documentation in the Platform SDK Windows API.</span></span> <span data-ttu-id="4f54f-123">Windows API で使用する定数の詳細については、プラットフォーム SDK に付属している Windows.h などのヘッダー ファイルを調べてください。</span><span class="sxs-lookup"><span data-stu-id="4f54f-123">For more information about the constants that Windows APIs use, examine the header files such as Windows.h included with the Platform SDK.</span></span>  
  
2. <span data-ttu-id="4f54f-124">**[ファイル]** メニューの **[新規作成]** をクリックし、次に **[プロジェクト]** をクリックして、新しい Windows アプリケーション プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-124">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="4f54f-125">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-125">The **New Project** dialog box appears.</span></span>  
  
3. <span data-ttu-id="4f54f-126">Visual Basic プロジェクト テンプレートの一覧から **[Windows アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-126">Select **Windows Application** from the list of Visual Basic project templates.</span></span> <span data-ttu-id="4f54f-127">新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-127">The new project is displayed.</span></span>  
  
4. <span data-ttu-id="4f54f-128">DLL を使用するクラスまたはモジュールに、次の `Declare` 関数を追加します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-128">Add the following `Declare` function either to the class or module in which you want to use the DLL:</span></span>  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a><span data-ttu-id="4f54f-129">Declare ステートメントの各部</span><span class="sxs-lookup"><span data-stu-id="4f54f-129">Parts of the Declare Statement</span></span>  

 <span data-ttu-id="4f54f-130">`Declare` ステートメントには、次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-130">The `Declare` statement includes the following elements.</span></span>  
  
#### <a name="auto-modifier"></a><span data-ttu-id="4f54f-131">Auto 修飾子</span><span class="sxs-lookup"><span data-stu-id="4f54f-131">Auto modifier</span></span>  

 <span data-ttu-id="4f54f-132">`Auto` は、共通言語ランタイムの規則 (または、指定されている場合はエイリアス名) に従って、メソッド名に基づいて文字列を変換するようにランタイムに指示する修飾子です。</span><span class="sxs-lookup"><span data-stu-id="4f54f-132">The `Auto` modifier instructs the runtime to convert the string based on the method name according to common language runtime rules (or alias name if specified).</span></span>  
  
#### <a name="lib-and-alias-keywords"></a><span data-ttu-id="4f54f-133">Lib キーワードと Alias キーワード</span><span class="sxs-lookup"><span data-stu-id="4f54f-133">Lib and Alias keywords</span></span>  

 <span data-ttu-id="4f54f-134">`Function` キーワードの後の名前は、インポートされた関数にアクセスするためにプログラムで使用する名前です。</span><span class="sxs-lookup"><span data-stu-id="4f54f-134">The name following the `Function` keyword is the name your program uses to access the imported function.</span></span> <span data-ttu-id="4f54f-135">これは、呼び出す関数の実際の名前と同じにすることができます。または、任意の有効なプロシージャ名を使用し、`Alias` キーワードを使って呼び出す関数の実際の名前を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-135">It can be the same as the real name of the function you are calling, or you can use any valid procedure name and then employ the `Alias` keyword to specify the real name of the function you are calling.</span></span>  
  
 <span data-ttu-id="4f54f-136">`Lib` キーワードを指定し、その後に、呼び出す関数を含む DLL の名前と場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-136">Specify the `Lib` keyword, followed by the name and location of the DLL that contains the function you are calling.</span></span> <span data-ttu-id="4f54f-137">Windows システム ディレクトリにあるファイルのパスを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4f54f-137">You do not need to specify the path for files located in the Windows system directories.</span></span>  
  
 <span data-ttu-id="4f54f-138">呼び出す関数の名前が有効な Visual Basic プロシージャ名ではない場合、またはアプリケーション内の他の項目の名前と競合する場合は、`Alias` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-138">Use the `Alias` keyword if the name of the function you are calling is not a valid Visual Basic procedure name, or conflicts with the name of other items in your application.</span></span> <span data-ttu-id="4f54f-139">呼び出す関数の名前を `Alias` で示します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-139">`Alias` indicates the true name of the function being called.</span></span>  
  
#### <a name="argument-and-data-type-declarations"></a><span data-ttu-id="4f54f-140">引数とデータ型の宣言</span><span class="sxs-lookup"><span data-stu-id="4f54f-140">Argument and Data Type Declarations</span></span>  

 <span data-ttu-id="4f54f-141">引数とそのデータ型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-141">Declare the arguments and their data types.</span></span> <span data-ttu-id="4f54f-142">Windows で使用されるデータ型は Visual Studio のデータ型に対応していないため、この部分は難しくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f54f-142">This part can be challenging because the data types that Windows uses do not correspond to Visual Studio data types.</span></span> <span data-ttu-id="4f54f-143">Visual Basic では、引数を互換性のあるデータ型に変換すること ("*マーシャリング*" と呼ばれるプロセス) によって、さまざまな処理が自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-143">Visual Basic does a lot of the work for you by converting arguments to compatible data types, a process called *marshaling*.</span></span> <span data-ttu-id="4f54f-144"><xref:System.Runtime.InteropServices> 名前空間に定義されている <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を使用して、引数のマーシャリング方法を明示的に制御できます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-144">You can explicitly control how arguments are marshaled by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f54f-145">以前のバージョンの Visual Basic では、パラメーターを `As Any` と宣言することができました。これは、任意のデータ型のデータを使用できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-145">Previous versions of Visual Basic allowed you to declare parameters `As Any`, meaning that data of any data type could be used.</span></span> <span data-ttu-id="4f54f-146">Visual Basic では、すべての `Declare` ステートメントで特定のデータ型を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f54f-146">Visual Basic requires that you use a specific data type for all `Declare` statements.</span></span>  
  
#### <a name="windows-api-constants"></a><span data-ttu-id="4f54f-147">Windows API の定数</span><span class="sxs-lookup"><span data-stu-id="4f54f-147">Windows API Constants</span></span>  

 <span data-ttu-id="4f54f-148">定数を組み合わせた引数もあります。</span><span class="sxs-lookup"><span data-stu-id="4f54f-148">Some arguments are combinations of constants.</span></span> <span data-ttu-id="4f54f-149">たとえば、このチュートリアルに示されている `MessageBox` API では、メッセージ ボックスの表示方法を制御する `Typ` という整数の引数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-149">For example, the `MessageBox` API shown in this walkthrough accepts an integer argument called `Typ` that controls how the message box is displayed.</span></span> <span data-ttu-id="4f54f-150">これらの定数の数値を確認するには、WinUser.h ファイルの `#define` ステートメントを調べます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-150">You can determine the numeric value of these constants by examining the `#define` statements in the file WinUser.h.</span></span> <span data-ttu-id="4f54f-151">通常、数値は 16 進数で表示されるので、加算や 10 進数への変換には電卓を使用した方がよいかもしれません。</span><span class="sxs-lookup"><span data-stu-id="4f54f-151">The numeric values are generally shown in hexadecimal, so you may want to use a calculator to add them and convert to decimal.</span></span> <span data-ttu-id="4f54f-152">たとえば、感嘆符のスタイルを示す定数 `MB_ICONEXCLAMATION` 0x00000030 と、[はい] と [いいえ] のスタイルを示す定数 `MB_YESNO` 0x00000004 を組み合わせる場合は、これらの数値を加算して 0x00000034 または 10 進数の 52 という結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-152">For example, if you want to combine the constants for the exclamation style `MB_ICONEXCLAMATION` 0x00000030 and the Yes/No style `MB_YESNO` 0x00000004, you can add the numbers and get a result of 0x00000034, or 52 decimal.</span></span> <span data-ttu-id="4f54f-153">10 進数の結果を直接使用することもできますが、これらの値をアプリケーションで定数として宣言し、`Or` 演算子を使用して組み合わせることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4f54f-153">Although you can use the decimal result directly, it is better to declare these values as constants in your application and combine them using the `Or` operator.</span></span>  
  
##### <a name="to-declare-constants-for-windows-api-calls"></a><span data-ttu-id="4f54f-154">Windows API 呼び出しの定数を宣言するには</span><span class="sxs-lookup"><span data-stu-id="4f54f-154">To declare constants for Windows API calls</span></span>  
  
1. <span data-ttu-id="4f54f-155">呼び出す Windows 関数のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f54f-155">Consult the documentation for the Windows function you are calling.</span></span> <span data-ttu-id="4f54f-156">使用する定数の名前と、定数の数値が含まれている .h ファイルの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-156">Determine the name of the constants it uses and the name of the .h file that contains the numeric values for these constants.</span></span>  
  
2. <span data-ttu-id="4f54f-157">メモ帳などのテキスト エディターを使用してヘッダー (.h) ファイルの内容を表示し、使用する定数に関連付けられている値を見つけます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-157">Use a text editor, such as Notepad, to view the contents of the header (.h) file, and find the values associated with the constants you are using.</span></span> <span data-ttu-id="4f54f-158">たとえば、`MessageBox` API では、定数 `MB_ICONQUESTION` を使用して、メッセージ ボックスに疑問符を表示します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-158">For example, the `MessageBox` API uses the constant `MB_ICONQUESTION` to show a question mark in the message box.</span></span> <span data-ttu-id="4f54f-159">`MB_ICONQUESTION` の定義は WinUser.h にあり、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-159">The definition for `MB_ICONQUESTION` is in WinUser.h and appears as follows:</span></span>  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. <span data-ttu-id="4f54f-160">クラスまたはモジュールに同等の `Const` ステートメントを追加して、これらの定数をアプリケーションで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4f54f-160">Add equivalent `Const` statements to your class or module to make these constants available to your application.</span></span> <span data-ttu-id="4f54f-161">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-161">For example:</span></span>  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a><span data-ttu-id="4f54f-162">DLL プロシージャを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="4f54f-162">To call the DLL procedure</span></span>  
  
1. <span data-ttu-id="4f54f-163">`Button1` という名前のボタンをプロジェクトのスタートアップ フォームに追加し、それをダブルクリックしてコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-163">Add a button named `Button1` to the startup form for your project, and then double-click it to view its code.</span></span> <span data-ttu-id="4f54f-164">そのボタンに対応するイベント ハンドラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-164">The event handler for the button is displayed.</span></span>  
  
2. <span data-ttu-id="4f54f-165">追加したボタンの `Click` イベント ハンドラーにコードを追加して、プロシージャを呼び出し、適切な引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-165">Add code to the `Click` event handler for the button you added, to call the procedure and provide the appropriate arguments:</span></span>  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. <span data-ttu-id="4f54f-166">F5 キーを押して、プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-166">Run the project by pressing F5.</span></span> <span data-ttu-id="4f54f-167">メッセージ ボックスに **Yes** と **No** の両方の応答ボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-167">The message box is displayed with both **Yes** and **No** response buttons.</span></span> <span data-ttu-id="4f54f-168">どちらかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f54f-168">Click either one.</span></span>  
  
#### <a name="data-marshaling"></a><span data-ttu-id="4f54f-169">データ マーシャリング</span><span class="sxs-lookup"><span data-stu-id="4f54f-169">Data Marshaling</span></span>  

 <span data-ttu-id="4f54f-170">Visual Basic では、パラメーターと戻り値のデータ型が Windows API 呼び出し用に自動的に変換されますが、`MarshalAs` 属性を使用すると、API で想定されるアンマネージド データ型を明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-170">Visual Basic automatically converts the data types of parameters and return values for Windows API calls, but you can use the `MarshalAs` attribute to explicitly specify unmanaged data types that an API expects.</span></span> <span data-ttu-id="4f54f-171">相互運用マーシャリングの詳細については、「[相互運用マーシャリング](../../../framework/interop/interop-marshaling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f54f-171">For more information about interop marshaling, see [Interop Marshaling](../../../framework/interop/interop-marshaling.md).</span></span>  
  
##### <a name="to-use-declare-and-marshalas-in-an-api-call"></a><span data-ttu-id="4f54f-172">API 呼び出しで Declare と MarshalAs を使用するには</span><span class="sxs-lookup"><span data-stu-id="4f54f-172">To use Declare and MarshalAs in an API call</span></span>  
  
1. <span data-ttu-id="4f54f-173">呼び出す関数の名前と引数、データ型、戻り値を特定します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-173">Determine the name of the function you want to call, plus its arguments, data types, and return value.</span></span>  
  
2. <span data-ttu-id="4f54f-174">`MarshalAs` 属性へのアクセスを簡単にするために、次の例に示すように、クラスまたはモジュールのコードの先頭に `Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-174">To simplify access to the `MarshalAs` attribute, add an `Imports` statement to the top of the code for the class or module, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. <span data-ttu-id="4f54f-175">使用するクラスまたはモジュールに、インポートされる関数の関数プロトタイプを追加し、`MarshalAs` 属性をパラメーターまたは戻り値に適用します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-175">Add a function prototype for the imported function to the class or module you are using, and apply the `MarshalAs` attribute to the parameters or return value.</span></span> <span data-ttu-id="4f54f-176">次の例では、型 `void*` が想定される API 呼び出しを `AsAny` としてマーシャリングしています。</span><span class="sxs-lookup"><span data-stu-id="4f54f-176">In the following example, an API call that expects the type `void*` is marshaled as `AsAny`:</span></span>  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a><span data-ttu-id="4f54f-177">DllImport を使用した API 呼び出し</span><span class="sxs-lookup"><span data-stu-id="4f54f-177">API Calls Using DllImport</span></span>  

 <span data-ttu-id="4f54f-178">`DllImport` 属性により、タイプ ライブラリを使用せずに DLL 内の関数を呼び出す第 2 の方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-178">The `DllImport` attribute provides a second way to call functions in DLLs without type libraries.</span></span> <span data-ttu-id="4f54f-179">`DllImport` は `Declare` ステートメントを使用するのとほぼ同等ですが、関数の呼び出し方法をより詳細に制御できます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-179">`DllImport` is roughly equivalent to using a `Declare` statement but provides more control over how functions are called.</span></span>  
  
 <span data-ttu-id="4f54f-180">`DllImport` は、ほとんどの Windows API 呼び出しで使用できます。ただし、その呼び出しで共有 ("*静的*" とも呼ばれる) メソッドを参照している場合に限ります。</span><span class="sxs-lookup"><span data-stu-id="4f54f-180">You can use `DllImport` with most Windows API calls as long as the call refers to a shared (sometimes called *static*) method.</span></span> <span data-ttu-id="4f54f-181">クラスのインスタンスを必要とするメソッドは使用できません。</span><span class="sxs-lookup"><span data-stu-id="4f54f-181">You cannot use methods that require an instance of a class.</span></span> <span data-ttu-id="4f54f-182">`Declare` ステートメントとは異なり、`DllImport` 呼び出しでは `MarshalAs` 属性を使用できません。</span><span class="sxs-lookup"><span data-stu-id="4f54f-182">Unlike `Declare` statements, `DllImport` calls cannot use the `MarshalAs` attribute.</span></span>  
  
### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a><span data-ttu-id="4f54f-183">DllImport 属性を使用して Windows API を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="4f54f-183">To call a Windows API using the DllImport attribute</span></span>  
  
1. <span data-ttu-id="4f54f-184">**[ファイル]** メニューの **[新規作成]** をクリックし、次に **[プロジェクト]** をクリックして、新しい Windows アプリケーション プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-184">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="4f54f-185">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-185">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="4f54f-186">Visual Basic プロジェクト テンプレートの一覧から **[Windows アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-186">Select **Windows Application** from the list of Visual Basic project templates.</span></span> <span data-ttu-id="4f54f-187">新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-187">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="4f54f-188">`Button2` という名前のボタンをスタートアップ フォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-188">Add a button named `Button2` to the startup form.</span></span>  
  
4. <span data-ttu-id="4f54f-189">`Button2` をダブルクリックして、フォームのコード ビューを開きます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-189">Double-click `Button2` to open the code view for the form.</span></span>  
  
5. <span data-ttu-id="4f54f-190">`DllImport` へのアクセスを簡単にするために、スタートアップ フォーム クラスのコードの先頭に `Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-190">To simplify access to `DllImport`, add an `Imports` statement to the top of the code for the startup form class:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. <span data-ttu-id="4f54f-191">フォームの `End Class` ステートメントの前に空の関数を宣言し、その関数に `MoveFile` という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-191">Declare an empty function preceding the `End Class` statement for the form, and name the function `MoveFile`.</span></span>  
  
7. <span data-ttu-id="4f54f-192">関数宣言に `Public` および `Shared` 修飾子を適用し、Windows API 関数で使用される引数に基づいて `MoveFile` のパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-192">Apply the `Public` and `Shared` modifiers to the function declaration and set parameters for `MoveFile` based on the arguments the Windows API function uses:</span></span>  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     <span data-ttu-id="4f54f-193">ご自身の関数には任意の有効なプロシージャ名を使用できます。`DllImport` 属性で、DLL 内の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-193">Your function can have any valid procedure name; the `DllImport` attribute specifies the name in the DLL.</span></span> <span data-ttu-id="4f54f-194">また、それによってパラメーターと戻り値の相互運用マーシャリングも処理されるため、API で使用されているデータ型に似た Visual Studio データ型を選択できます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-194">It also handles interoperability marshaling for the parameters and return values, so you can choose Visual Studio data types that are similar to the data types the API uses.</span></span>  
  
8. <span data-ttu-id="4f54f-195">空のクラスに `DllImport` 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-195">Apply the `DllImport` attribute to the empty function.</span></span> <span data-ttu-id="4f54f-196">最初のパラメーターは、呼び出す関数を含む DLL の名前と場所です。</span><span class="sxs-lookup"><span data-stu-id="4f54f-196">The first parameter is the name and location of the DLL containing the function you are calling.</span></span> <span data-ttu-id="4f54f-197">Windows システム ディレクトリにあるファイルのパスを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4f54f-197">You do not need to specify the path for files located in the Windows system directories.</span></span> <span data-ttu-id="4f54f-198">2 番目のパラメーターは、Windows API 内の関数の名前を指定する名前付き引数です。</span><span class="sxs-lookup"><span data-stu-id="4f54f-198">The second parameter is a named argument that specifies the name of the function in the Windows API.</span></span> <span data-ttu-id="4f54f-199">この例では、`DllImport` 属性によって、`MoveFile` への呼び出しを KERNEL32.DLL 内の `MoveFileW` に強制的に転送しています。</span><span class="sxs-lookup"><span data-stu-id="4f54f-199">In this example, the `DllImport` attribute forces calls to `MoveFile` to be forwarded to `MoveFileW` in KERNEL32.DLL.</span></span> <span data-ttu-id="4f54f-200">`MoveFileW` メソッドにより、`src` パスから `dst` パスにファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="4f54f-200">The `MoveFileW` method copies a file from the path `src` to the path `dst`.</span></span>  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. <span data-ttu-id="4f54f-201">関数を呼び出すコードを `Button2_Click` イベント ハンドラーに追加します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-201">Add code to the `Button2_Click` event handler to call the function:</span></span>  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. <span data-ttu-id="4f54f-202">Test.txt という名前のファイルを作成し、ハード ドライブの C:\Tmp ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-202">Create a file named Test.txt and place it in the C:\Tmp directory on your hard drive.</span></span> <span data-ttu-id="4f54f-203">Tmp ディレクトリは、必要に応じて作成してください。</span><span class="sxs-lookup"><span data-stu-id="4f54f-203">Create the Tmp directory if necessary.</span></span>  
  
11. <span data-ttu-id="4f54f-204">F5 キーを押してアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="4f54f-204">Press F5 to start the application.</span></span> <span data-ttu-id="4f54f-205">メイン フォームが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-205">The main form appears.</span></span>  
  
12. <span data-ttu-id="4f54f-206">**[Button2]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f54f-206">Click **Button2**.</span></span> <span data-ttu-id="4f54f-207">ファイルを移動できた場合、"ファイルが正常に移動しました" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f54f-207">The message "The file was moved successfully" is displayed if the file can be moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f54f-208">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f54f-208">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="4f54f-209">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="4f54f-209">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)
- [<span data-ttu-id="4f54f-210">Auto</span><span class="sxs-lookup"><span data-stu-id="4f54f-210">Auto</span></span>](../../language-reference/modifiers/auto.md)
- [<span data-ttu-id="4f54f-211">Alias</span><span class="sxs-lookup"><span data-stu-id="4f54f-211">Alias</span></span>](../../language-reference/statements/alias-clause.md)
- [<span data-ttu-id="4f54f-212">COM 相互運用</span><span class="sxs-lookup"><span data-stu-id="4f54f-212">COM Interop</span></span>](index.md)
- [<span data-ttu-id="4f54f-213">マネージド コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="4f54f-213">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="4f54f-214">コールバック メソッドとしてのデリゲートのマーシャ リング</span><span class="sxs-lookup"><span data-stu-id="4f54f-214">Marshaling a Delegate as a Callback Method</span></span>](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)

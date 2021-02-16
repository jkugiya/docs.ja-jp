---
description: '詳細情報: Visual Basic のコーディング規則'
title: コーディング規則
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: 424871ab0e77629ded977bd0be768ed8736d1761
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460034"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="c8bf0-103">Visual Basic のコーディング規則</span><span class="sxs-lookup"><span data-stu-id="c8bf0-103">Visual Basic Coding Conventions</span></span>

<span data-ttu-id="c8bf0-104">Microsoft は、ここで示すガイドラインに従ってサンプルおよびドキュメントを開発しています。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-104">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="c8bf0-105">同じコーディング規則に従うと、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-105">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
- <span data-ttu-id="c8bf0-106">コードの見た目が統一されるため、コードを読むときに、レイアウトではなく内容に重点を置くことができます。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-106">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
- <span data-ttu-id="c8bf0-107">これまでの経験に基づいて推測できるようになるため、コードをすばやく理解できます。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-107">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="c8bf0-108">コードのコピー、変更、保守がより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-108">You can copy, change, and maintain the code more easily.</span></span>  
  
- <span data-ttu-id="c8bf0-109">コードが Visual Basic の "ベスト プラクティス" に従っていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-109">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="c8bf0-110">命名規則</span><span class="sxs-lookup"><span data-stu-id="c8bf0-110">Naming Conventions</span></span>  
  
- <span data-ttu-id="c8bf0-111">名前付けのガイドラインについては、「[Naming Guidelines (名前付けのガイドライン)](../../../standard/design-guidelines/naming-guidelines.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-111">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
- <span data-ttu-id="c8bf0-112">"My" または "my" を変数名の一部として使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-112">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="c8bf0-113">`My` オブジェクトとの混同を招くからです。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-113">This practice creates confusion with the `My` objects.</span></span>  
  
- <span data-ttu-id="c8bf0-114">自動生成されたコードに含まれるオブジェクトの名前をこのガイドラインに合わせて変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-114">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="c8bf0-115">レイアウト規則</span><span class="sxs-lookup"><span data-stu-id="c8bf0-115">Layout Conventions</span></span>  
  
- <span data-ttu-id="c8bf0-116">タブを空白として挿入し、4 文字インデントによるスマート インデントを使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-116">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
- <span data-ttu-id="c8bf0-117">コード エディターで **[コードの再フォーマット]** を使用してコードの書式を再設定します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-117">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="c8bf0-118">詳細については、[[オプション]、[テキスト エディター]、[基本] (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic) に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-118">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
- <span data-ttu-id="c8bf0-119">1 つの行には 1 つのステートメントのみを記述します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-119">Use only one statement per line.</span></span> <span data-ttu-id="c8bf0-120">Visual Basic の行区切り記号 (:) は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-120">Don't use the Visual Basic line separator character (:).</span></span>  
  
- <span data-ttu-id="c8bf0-121">言語で許可される場所では、明示的な行継続文字 "_" ではなく暗黙的な行継続を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-121">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
- <span data-ttu-id="c8bf0-122">1 つの行には 1 つの宣言のみを記述します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-122">Use only one declaration per line.</span></span>  
  
- <span data-ttu-id="c8bf0-123">**[コードの再フォーマット]** で継続行が自動的に書式設定されない場合は、継続行のインデントを手動で 1 タブ ストップに設定します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-123">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="c8bf0-124">ただし、リストの項目は常に左揃えにします。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-124">However, always left-align items in a list.</span></span>  
  
    ```vb  
    a As Integer,  
    b As Integer  
    ```  
  
- <span data-ttu-id="c8bf0-125">メソッド定義とプロパティ定義の間に少なくとも 1 行の空白行を追加します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-125">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="c8bf0-126">コメント規則</span><span class="sxs-lookup"><span data-stu-id="c8bf0-126">Commenting Conventions</span></span>  
  
- <span data-ttu-id="c8bf0-127">コメントは、コード行の末尾ではなく別の行に記述します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-127">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
- <span data-ttu-id="c8bf0-128">英語でコメントを記述する場合、コメント テキストの始まりには英大文字を使用し、終わりにはピリオドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-128">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
- <span data-ttu-id="c8bf0-129">コメント デリミター (') とコメント テキストの間に空白を 1 つ挿入します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-129">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- <span data-ttu-id="c8bf0-130">アスタリスク (\*) を整形したブロックでコメントを囲まないようにします。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-130">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="c8bf0-131">プログラムの構造</span><span class="sxs-lookup"><span data-stu-id="c8bf0-131">Program Structure</span></span>  
  
- <span data-ttu-id="c8bf0-132">`Main` メソッドを使用するときには、新しいコンソール アプリケーションの既定の構造を使用し、コマンド ライン引数には `My` を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-132">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="c8bf0-133">言語ガイドライン</span><span class="sxs-lookup"><span data-stu-id="c8bf0-133">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="c8bf0-134">文字列型 (String)</span><span class="sxs-lookup"><span data-stu-id="c8bf0-134">String Data Type</span></span>  
  
- <span data-ttu-id="c8bf0-135">次のコードに示すように、短い文字列を連結するときは[文字列補間](../language-features/strings/interpolated-strings.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-135">Use [string interpolation](../language-features/strings/interpolated-strings.md) to concatenate short strings, as shown in the following code.</span></span>
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- <span data-ttu-id="c8bf0-136">ループ内での文字列の追加には <xref:System.Text.StringBuilder> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-136">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="c8bf0-137">イベント ハンドラー内の厳密でないデリゲート</span><span class="sxs-lookup"><span data-stu-id="c8bf0-137">Relaxed Delegates in Event Handlers</span></span>  

 <span data-ttu-id="c8bf0-138">イベント ハンドラーの引数 (Object および EventArgs) は明示的に修飾しません。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-138">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="c8bf0-139">イベントに渡されるイベント引数 (sender as Object、e as EventArgs など) を使用しない場合は、厳密でないデリゲートを使用して、コードでイベント引数を省略します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-139">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="c8bf0-140">Unsigned データ型</span><span class="sxs-lookup"><span data-stu-id="c8bf0-140">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="c8bf0-141">特に必要でない限り、unsigned 型ではなく `Integer` を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-141">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="c8bf0-142">配列</span><span class="sxs-lookup"><span data-stu-id="c8bf0-142">Arrays</span></span>  
  
- <span data-ttu-id="c8bf0-143">宣言行で配列を初期化するときは短い構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-143">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="c8bf0-144">たとえば、次のような構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-144">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     <span data-ttu-id="c8bf0-145">次のような構文は使用しません。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-145">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- <span data-ttu-id="c8bf0-146">配列指定子は、変数ではなく型に指定します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-146">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="c8bf0-147">たとえば、次のような構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-147">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     <span data-ttu-id="c8bf0-148">次のような構文は使用しません。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-148">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- <span data-ttu-id="c8bf0-149">基本データ型の配列の宣言と初期化では、{ } 構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-149">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="c8bf0-150">たとえば、次のような構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-150">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     <span data-ttu-id="c8bf0-151">次のような構文は使用しません。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-151">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="c8bf0-152">With キーワードの使用</span><span class="sxs-lookup"><span data-stu-id="c8bf0-152">Use the With Keyword</span></span>  

 <span data-ttu-id="c8bf0-153">同じオブジェクトの呼び出しを複数回使用する場合には、`With` キーワードの使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-153">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="c8bf0-154">例外処理を使用する場合の Try...Catch/Using ステートメントの使用</span><span class="sxs-lookup"><span data-stu-id="c8bf0-154">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  

 <span data-ttu-id="c8bf0-155">`On Error Goto`は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-155">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="c8bf0-156">IsNot キーワードの使用</span><span class="sxs-lookup"><span data-stu-id="c8bf0-156">Use the IsNot Keyword</span></span>  

 <span data-ttu-id="c8bf0-157">`IsNot` の代わりに `Not...Is Nothing` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-157">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="c8bf0-158">New キーワード</span><span class="sxs-lookup"><span data-stu-id="c8bf0-158">New Keyword</span></span>  
  
- <span data-ttu-id="c8bf0-159">短い形式のインスタンス化を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-159">Use short instantiation.</span></span> <span data-ttu-id="c8bf0-160">たとえば、次のような構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-160">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     <span data-ttu-id="c8bf0-161">この行は次の行と同じ結果をもたらします。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-161">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- <span data-ttu-id="c8bf0-162">新しいオブジェクトには、パラメーターなしのコンストラクターの代わりにオブジェクト初期化子を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-162">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a><span data-ttu-id="c8bf0-163">イベント処理</span><span class="sxs-lookup"><span data-stu-id="c8bf0-163">Event Handling</span></span>  
  
- <span data-ttu-id="c8bf0-164">`Handles` ではなく `AddHandler` を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-164">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- <span data-ttu-id="c8bf0-165">`AddressOf` を使用し、デリゲートの明示的なインスタンス化は避けます。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-165">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- <span data-ttu-id="c8bf0-166">イベントを定義するときには、短い構文を使用し、デリゲートの定義はコンパイラに任せます。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-166">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- <span data-ttu-id="c8bf0-167">`Nothing` メソッドを呼び出す前にイベントが `RaiseEvent` (null) かどうか確認しないようにします。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-167">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="c8bf0-168">`RaiseEvent` は、イベントを発生させる前に `Nothing` かどうか確認します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-168">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="c8bf0-169">共有メンバーの使用</span><span class="sxs-lookup"><span data-stu-id="c8bf0-169">Using Shared Members</span></span>  

 <span data-ttu-id="c8bf0-170">`Shared` メンバーの呼び出しにはクラス名を使用し、インスタンス変数からは行わないようにします。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-170">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="c8bf0-171">XML リテラルの使用</span><span class="sxs-lookup"><span data-stu-id="c8bf0-171">Use XML Literals</span></span>  

 <span data-ttu-id="c8bf0-172">XML リテラルを使用すると、XML 操作時に行う最も一般的なタスク (読み込み、クエリ、変換など) を簡素化できます。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-172">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="c8bf0-173">XML を使用して開発を行う場合は、次のガイドラインに従います。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-173">When you develop with XML, follow these guidelines:</span></span>  
  
- <span data-ttu-id="c8bf0-174">XML API を直接呼び出す代わりに XML リテラルを使用して XML ドキュメントおよびフラグメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-174">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
- <span data-ttu-id="c8bf0-175">ファイル レベルまたはプロジェクト レベルで XML 名前空間をインポートし、XML リテラルによるパフォーマンスの最適化を利用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-175">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
- <span data-ttu-id="c8bf0-176">XML 軸プロパティを使用して XML ドキュメント内の要素と属性にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-176">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
- <span data-ttu-id="c8bf0-177">`Add` メソッドなどの API 呼び出しを使用する代わりに、埋め込み式を使用して既存の値から値を組み込んで XML を作成します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-177">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a><span data-ttu-id="c8bf0-178">LINQ クエリ</span><span class="sxs-lookup"><span data-stu-id="c8bf0-178">LINQ Queries</span></span>  
  
- <span data-ttu-id="c8bf0-179">クエリ変数にはわかりやすい名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-179">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- <span data-ttu-id="c8bf0-180">クエリ内で要素の名前を指定して、匿名型のプロパティ名の大文字と小文字の使用が正しい Pascal 形式になるようにします。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-180">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- <span data-ttu-id="c8bf0-181">結果のプロパティ名があいまいになる場合は、プロパティ名を変更します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-181">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="c8bf0-182">たとえば、クエリが顧客名と注文 ID を返す場合、それらの名前を結果の `Name` と `ID` のままにはせずに変更します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-182">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- <span data-ttu-id="c8bf0-183">クエリ変数と範囲変数の宣言で型の推論を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-183">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- <span data-ttu-id="c8bf0-184">各クエリ句を `From` ステートメントの下に揃えます。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-184">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- <span data-ttu-id="c8bf0-185">`Where` 句を他のクエリ句より先に使用し、それ以降のクエリ句では、フィルター化されたデータセットが処理されるようにします。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-185">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- <span data-ttu-id="c8bf0-186">`Join` 句を使用して暗黙的に結合操作を定義する代わりに、`Where` 句を使用して明示的に結合操作を定義します。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-186">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="c8bf0-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8bf0-187">See also</span></span>

- [<span data-ttu-id="c8bf0-188">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c8bf0-188">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)

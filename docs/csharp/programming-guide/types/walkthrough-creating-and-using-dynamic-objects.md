---
title: 'チュートリアル: 動的オブジェクトの作成と使用 (C# および Visual Basic)'
description: このチュートリアルでは、動的オブジェクトを作成および使用する方法について説明します。 カスタム動的オブジェクトと、'IronPython' ライブラリを使用するプロジェクトを作成します。
ms.date: 03/24/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.openlocfilehash: 3b342f23a2974affdcd7a1e91093aaef504afb63
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111024"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a><span data-ttu-id="832de-104">チュートリアル: 動的オブジェクトの作成と使用 (C# および Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="832de-104">Walkthrough: Creating and Using Dynamic Objects (C# and Visual Basic)</span></span>

<span data-ttu-id="832de-105">動的オブジェクトは、プロパティやメソッドなどのメンバーを、コンパイル時ではなく実行時に公開します。</span><span class="sxs-lookup"><span data-stu-id="832de-105">Dynamic objects expose members such as properties and methods at run time, instead of at compile time.</span></span> <span data-ttu-id="832de-106">これにより、静的な型や書式に一致しない構造体と連携するオブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="832de-106">This enables you to create objects to work with structures that do not match a static type or format.</span></span> <span data-ttu-id="832de-107">たとえば、動的オブジェクトを使用して HTML ドキュメント オブジェクト モデル (DOM) を参照することもできます。HTML DOM には、有効な HTML マークアップ要素と属性の任意の組み合わせを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="832de-107">For example, you can use a dynamic object to reference the HTML Document Object Model (DOM), which can contain any combination of valid HTML markup elements and attributes.</span></span> <span data-ttu-id="832de-108">各 HTML ドキュメントは一意であるため、特定の HTML ドキュメントのメンバーは実行時に決定されます。</span><span class="sxs-lookup"><span data-stu-id="832de-108">Because each HTML document is unique, the members for a particular HTML document are determined at run time.</span></span> <span data-ttu-id="832de-109">HTML 要素の属性を参照するための一般的な方法は、属性の名前を要素の `GetProperty` メソッドに渡す方法です。</span><span class="sxs-lookup"><span data-stu-id="832de-109">A common method to reference an attribute of an HTML element is to pass the name of the attribute to the `GetProperty` method of the element.</span></span> <span data-ttu-id="832de-110">HTML 要素 `<div id="Div1">` の `id` 属性を参照するには、まず `<div>` 要素への参照を取得し、その後 `divElement.GetProperty("id")` を使用します。</span><span class="sxs-lookup"><span data-stu-id="832de-110">To reference the `id` attribute of the HTML element `<div id="Div1">`, you first obtain a reference to the `<div>` element, and then use `divElement.GetProperty("id")`.</span></span> <span data-ttu-id="832de-111">動的オブジェクトを使用する場合は、`id` 属性を `divElement.id` として参照できます。</span><span class="sxs-lookup"><span data-stu-id="832de-111">If you use a dynamic object, you can reference the `id` attribute as `divElement.id`.</span></span>

 <span data-ttu-id="832de-112">動的オブジェクトを使用すると、IronPython や IronRuby などの動的言語にも簡単にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="832de-112">Dynamic objects also provide convenient access to dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="832de-113">動的オブジェクトを使用して、実行時に解釈される動的スクリプトを参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="832de-113">You can use a dynamic object to refer to a dynamic script that is interpreted at run time.</span></span>

 <span data-ttu-id="832de-114">動的オブジェクトを参照するには、遅延バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="832de-114">You reference a dynamic object by using late binding.</span></span> <span data-ttu-id="832de-115">C# では、遅延バインディング オブジェクトの型は `dynamic` として指定します。</span><span class="sxs-lookup"><span data-stu-id="832de-115">In C#, you specify the type of a late-bound object as `dynamic`.</span></span> <span data-ttu-id="832de-116">Visual Basic では、遅延バインディング オブジェクトの型は `Object` として指定します。</span><span class="sxs-lookup"><span data-stu-id="832de-116">In Visual Basic, you specify the type of a late-bound object as `Object`.</span></span> <span data-ttu-id="832de-117">詳しくは、「[dynamic](../../language-reference/builtin-types/reference-types.md)」および「[事前バインディングと遅延バインディング](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="832de-117">For more information, see [dynamic](../../language-reference/builtin-types/reference-types.md) and [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).</span></span>

 <span data-ttu-id="832de-118">カスタムの動的オブジェクトは、<xref:System.Dynamic?displayProperty=nameWithType> 名前空間内のクラスを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="832de-118">You can create custom dynamic objects by using the classes in the <xref:System.Dynamic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="832de-119">たとえば、<xref:System.Dynamic.ExpandoObject> を作成し、実行時にそのオブジェクトのメンバーを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="832de-119">For example, you can create an <xref:System.Dynamic.ExpandoObject> and specify the members of that object at run time.</span></span> <span data-ttu-id="832de-120">また、<xref:System.Dynamic.DynamicObject> クラスを継承する、独自の型を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="832de-120">You can also create your own type that inherits the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="832de-121">その後、<xref:System.Dynamic.DynamicObject> クラスのメンバーをオーバーライドして、実行時の動的機能を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="832de-121">You can then override the members of the <xref:System.Dynamic.DynamicObject> class to provide run-time dynamic functionality.</span></span>

 <span data-ttu-id="832de-122">この記事には、次の 2 つの独立したチュートリアルがあります。</span><span class="sxs-lookup"><span data-stu-id="832de-122">This article contains two independent walkthroughs:</span></span>

- <span data-ttu-id="832de-123">テキスト ファイルの内容をオブジェクトのプロパティとして動的に公開する、カスタム オブジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="832de-123">Create a custom object that dynamically exposes the contents of a text file as properties of an object.</span></span>

- <span data-ttu-id="832de-124">`IronPython` ライブラリを使用するプロジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="832de-124">Create a project that uses an `IronPython` library.</span></span>

<span data-ttu-id="832de-125">これらのいずれかまたは両方を実行することができます。両方を実行する場合、順序は関係ありません。</span><span class="sxs-lookup"><span data-stu-id="832de-125">You can do either one of these or both of them, and if you do both, the order doesn't matter.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="832de-126">前提条件</span><span class="sxs-lookup"><span data-stu-id="832de-126">Prerequisites</span></span>

* <span data-ttu-id="832de-127">**.NET デスクトップ開発** ワークロードがインストールされている [Visual Studio 2019 バージョン 16.9 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="832de-127">[Visual Studio 2019 version 16.9 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span> <span data-ttu-id="832de-128">このワークロードを選択すると、.NET 5.0 SDK が自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="832de-128">The .NET 5.0 SDK is automatically installed when you select this workload.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

* <span data-ttu-id="832de-129">2 番目のチュートリアルでは、[IronPython](https://ironpython.net/) for .NET をインストールします。</span><span class="sxs-lookup"><span data-stu-id="832de-129">For the second walkthrough, install [IronPython](https://ironpython.net/) for .NET.</span></span> <span data-ttu-id="832de-130">最新バージョンを取得するには、[ダウンロード ページ](https://ironpython.net/download/)に移動します。</span><span class="sxs-lookup"><span data-stu-id="832de-130">Go to their [Download page](https://ironpython.net/download/) to obtain the latest version.</span></span>

## <a name="create-a-custom-dynamic-object"></a><span data-ttu-id="832de-131">カスタム動的オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="832de-131">Create a Custom Dynamic Object</span></span>

<span data-ttu-id="832de-132">最初のチュートリアルでは、テキスト ファイルの内容を検索するカスタム動的オブジェクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="832de-132">The first walkthrough defines a custom dynamic object that searches the contents of a text file.</span></span> <span data-ttu-id="832de-133">動的プロパティにより、検索するテキストが指定されます。</span><span class="sxs-lookup"><span data-stu-id="832de-133">A dynamic property specifies the text to search for.</span></span> <span data-ttu-id="832de-134">たとえば、呼び出しコードで `dynamicFile.Sample` が指定された場合、動的クラスは "Sample" で始まるすべての行をファイルから取得し、それらを含んだ文字列のジェネリック リストを返します。</span><span class="sxs-lookup"><span data-stu-id="832de-134">For example, if calling code specifies `dynamicFile.Sample`, the dynamic class returns a generic list of strings that contains all of the lines from the file that begin with "Sample".</span></span> <span data-ttu-id="832de-135">検索では、大文字と小文字を区別しません。</span><span class="sxs-lookup"><span data-stu-id="832de-135">The search is case-insensitive.</span></span> <span data-ttu-id="832de-136">動的クラスでは、2 つの省略可能な引数もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="832de-136">The dynamic class also supports two optional arguments.</span></span> <span data-ttu-id="832de-137">最初の引数は、検索オプションの列挙値です。この引数では、動的クラスが行の先頭、行の末尾、または行内の任意の場所から一致を検索することを指定します。</span><span class="sxs-lookup"><span data-stu-id="832de-137">The first argument is a search option enum value that specifies that the dynamic class should search for matches at the start of the line, the end of the line, or anywhere in the line.</span></span> <span data-ttu-id="832de-138">2 番目の引数は、動的クラスが検索の前に各行から先頭と末尾の空白をトリミングすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="832de-138">The second argument specifies that the dynamic class should trim leading and trailing spaces from each line before searching.</span></span> <span data-ttu-id="832de-139">たとえば、呼び出しコードで `dynamicFile.Sample(StringSearchOption.Contains)` と指定された場合、動的クラスは行内の任意の場所にある "Sample" を検索します。</span><span class="sxs-lookup"><span data-stu-id="832de-139">For example, if calling code specifies `dynamicFile.Sample(StringSearchOption.Contains)`, the dynamic class searches for "Sample" anywhere in a line.</span></span> <span data-ttu-id="832de-140">呼び出しコードで `dynamicFile.Sample(StringSearchOption.StartsWith, false)` と指定された場合、動的クラスは、各行の先頭にある "Sample" を検索し、先頭と末尾のスペースは削除しません。</span><span class="sxs-lookup"><span data-stu-id="832de-140">If calling code specifies `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, the dynamic class searches for "Sample" at the start of each line, and does not remove leading and trailing spaces.</span></span> <span data-ttu-id="832de-141">既定では、動的クラスは各行の先頭で一致を検索し、先頭と末尾のスペースを削除します。</span><span class="sxs-lookup"><span data-stu-id="832de-141">The default behavior of the dynamic class is to search for a match at the start of each line and to remove leading and trailing spaces.</span></span>

### <a name="to-create-a-custom-dynamic-class"></a><span data-ttu-id="832de-142">カスタムの動的クラスを作成するには</span><span class="sxs-lookup"><span data-stu-id="832de-142">To create a custom dynamic class</span></span>

1. <span data-ttu-id="832de-143">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="832de-143">Start Visual Studio.</span></span>

1. <span data-ttu-id="832de-144">**[新しいプロジェクトの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="832de-144">Select **Create a new project**.</span></span>

1. <span data-ttu-id="832de-145">**[新しいプロジェクトの作成]** ダイアログで、[C#] または [Visual Basic] を選択し、 **[コンソール アプリケーション]** を選択して、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="832de-145">In the **Create a new project** dialog, select C# or Visual Basic, select **Console Application**, and then select **Next**.</span></span>

1. <span data-ttu-id="832de-146">**[新しいプロジェクトの構成]** ダイアログで、 **[プロジェクト名]** に「`DynamicSample`」と入力し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="832de-146">In the **Configure your new project** dialog, enter `DynamicSample` for the **Project name**, and then select **Next**.</span></span>

1. <span data-ttu-id="832de-147">**[追加情報]** ダイアログで、 **[ターゲット フレームワーク]** に **[.NET 5.0 (Current)]** を選んでから、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="832de-147">In the **Additional information** dialog, select **.NET 5.0 (Current)** for the **Target Framework**, and then select **Create**.</span></span>

   <span data-ttu-id="832de-148">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="832de-148">The new project is created.</span></span>

1. <span data-ttu-id="832de-149">**ソリューション エクスプローラー** で、DynamicSample プロジェクトを右リックし、 **[追加]**  >  **[クラス]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="832de-149">In **Solution Explorer**, right-click the DynamicSample project and select **Add** > **Class**.</span></span> <span data-ttu-id="832de-150">**[名前]** ボックスに「`ReadOnlyFile`」と入力し、 **[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="832de-150">In the **Name** box, type `ReadOnlyFile`, and then select **Add**.</span></span>

   <span data-ttu-id="832de-151">ReadOnlyFile クラスを含んだ新しいファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="832de-151">A new file is added that contains the ReadOnlyFile class.</span></span>

1. <span data-ttu-id="832de-152">*ReadOnlyFile.cs* または *ReadOnlyFile.vb* のファイルの先頭に、次のコードを追加して <xref:System.IO?displayProperty=nameWithType> および <xref:System.Dynamic?displayProperty=nameWithType> の名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="832de-152">At the top of the *ReadOnlyFile.cs* or *ReadOnlyFile.vb* file, add the following code to import the <xref:System.IO?displayProperty=nameWithType> and <xref:System.Dynamic?displayProperty=nameWithType> namespaces.</span></span>

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]

1. <span data-ttu-id="832de-153">カスタム動的オブジェクトでは、列挙型を使用して検索条件を決定します。</span><span class="sxs-lookup"><span data-stu-id="832de-153">The custom dynamic object uses an enum to determine the search criteria.</span></span> <span data-ttu-id="832de-154">クラス ステートメントの前に、次の列挙定義を追加します。</span><span class="sxs-lookup"><span data-stu-id="832de-154">Before the class statement, add the following enum definition.</span></span>

    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]

1. <span data-ttu-id="832de-155">次のコード例に示すように、クラス ステートメントを更新して `DynamicObject` クラスを継承します。</span><span class="sxs-lookup"><span data-stu-id="832de-155">Update the class statement to inherit the `DynamicObject` class, as shown in the following code example.</span></span>

    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

1. <span data-ttu-id="832de-156">`ReadOnlyFile` クラスに次のコードを追加して、 ファイル パスのプライベート フィールドと、`ReadOnlyFile` クラスのコンス トラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="832de-156">Add the following code to the `ReadOnlyFile` class to define a private field for the file path and a constructor for the `ReadOnlyFile` class.</span></span>

    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]

1. <span data-ttu-id="832de-157">次の `GetPropertyValue` メソッドを `ReadOnlyFile` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="832de-157">Add the following `GetPropertyValue` method to the `ReadOnlyFile` class.</span></span> <span data-ttu-id="832de-158">`GetPropertyValue` メソッドは検索条件を (入力として) 受け取り、テキスト ファイルから検索条件に一致する行を返します。</span><span class="sxs-lookup"><span data-stu-id="832de-158">The `GetPropertyValue` method takes, as input, search criteria and returns the lines from a text file that match that search criteria.</span></span> <span data-ttu-id="832de-159">`ReadOnlyFile` クラスによって提供される動的メソッドは、`GetPropertyValue` メソッドを呼び出して、それぞれの結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="832de-159">The dynamic methods provided by the `ReadOnlyFile` class call the `GetPropertyValue` method to retrieve their respective results.</span></span>

    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]

1. <span data-ttu-id="832de-160">`GetPropertyValue` メソッドの後に、<xref:System.Dynamic.DynamicObject> クラスの <xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドをオーバーライドする次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="832de-160">After the `GetPropertyValue` method, add the following code to override the <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method of the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="832de-161"><xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドは、動的クラスのメンバーが要求され、引数が指定されていない場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="832de-161">The <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method is called when a member of a dynamic class is requested and no arguments are specified.</span></span> <span data-ttu-id="832de-162">`binder` 引数には、参照されているメンバーに関する情報が含まれます。`result` 引数は、指定したメンバーに対して返された結果を参照します。</span><span class="sxs-lookup"><span data-stu-id="832de-162">The `binder` argument contains information about the referenced member, and the `result` argument references the result returned for the specified member.</span></span> <span data-ttu-id="832de-163"><xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドはブール値を返します。要求されたメンバーが存在する場合には `true` を返し、その他の場合には `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="832de-163">The <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method returns a Boolean value that returns `true` if the requested member exists; otherwise it returns `false`.</span></span>

    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]

1. <span data-ttu-id="832de-164">`TryGetMember` メソッドの後に、<xref:System.Dynamic.DynamicObject> クラスの <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドをオーバーライドする次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="832de-164">After the `TryGetMember` method, add the following code to override the <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method of the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="832de-165"><xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドは、動的クラスのメンバーが引数を使用して要求された場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="832de-165">The <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method is called when a member of a dynamic class is requested with arguments.</span></span> <span data-ttu-id="832de-166">`binder` 引数には、参照されているメンバーに関する情報が含まれます。`result` 引数は、指定したメンバーに対して返された結果を参照します。</span><span class="sxs-lookup"><span data-stu-id="832de-166">The `binder` argument contains information about the referenced member, and the `result` argument references the result returned for the specified member.</span></span> <span data-ttu-id="832de-167">`args` 引数には、メンバーに渡される引数の配列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="832de-167">The `args` argument contains an array of the arguments that are passed to the member.</span></span> <span data-ttu-id="832de-168"><xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドはブール値を返します。要求されたメンバーが存在する場合には `true` を返し、その他の場合には `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="832de-168">The <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method returns a Boolean value that returns `true` if the requested member exists; otherwise it returns `false`.</span></span>

    <span data-ttu-id="832de-169">`TryInvokeMember` メソッドのカスタム バージョンは、1 つ目の引数として、前の手順で定義した `StringSearchOption` 列挙からの値を受け付けます。</span><span class="sxs-lookup"><span data-stu-id="832de-169">The custom version of the `TryInvokeMember` method expects the first argument to be a value from the `StringSearchOption` enum that you defined in a previous step.</span></span> <span data-ttu-id="832de-170">`TryInvokeMember` メソッドは、2 つ目の引数としてブール値を受け付けます。</span><span class="sxs-lookup"><span data-stu-id="832de-170">The `TryInvokeMember` method expects the second argument to be a Boolean value.</span></span> <span data-ttu-id="832de-171">引数の一方または両方が有効な値であれば、それらが `GetPropertyValue` メソッドに渡され、結果が取得されます。</span><span class="sxs-lookup"><span data-stu-id="832de-171">If one or both arguments are valid values, they are passed to the `GetPropertyValue` method to retrieve the results.</span></span>

    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]

1. <span data-ttu-id="832de-172">ファイルを保存して閉じます。</span><span class="sxs-lookup"><span data-stu-id="832de-172">Save and close the file.</span></span>

### <a name="to-create-a-sample-text-file"></a><span data-ttu-id="832de-173">サンプルのテキスト ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="832de-173">To create a sample text file</span></span>

1. <span data-ttu-id="832de-174">**ソリューション エクスプローラー** で、DynamicSample プロジェクトを右クリックし、 **[追加]**  >  **[新しい項目]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="832de-174">In **Solution Explorer**, right-click the DynamicSample project and select **Add** > **New Item**.</span></span> <span data-ttu-id="832de-175">**[インストールされたテンプレート]** ペインで **[全般]** をクリックし、 **[テキスト ファイル]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="832de-175">In the **Installed Templates** pane, select **General**, and then select the **Text File** template.</span></span> <span data-ttu-id="832de-176">**[名前]** ボックスで、既定の名前である *TextFile1.txt* をそのままにし、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="832de-176">Leave the default name of *TextFile1.txt* in the **Name** box, and then click **Add**.</span></span> <span data-ttu-id="832de-177">新しいテキスト ファイルがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="832de-177">A new text file is added to the project.</span></span>

1. <span data-ttu-id="832de-178">*TextFile1.txt* ファイルに次のテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="832de-178">Copy the following text to the *TextFile1.txt* file.</span></span>

    ```text
    List of customers and suppliers

    Supplier: Lucerne Publishing (https://www.lucernepublishing.com/)
    Customer: Preston, Chris
    Customer: Hines, Patrick
    Customer: Cameron, Maria
    Supplier: Graphic Design Institute (https://www.graphicdesigninstitute.com/)
    Supplier: Fabrikam, Inc. (https://www.fabrikam.com/)
    Customer: Seubert, Roxanne
    Supplier: Proseware, Inc. (http://www.proseware.com/)
    Customer: Adolphi, Stephan
    Customer: Koch, Paul
    ```

1. <span data-ttu-id="832de-179">ファイルを保存して閉じます。</span><span class="sxs-lookup"><span data-stu-id="832de-179">Save and close the file.</span></span>

### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a><span data-ttu-id="832de-180">カスタム動的オブジェクトを使用するサンプル アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="832de-180">To create a sample application that uses the custom dynamic object</span></span>

1. <span data-ttu-id="832de-181">**ソリューション エクスプローラー** で、Visual Basic をお使いの場合は *Program.vb* ファイルを、Visual C# をお使いの場合は *Program.cs* ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="832de-181">In **Solution Explorer**, double-click the *Program.vb* file if you're using Visual Basic or the *Program.cs* file if you're using Visual C#.</span></span>

2. <span data-ttu-id="832de-182">`Main` プロシージャに次のコードを追加して、*TextFile1.txt* ファイル用に `ReadOnlyFile` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="832de-182">Add the following code to the `Main` procedure to create an instance of the `ReadOnlyFile` class for the *TextFile1.txt* file.</span></span> <span data-ttu-id="832de-183">このコードは、遅延バインディングを使用して動的メンバーを呼び出し、"Customer" という文字列を含んだテキスト行を取得します。</span><span class="sxs-lookup"><span data-stu-id="832de-183">The code uses late binding to call dynamic members and retrieve lines of text that contain the string "Customer".</span></span>

     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/Program.vb#8)]

3. <span data-ttu-id="832de-184">ファイルを保存し、<kbd>Ctrl</kdb>+<kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="832de-184">Save the file and press <kbd>Ctrl</kdb>+<kbd>F5</kbd> to build and run the application.</span></span>

## <a name="call-a-dynamic-language-library"></a><span data-ttu-id="832de-185">動的言語ライブラリの呼び出し</span><span class="sxs-lookup"><span data-stu-id="832de-185">Call a dynamic language library</span></span>

<span data-ttu-id="832de-186">次のチュートリアルでは、動的言語 IronPython で記述されたライブラリにアクセスするプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="832de-186">The following walkthrough creates a project that accesses a library that is written in the dynamic language IronPython.</span></span>

### <a name="to-create-a-custom-dynamic-class"></a><span data-ttu-id="832de-187">カスタムの動的クラスを作成するには</span><span class="sxs-lookup"><span data-stu-id="832de-187">To create a custom dynamic class</span></span>

1. <span data-ttu-id="832de-188">Visual Studio で、 **[ファイル]**  >  **[新規]**  >  **[プロジェクト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="832de-188">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="832de-189">**[新しいプロジェクトの作成]** ダイアログで、[C#] または [Visual Basic] を選択し、 **[コンソール アプリケーション]** を選択して、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="832de-189">In the **Create a new project** dialog, select C# or Visual Basic, select **Console Application**, and then select **Next**.</span></span>

1. <span data-ttu-id="832de-190">**[新しいプロジェクトの構成]** ダイアログで、 **[プロジェクト名]** に「`DynamicIronPythonSample`」と入力し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="832de-190">In the **Configure your new project** dialog, enter `DynamicIronPythonSample` for the **Project name**, and then select **Next**.</span></span>

1. <span data-ttu-id="832de-191">**[追加情報]** ダイアログで、 **[ターゲット フレームワーク]** に **[.NET 5.0 (Current)]** を選んでから、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="832de-191">In the **Additional information** dialog, select **.NET 5.0 (Current)** for the **Target Framework**, and then select **Create**.</span></span>

   <span data-ttu-id="832de-192">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="832de-192">The new project is created.</span></span>

1. <span data-ttu-id="832de-193">[IronPython](https://www.nuget.org/packages/IronPython) NuGet パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="832de-193">Install the [IronPython](https://www.nuget.org/packages/IronPython) NuGet package.</span></span>

1. <span data-ttu-id="832de-194">Visual Basic をお使いの場合は、*Program.vb* ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="832de-194">If you're using Visual Basic, edit the *Program.vb* file.</span></span> <span data-ttu-id="832de-195">Visual C# をお使いの場合は、*Program.cs* ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="832de-195">If you're using Visual C#, edit the *Program.cs* file.</span></span>

1. <span data-ttu-id="832de-196">ファイルの先頭に次のコードを追加して、IronPython ライブラリと `System.Linq` 名前空間から `Microsoft.Scripting.Hosting` および `IronPython.Hosting` 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="832de-196">At the top of the file, add the following code to import the `Microsoft.Scripting.Hosting` and `IronPython.Hosting` namespaces from the IronPython libraries and the `System.Linq` namespace.</span></span>

    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/Program.vb#1)]

1. <span data-ttu-id="832de-197">Main メソッドで、IronPython ライブラリをホストする新しい `Microsoft.Scripting.Hosting.ScriptRuntime` オブジェクトを作成するための次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="832de-197">In the Main method, add the following code to create a new `Microsoft.Scripting.Hosting.ScriptRuntime` object to host the IronPython libraries.</span></span> <span data-ttu-id="832de-198">`ScriptRuntime` オブジェクトは、IronPython ライブラリ モジュール random.py を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="832de-198">The `ScriptRuntime` object loads the IronPython library module random.py.</span></span>

     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/Program.vb#2)]

1. <span data-ttu-id="832de-199">Random.py モジュールを読み込むコードの後に、整数の配列を作成する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="832de-199">After the code to load the random.py module, add the following code to create an array of integers.</span></span> <span data-ttu-id="832de-200">配列は random.py モジュールの `shuffle` メソッドに渡されます。このメソッドは、配列内の値をランダムに並べ替えします。</span><span class="sxs-lookup"><span data-stu-id="832de-200">The array is passed to the `shuffle` method of the random.py module, which randomly sorts the values in the array.</span></span>

     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/Program.vb#3)]

1. <span data-ttu-id="832de-201">ファイルを保存し、<kbd>Ctrl</kdb>+<kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="832de-201">Save the file and press <kbd>Ctrl</kdb>+<kbd>F5</kbd> to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="832de-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="832de-202">See also</span></span>

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [<span data-ttu-id="832de-203">dynamic 型の使用</span><span class="sxs-lookup"><span data-stu-id="832de-203">Using Type dynamic</span></span>](./using-type-dynamic.md)
- [<span data-ttu-id="832de-204">事前バインディングと遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="832de-204">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="832de-205">dynamic</span><span class="sxs-lookup"><span data-stu-id="832de-205">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="832de-206">動的なインターフェイスの実装 (Microsoft TechNet からダウンロードできる PDF)</span><span class="sxs-lookup"><span data-stu-id="832de-206">Implementing Dynamic Interfaces (downloadable PDF from Microsoft TechNet)</span></span>](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)

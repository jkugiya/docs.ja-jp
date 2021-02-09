---
description: "詳細情報: BC30451:名前 '<name>' は宣言されていません。"
title: 名前 '<name>' は宣言されていません。
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 8d76bcfd18b277a5f542f363cb906496680bae29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795743"
---
# <a name="bc30451-name-name-is-not-declared"></a><span data-ttu-id="f498e-103">BC30451:名前 '\<name>' は宣言されていません。</span><span class="sxs-lookup"><span data-stu-id="f498e-103">BC30451: Name '\<name>' is not declared</span></span>

<span data-ttu-id="f498e-104">ステートメントでプログラミング要素を参照していますが、名前が完全に一致する要素をコンパイラが見つけることができません。</span><span class="sxs-lookup"><span data-stu-id="f498e-104">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>

 <span data-ttu-id="f498e-105">**エラー ID:** BC30451</span><span class="sxs-lookup"><span data-stu-id="f498e-105">**Error ID:** BC30451</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="f498e-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="f498e-106">To correct this error</span></span>

1. <span data-ttu-id="f498e-107">参照元のステートメントで名前のスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="f498e-107">Check the spelling of the name in the referring statement.</span></span> <span data-ttu-id="f498e-108">Visual Basic では、大文字と小文字が区別されませんが、スペルに他の何らかの違いがあった場合は完全に異なる名前と見なされます。</span><span class="sxs-lookup"><span data-stu-id="f498e-108">Visual Basic is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="f498e-109">アンダースコア (`_`) も名前の一部であり、スペルに含まれます。</span><span class="sxs-lookup"><span data-stu-id="f498e-109">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>

2. <span data-ttu-id="f498e-110">オブジェクトとそのメンバーの間にメンバー アクセス演算子 (`.`) を指定していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f498e-110">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="f498e-111">たとえば、 <xref:System.Windows.Forms.TextBox> という名前の `TextBox1`コントロールがある場合、このコントロールの <xref:System.Windows.Forms.TextBoxBase.Text%2A> プロパティにアクセスするには、「 `TextBox1.Text`」と入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f498e-111">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="f498e-112">代わりに「 `TextBox1Text`」と入力した場合、別の名前と見なされます。</span><span class="sxs-lookup"><span data-stu-id="f498e-112">If instead you type `TextBox1Text`, you have created a different name.</span></span>

3. <span data-ttu-id="f498e-113">スペルが正しく、オブジェクト メンバー アクセスの構文が正しい場合は、要素が宣言されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f498e-113">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="f498e-114">詳細については、[宣言された要素](../../programming-guide/language-features/declared-elements/index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f498e-114">For more information, see [Declared Elements](../../programming-guide/language-features/declared-elements/index.md).</span></span>

4. <span data-ttu-id="f498e-115">プログラミング要素が宣言されている場合、それがスコープ内にあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f498e-115">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="f498e-116">参照元のステートメントがプログラミング要素を宣言している領域の外部にある場合は、要素名を修飾する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="f498e-116">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="f498e-117">詳細については、「 [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f498e-117">For more information, see [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span></span>

5. <span data-ttu-id="f498e-118">完全修飾型または型とメンバー名を使用していない (たとえば、コードで `System.Reflection.MethodInfo.Name` ではなく `MethodInfo.Name` としてプロパティを参照している) 場合は、[Imports ステートメント](../statements/imports-statement-net-namespace-and-type.md)を追加します。</span><span class="sxs-lookup"><span data-stu-id="f498e-118">If you are not using a fully qualified type or type and member name (for example, your code refers to a property as `MethodInfo.Name` instead of `System.Reflection.MethodInfo.Name`), add an [Imports statement](../statements/imports-statement-net-namespace-and-type.md).</span></span>

6. <span data-ttu-id="f498e-119">SDK スタイルのプロジェクト (`<Project Sdk="Microsoft.NET.Sdk">` 行で始まる \*.vbproj ファイルによるプロジェクト) をコンパイルしようとし、エラーメッセージで、Microsoft.VisualBasic.dll アセンブリの型またはメンバーが参照されている場合は、Visual Basic ランタイム ライブラリへの参照を使用してコンパイルするようにアプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="f498e-119">If you are attempting to compile an SDK-style project (a project with a \*.vbproj file that begins with the line `<Project Sdk="Microsoft.NET.Sdk">`), and the error message refers to a type or member in the Microsoft.VisualBasic.dll assembly, configure your application to compile with a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="f498e-120">既定で、ライブラリのサブセットは、SDK スタイルのプロジェクトのアセンブリに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="f498e-120">By default, a subset of the library is embedded in your assembly in an SDK-style project.</span></span>

   <span data-ttu-id="f498e-121">たとえば、次の例では、<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> メソッドが見つからないため、コンパイルに失敗します。</span><span class="sxs-lookup"><span data-stu-id="f498e-121">For example, the following example fails to compile because the <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> method cannot be found.</span></span> <span data-ttu-id="f498e-122">アプリケーションに含まれている Visual Basic ランタイムのサブセットに埋め込まれていません。</span><span class="sxs-lookup"><span data-stu-id="f498e-122">It is not embedded in the subset of the Visual Basic Runtime included with your application.</span></span>

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   <span data-ttu-id="f498e-123">このエラーに対処するには、次の Visual Basic プロジェクト ファイルに示すように、プロジェクトの `<PropertyGroup>` セクションに `<VBRuntime>Default</VBRuntime>` 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="f498e-123">To address this error, add the `<VBRuntime>Default</VBRuntime>` element to the projects `<PropertyGroup>` section, as the following Visual Basic project file shows.</span></span>

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a><span data-ttu-id="f498e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="f498e-124">See also</span></span>

- [<span data-ttu-id="f498e-125">宣言と定数の概要</span><span class="sxs-lookup"><span data-stu-id="f498e-125">Declarations and Constants Summary</span></span>](../keywords/declarations-and-constants-summary.md)
- [<span data-ttu-id="f498e-126">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="f498e-126">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="f498e-127">宣言された要素の名前</span><span class="sxs-lookup"><span data-stu-id="f498e-127">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="f498e-128">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="f498e-128">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

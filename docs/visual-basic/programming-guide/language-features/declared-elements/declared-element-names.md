---
description: '詳細情報: 宣言された要素の名前 (Visual Basic)'
title: 宣言された要素の名前
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: ba0a6d6b236c0c4e9ce81c37a1cca4e709cc5588
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425686"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="ebfb0-103">宣言された要素の名前 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebfb0-103">Declared Element Names (Visual Basic)</span></span>

<span data-ttu-id="ebfb0-104">宣言されたすべての要素には名前が付いています。これは *識別子* とも呼ばれ、コードが参照するために使用するものです。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-104">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ebfb0-105">ルール</span><span class="sxs-lookup"><span data-stu-id="ebfb0-105">Rules</span></span>  

 <span data-ttu-id="ebfb0-106">Visual Basic 内の要素名は、次のルールを守る必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-106">An element name in Visual Basic must observe the following rules:</span></span>  
  
- <span data-ttu-id="ebfb0-107">先頭は英文字またはアンダースコア (`_`) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-107">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="ebfb0-108">含めることができるのは、英字、10 進数の数字、アンダースコアのみです。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-108">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
- <span data-ttu-id="ebfb0-109">アンダースコアで始まる場合は、少なくとも 1 つの英字または 10 進数の数字が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-109">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
- <span data-ttu-id="ebfb0-110">1023 文字以下にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-110">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="ebfb0-111">1023 文字の長さの制限は、`outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement` など、完全修飾名の文字列全体にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-111">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="ebfb0-112">いくつかの有効な要素名を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-112">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="ebfb0-113">いくつかの無効な要素名を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-113">The following example shows some invalid element names.</span></span> <span data-ttu-id="ebfb0-114">1 つ目にはアンダースコアのみが含まれ、2 つ目は 10 進数の数字で始まり、3 つ目には無効な文字 ($) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-114">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> <span data-ttu-id="ebfb0-115">アンダースコア (`_`) で始まる要素名は、[言語への非依存性、および言語非依存コンポーネント](../../../../standard/language-independence-and-language-independent-components.md) (CLS) の一部ではないため、CLS 準拠のコードでは、このような名前を定義するコンポーネントを使用できません。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-115">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="ebfb0-116">ただし、要素名の他の位置にあるアンダースコアは CLS に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-116">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="ebfb0-117">名前の長さのガイドライン</span><span class="sxs-lookup"><span data-stu-id="ebfb0-117">Name Length Guidelines</span></span>  

 <span data-ttu-id="ebfb0-118">現実問題として、名前は、可能な限り短くしながらも、要素の性質を明確に特定するものにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-118">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="ebfb0-119">これにより、コードの読みやすさが向上し、行の長さとソース ファイルのサイズが減少します。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-119">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="ebfb0-120">一方、要素が何を表し、コードがそれをどのように使用するかを適切に説明できないほど短い名前にはしないでください。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-120">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="ebfb0-121">これはコードの読みやすさのために重要です。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-121">This is important for the readability of your code.</span></span> <span data-ttu-id="ebfb0-122">他のユーザーが理解しようとするとき、またはユーザー自身がそれを記述してから長い間が経っている場合でも、適切な要素名にすることでかなりの時間を節約できます。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-122">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="ebfb0-123">エスケープされた名前</span><span class="sxs-lookup"><span data-stu-id="ebfb0-123">Escaped Names</span></span>  

 <span data-ttu-id="ebfb0-124">一般に、要素名は、Visual Basic によって予約されているキーワード (`Case` や `Friend` など) と一致しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-124">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="ebfb0-125">ただし、*エスケープされた名前* を定義できます。これは、角かっこ (`[ ]`) で囲まれています。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-125">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="ebfb0-126">エスケープされた名前は、角かっこによってあいまいさが解消されるため、どの Visual Basic キーワードとも一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-126">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="ebfb0-127">また、コード内で後で名前を参照するときにも、角かっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-127">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="ebfb0-128">通常、エスケープされた名前は、次の場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-128">In general, you should use escaped names only when:</span></span>  
  
- <span data-ttu-id="ebfb0-129">コードが、名前として使用されるキーワードを予約しなかった以前のバージョンの Visual Basic から移行された。または、</span><span class="sxs-lookup"><span data-stu-id="ebfb0-129">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
- <span data-ttu-id="ebfb0-130">指定されたキーワードが予約されていない別の言語で記述されたコードを操作している。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-130">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="ebfb0-131">それ以外の場合、名前がキーワードと競合する場合は、要素の名前を変更することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-131">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="ebfb0-132">統合開発環境 (IDE) を使用すると、この操作を簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-132">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="ebfb0-133">詳細については、[リファクタリング](/visualstudio/ide/refactoring-in-visual-studio)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-133">For more information, see [Refactoring](/visualstudio/ide/refactoring-in-visual-studio).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="ebfb0-134">名前の大文字と小文字の区別</span><span class="sxs-lookup"><span data-stu-id="ebfb0-134">Case Sensitivity in Names</span></span>  

 <span data-ttu-id="ebfb0-135">Visual Basic の要素名は、大文字と小文字を区別しません。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-135">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="ebfb0-136">つまり、英字の大文字と小文字の違いしかない 2 つの名前を比較した場合、コンパイラはそれらを同じ名前と解釈します。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-136">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="ebfb0-137">たとえば、 `ABC` と `abc` は、宣言された同じ要素を参照していると見なされます。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-137">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="ebfb0-138">しかし、共通言語ランタイム (CLR) のバインディングでは大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-138">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="ebfb0-139">このため、アセンブリまたは DLL を作成し、他のアセンブリで使用できるようにすると、名前の大文字と小文字が区別されるようになります。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-139">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="ebfb0-140">たとえば、 `ABC`という名前の要素を持つクラスを定義し、他のアセンブリから共通言語ランタイムを通じてこのクラスを使用する場合は、この要素を `ABC`として参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-140">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="ebfb0-141">後でクラスを再コンパイルして要素の名前を `abc` に変更すると、このクラスを使用していた他のアセンブリがこの要素にアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-141">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="ebfb0-142">したがって、アセンブリを更新してリリースするときは、パブリックな要素の名前の大文字と小文字を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-142">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="ebfb0-143">名前とロケール</span><span class="sxs-lookup"><span data-stu-id="ebfb0-143">Names and Locales</span></span>  

 <span data-ttu-id="ebfb0-144">名前の比較は、ロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-144">Comparison of names is independent of locale.</span></span> <span data-ttu-id="ebfb0-145">2 つの名前が 1 つのロケールで一致する場合は、すべてのロケールで一致することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="ebfb0-145">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebfb0-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebfb0-146">See also</span></span>

- [<span data-ttu-id="ebfb0-147">宣言された要素</span><span class="sxs-lookup"><span data-stu-id="ebfb0-147">Declared Elements</span></span>](index.md)
- [<span data-ttu-id="ebfb0-148">宣言された要素の特性</span><span class="sxs-lookup"><span data-stu-id="ebfb0-148">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="ebfb0-149">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="ebfb0-149">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="ebfb0-150">ステートメント</span><span class="sxs-lookup"><span data-stu-id="ebfb0-150">Statements</span></span>](../../../language-reference/statements/index.md)

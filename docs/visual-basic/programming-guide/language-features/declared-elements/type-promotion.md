---
description: '詳細情報: 型の上位変換 (Visual Basic)'
title: 型の上位変換
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: fd8a30fb7e442d82222ae55daabf70bd8e532138
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434720"
---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="ec4e5-103">型の上位変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec4e5-103">Type Promotion (Visual Basic)</span></span>

<span data-ttu-id="ec4e5-104">モジュールでプログラミング要素を宣言すると、Visual Basic によって、そのスコープがモジュールを含む名前空間に昇格されます。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-104">When you declare a programming element in a module, Visual Basic promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="ec4e5-105">これは *型の上位変換* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-105">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="ec4e5-106">次の例では、モジュールのスケルトン定義とそのモジュールの 2 つのメンバーを示しています。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-106">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="ec4e5-107">`projModule` 内で、モジュール レベルで宣言されたプログラミング要素が `projNamespace` に昇格されます。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-107">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="ec4e5-108">前の例では、`basicEnum` と `innerClass` は昇格されますが、`numberSub` は、モジュール レベルで宣言されていないため、昇格されません。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-108">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="ec4e5-109">型の上位変換の効果</span><span class="sxs-lookup"><span data-stu-id="ec4e5-109">Effect of Type Promotion</span></span>  

 <span data-ttu-id="ec4e5-110">型の上位変換の効果は、修飾文字列にモジュール名を含める必要がないことです。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-110">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="ec4e5-111">次の例では、前の例のプロシージャを 2 回呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-111">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 <span data-ttu-id="ec4e5-112">前の例では、最初の呼び出しで完全修飾文字列を使用しています。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-112">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="ec4e5-113">ただし、型の上位変換のため、これは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-113">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="ec4e5-114">2 番目の呼び出しでは、修飾文字列に `projModule` を含めずに、モジュールのメンバーにアクセスしています。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-114">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="ec4e5-115">型の上位変換の無効化</span><span class="sxs-lookup"><span data-stu-id="ec4e5-115">Defeat of Type Promotion</span></span>  

 <span data-ttu-id="ec4e5-116">名前空間にモジュール メンバーと同じ名前のメンバーが既に存在する場合、そのモジュール メンバーに対して型の上位変換は無効になります。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-116">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="ec4e5-117">次の例では、同じ名前空間内の列挙とモジュールのスケルトン定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-117">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 <span data-ttu-id="ec4e5-118">前の例では、名前空間レベルで同じ名前を持つ列挙が既に存在するため、Visual Basic がクラス `abc` を `thisNameSpace` に昇格できません。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-118">In the preceding example, Visual Basic cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="ec4e5-119">`abcSub` にアクセスするには、完全修飾文字列 `thisNamespace.thisModule.abc.abcSub` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-119">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="ec4e5-120">ただし、クラス `xyz` は引き続き昇格され、短い修飾文字列 `thisNamespace.xyz.xyzSub` で、`xyzSub` にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-120">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="ec4e5-121">部分型の型の上位変換の無効化</span><span class="sxs-lookup"><span data-stu-id="ec4e5-121">Defeat of Type Promotion for Partial Types</span></span>  

 <span data-ttu-id="ec4e5-122">モジュール内のクラスまたは構造体で [Partial](../../../language-reference/modifiers/partial.md) キーワードを使用している場合は、名前空間に同じ名前のメンバーが含まれているかどうかに関係なく、そのクラスまたは構造体に対する型の上位変換が自動的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-122">If a class or structure inside a module uses the [Partial](../../../language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="ec4e5-123">モジュール内の他の要素は、引き続き型の上位変換の対象になります。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-123">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="ec4e5-124">**結果。**</span><span class="sxs-lookup"><span data-stu-id="ec4e5-124">**Consequences.**</span></span> <span data-ttu-id="ec4e5-125">部分定義の型の上位変換の無効化によって、予期しない結果が発生したり、コンパイラ エラーが発生したりすることもあります。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-125">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="ec4e5-126">次の例では、クラスのスケルトンの部分定義を示しており、そのうちの 1 つがモジュール内にあります。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-126">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 <span data-ttu-id="ec4e5-127">前の例で、開発者は、コンパイラに `sampleClass` の 2 つの部分定義をマージすることを期待するかもしれません。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-127">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="ec4e5-128">しかし、コンパイラでは `sampleModule` 内の部分定義の上位変換が考慮されません。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-128">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="ec4e5-129">そのため、どちらも `sampleClass` という名前が付けられていますが、修飾パスが異なる 2 つの個別のクラスのコンパイルが試みられます。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-129">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="ec4e5-130">コンパイラは、完全修飾されたパスがまったく同じ場合にのみ、部分定義をマージします。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-130">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="ec4e5-131">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ec4e5-131">Recommendations</span></span>  

 <span data-ttu-id="ec4e5-132">次の推奨事項は、優れたプログラミング方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-132">The following recommendations represent good programming practice.</span></span>  
  
- <span data-ttu-id="ec4e5-133">**一意の名前。**</span><span class="sxs-lookup"><span data-stu-id="ec4e5-133">**Unique Names.**</span></span> <span data-ttu-id="ec4e5-134">プログラミング要素の名前付けを完全に制御できる場合は、どこでも一意の名前を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-134">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="ec4e5-135">同一の名前は追加の修飾が必要であり、コードが読みにくくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-135">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="ec4e5-136">それらは、軽度のエラーや予期しない結果につながる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-136">They can also lead to subtle errors and unexpected results.</span></span>  
  
- <span data-ttu-id="ec4e5-137">**完全修飾。**</span><span class="sxs-lookup"><span data-stu-id="ec4e5-137">**Full Qualification.**</span></span> <span data-ttu-id="ec4e5-138">同じ名前空間内のモジュールやその他の要素を操作する場合、最も安全な方法は、すべてのプログラミング要素に対して常に完全修飾を使用することです。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-138">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="ec4e5-139">モジュール メンバーの型の上位変換が無効になっていて、そのメンバーを完全に修飾していない場合、誤って別のプログラミング要素にアクセスする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec4e5-139">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4e5-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec4e5-140">See also</span></span>

- [<span data-ttu-id="ec4e5-141">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="ec4e5-141">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="ec4e5-142">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="ec4e5-142">Namespace Statement</span></span>](../../../language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="ec4e5-143">Partial</span><span class="sxs-lookup"><span data-stu-id="ec4e5-143">Partial</span></span>](../../../language-reference/modifiers/partial.md)
- [<span data-ttu-id="ec4e5-144">Visual Basic におけるスコープ</span><span class="sxs-lookup"><span data-stu-id="ec4e5-144">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="ec4e5-145">方法: 変数のスコープを制御する</span><span class="sxs-lookup"><span data-stu-id="ec4e5-145">How to: Control the Scope of a Variable</span></span>](how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="ec4e5-146">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="ec4e5-146">References to Declared Elements</span></span>](references-to-declared-elements.md)

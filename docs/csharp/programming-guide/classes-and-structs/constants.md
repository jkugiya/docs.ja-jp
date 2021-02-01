---
title: 定数 - C# プログラミング ガイド
description: C# の定数は、プログラムのコンパイル後に変更されない、コンパイル時リテラル値です。 C# の組み込み型だけが定数になります。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 4783aff8e9424c90e46cb52692a3e645e995d914
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899075"
---
# <a name="constants-c-programming-guide"></a><span data-ttu-id="d9156-104">定数 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="d9156-104">Constants (C# Programming Guide)</span></span>

<span data-ttu-id="d9156-105">定数とは、コンパイル時に既知であり、プログラムの実行期間を通じて変更されない値です。</span><span class="sxs-lookup"><span data-stu-id="d9156-105">Constants are immutable values which are known at compile time and do not change for the life of the program.</span></span> <span data-ttu-id="d9156-106">定数を宣言するには、[const](../../language-reference/keywords/const.md) 修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="d9156-106">Constants are declared with the [const](../../language-reference/keywords/const.md) modifier.</span></span> <span data-ttu-id="d9156-107">`const` として宣言できるのは、C# [組み込み型](../../language-reference/builtin-types/built-in-types.md) (<xref:System.Object?displayProperty=nameWithType> を除く) のみです。</span><span class="sxs-lookup"><span data-stu-id="d9156-107">Only the C# [built-in types](../../language-reference/builtin-types/built-in-types.md) (excluding <xref:System.Object?displayProperty=nameWithType>) may be declared as `const`.</span></span> <span data-ttu-id="d9156-108">クラス、構造体、配列などのユーザー定義型を `const` にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d9156-108">User-defined types, including classes, structs, and arrays, cannot be `const`.</span></span> <span data-ttu-id="d9156-109">実行時に (コンストラクターなどで) 一度だけ初期化され、その後は変更できないクラス、構造体、または配列を作成するには、[readonly](../../language-reference/keywords/readonly.md) 修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="d9156-109">Use the [readonly](../../language-reference/keywords/readonly.md) modifier to create a class, struct, or array that is initialized one time at runtime (for example in a constructor) and thereafter cannot be changed.</span></span>  
  
 <span data-ttu-id="d9156-110">C# では、`const` のメソッド、プロパティ、またはイベントはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d9156-110">C# does not support `const` methods, properties, or events.</span></span>  
  
 <span data-ttu-id="d9156-111">enum 型を使用すると、組み込みの整数型 (`int`、`uint`、`long` など) の名前付き定数を定義できます。</span><span class="sxs-lookup"><span data-stu-id="d9156-111">The enum type enables you to define named constants for integral built-in types (for example `int`, `uint`, `long`, and so on).</span></span> <span data-ttu-id="d9156-112">詳細については、「[enum](../../language-reference/builtin-types/enum.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9156-112">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="d9156-113">定数は、宣言するときに初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9156-113">Constants must be initialized as they are declared.</span></span> <span data-ttu-id="d9156-114">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d9156-114">For example:</span></span>  
  
 [!code-csharp[Calendar#1](snippets/constants/Calendar.cs#1)]
  
 <span data-ttu-id="d9156-115">この例では、定数 `Months` は常に 12 になり、クラス自体によっても変更できません。</span><span class="sxs-lookup"><span data-stu-id="d9156-115">In this example, the constant `Months` is always 12, and it cannot be changed even by the class itself.</span></span> <span data-ttu-id="d9156-116">実際、コンパイラが C# ソース コードで定数の識別子 (この場合は `Months`) を検出すると、コンパイラが生成する中間言語 (IL) コードには、識別子の代わりにリテラル値が直接出力されます。</span><span class="sxs-lookup"><span data-stu-id="d9156-116">In fact, when the compiler encounters a constant identifier in C# source code (for example, `Months`), it substitutes the literal value directly into the intermediate language (IL) code that it produces.</span></span> <span data-ttu-id="d9156-117">実行時に定数に関連付けられる変数アドレスが存在しないため、`const` フィールドは、参照渡しすることも、式の左辺値として指定することもできません。</span><span class="sxs-lookup"><span data-stu-id="d9156-117">Because there is no variable address associated with a constant at run time, `const` fields cannot be passed by reference and cannot appear as an l-value in an expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9156-118">DLL などの他のコードに定義されている定数値を参照するときは、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="d9156-118">Use caution when you refer to constant values defined in other code such as DLLs.</span></span> <span data-ttu-id="d9156-119">新しいバージョンの DLL で定数の新しい値を定義しても、その新バージョンを対象にプログラムを再コンパイルするまで、プログラムには古いリテラル値が保持されたままになります。</span><span class="sxs-lookup"><span data-stu-id="d9156-119">If a new version of the DLL defines a new value for the constant, your program will still hold the old literal value until it is recompiled against the new version.</span></span>  
  
 <span data-ttu-id="d9156-120">同じ型の複数の定数を、次のように同時に宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d9156-120">Multiple constants of the same type can be declared at the same time, for example:</span></span>  
  
 [!code-csharp[Calendar#2](snippets/constants/Calendar.cs#2)]
  
 <span data-ttu-id="d9156-121">定数の初期化に使用する式は、循環参照を形成しない限り別の定数を参照できます。</span><span class="sxs-lookup"><span data-stu-id="d9156-121">The expression that is used to initialize a constant can refer to another constant if it does not create a circular reference.</span></span> <span data-ttu-id="d9156-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d9156-122">For example:</span></span>  
  
 [!code-csharp[Calendar#3](snippets/constants/Calendar.cs#3)]
  
 <span data-ttu-id="d9156-123">定数は、[public](../../language-reference/keywords/public.md)、[private](../../language-reference/keywords/private.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md) または [private protected](../../language-reference/keywords/private-protected.md) としてマークできます。</span><span class="sxs-lookup"><span data-stu-id="d9156-123">Constants can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="d9156-124">これらのアクセス修飾子により、クラスのユーザーが定数にアクセスする方法が定義されます。</span><span class="sxs-lookup"><span data-stu-id="d9156-124">These access modifiers define how users of the class can access the constant.</span></span> <span data-ttu-id="d9156-125">詳細については、「[アクセス修飾子](./access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9156-125">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="d9156-126">定数の値は型のすべてのインスタンスで同じであるため、定数は[静的](../../language-reference/keywords/static.md)フィールドのようにアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="d9156-126">Constants are accessed as if they were [static](../../language-reference/keywords/static.md) fields because the value of the constant is the same for all instances of the type.</span></span> <span data-ttu-id="d9156-127">定数の宣言に `static` キーワードは使用しません。</span><span class="sxs-lookup"><span data-stu-id="d9156-127">You do not use the `static` keyword to declare them.</span></span> <span data-ttu-id="d9156-128">定数を定義しているクラスに含まれていない式で定数を使用する場合は、クラス名、ピリオド、定数の名前を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9156-128">Expressions that are not in the class that defines the constant must use the class name, a period, and the name of the constant to access the constant.</span></span> <span data-ttu-id="d9156-129">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d9156-129">For example:</span></span>  
  
 [!code-csharp[Calendar#4](snippets/constants/Calendar.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="d9156-130">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="d9156-130">C# Language Specification</span></span>  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d9156-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9156-131">See also</span></span>

- [<span data-ttu-id="d9156-132">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="d9156-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d9156-133">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="d9156-133">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="d9156-134">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d9156-134">Properties</span></span>](./properties.md)
- [<span data-ttu-id="d9156-135">型</span><span class="sxs-lookup"><span data-stu-id="d9156-135">Types</span></span>](../types/index.md)
- [<span data-ttu-id="d9156-136">readonly</span><span class="sxs-lookup"><span data-stu-id="d9156-136">readonly</span></span>](../../language-reference/keywords/readonly.md)
- [<span data-ttu-id="d9156-137">C# の不変性パート 1: 不変性の種類</span><span class="sxs-lookup"><span data-stu-id="d9156-137">Immutability in C# Part One: Kinds of Immutability</span></span>](/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability)

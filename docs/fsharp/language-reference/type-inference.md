---
title: 型推論
description: F# コンパイラが値、変数、パラメーター、戻り値の型を推定する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 4b18c1a67a8b7ddadb4fb334ea4736e9fd29feb0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630188"
---
# <a name="type-inference"></a><span data-ttu-id="6dbb0-103">型推論</span><span class="sxs-lookup"><span data-stu-id="6dbb0-103">Type Inference</span></span>

<span data-ttu-id="6dbb0-104">このトピックでは、F# コンパイラが値、変数、パラメーター、戻り値の型を推定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="6dbb0-105">型の推定一般</span><span class="sxs-lookup"><span data-stu-id="6dbb0-105">Type Inference in General</span></span>

<span data-ttu-id="6dbb0-106">型の推定の概念は、コンパイラが最終的に型を推測できない場合を除いて、F# コンストラクトの型を指定する必要がないということです。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="6dbb0-107">明示的な型情報を省略するのは、F# が動的型付け言語であるという意味でも、その F# の値の型付けが弱いという意味でもありません。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="6dbb0-108">F# は、静的型付け言語です。つまり、コンパイラはコンパイル時に各コンストラクトに対して正確な型を推測します。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="6dbb0-109">コンパイラが各コンストラクトの型を推測するのに十分な情報がない場合は、通常、コード内のどこかに明示的な型の注釈を追加することにより、追加の型情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>

## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="6dbb0-110">パラメーターと戻り値の型の推定</span><span class="sxs-lookup"><span data-stu-id="6dbb0-110">Inference of Parameter and Return Types</span></span>

<span data-ttu-id="6dbb0-111">パラメーター リストでは、各パラメーターの型を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="6dbb0-112">それでも、F# は静的型付け言語であるため、すべての値と式にはコンパイル時に明確な型が指定されます。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="6dbb0-113">明示的に指定しない型については、コンパイラがコンテキストに基づいて型を推定します。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="6dbb0-114">型が指定されていない場合は、ジェネリックであると推定されます。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="6dbb0-115">コード内で、ある値が一貫性のある方法で使用されていない場合 (ある値のすべての使用箇所で条件にかなう単一の推定型がない場合など)、コンパイラによりエラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="6dbb0-116">関数の戻り値の型は、関数に含まれている最後の式の型によって決まります。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="6dbb0-117">たとえば、次のコードでは、リテラル `100` の型が `int` であるため、パラメーターの型 `a` と `b`、および戻り値の型はすべて `int` と推定されます。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="6dbb0-118">リテラルを変更することで、型の推定に影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="6dbb0-119">サフィックス `u` を追加して `100` を `uint32` にする場合、`a`、`b`、戻り値の型は `uint32` と推定されます。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="6dbb0-120">特定の型のみを処理する関数やメソッドなど、型に制限がある他の構造体を使用して、型の推定に影響を与えることもできます。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="6dbb0-121">また、次の例に示すように、関数やメソッドのパラメーターまたは式の変数に明示的な型の注釈を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="6dbb0-122">異なる制約の間で競合が発生すると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="6dbb0-123">また、すべてのパラメーターの後に型の注釈を指定して、関数の戻り値を明示的に指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="6dbb0-124">パラメーターで型の注釈が役立つ一般的なケースは、パラメーターがオブジェクト型で、メンバーを使用する場合です。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a><span data-ttu-id="6dbb0-125">自動ジェネリック化</span><span class="sxs-lookup"><span data-stu-id="6dbb0-125">Automatic Generalization</span></span>

<span data-ttu-id="6dbb0-126">関数コードがパラメーターの型に依存していない場合、コンパイラはパラメーターをジェネリックと見なします。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="6dbb0-127">これは "*自動ジェネリック化*" と呼ばれ、複雑さを増大させることなくジェネリック コードを記述するための強力な機能となります。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="6dbb0-128">たとえば、次の関数は、任意の型の 2 つのパラメーターを結合してタプルにします。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="6dbb0-129">型は、次のように推定されます。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="6dbb0-130">追加情報</span><span class="sxs-lookup"><span data-stu-id="6dbb0-130">Additional Information</span></span>

<span data-ttu-id="6dbb0-131">型の推定については、F# 言語仕様でさらに詳しく説明されています。</span><span class="sxs-lookup"><span data-stu-id="6dbb0-131">Type inference is described in more detail in the F# Language Specification.</span></span>

## <a name="see-also"></a><span data-ttu-id="6dbb0-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="6dbb0-132">See also</span></span>

- [<span data-ttu-id="6dbb0-133">自動ジェネリック化</span><span class="sxs-lookup"><span data-stu-id="6dbb0-133">Automatic Generalization</span></span>](./generics/automatic-generalization.md)

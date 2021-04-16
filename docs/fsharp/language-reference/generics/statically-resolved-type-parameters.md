---
title: 静的に解決される型パラメーター
description: 実行時ではなく、コンパイル時に実際の型に置き換えられる、F# の静的に解決される型パラメーターの使い方について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 017c18dd3caaa484ddc653557573f548e3224ca0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425008"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="64e8e-103">静的に解決される型パラメーター</span><span class="sxs-lookup"><span data-stu-id="64e8e-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="64e8e-104">"*静的に解決される型パラメーター*" とは、実行時でなく、コンパイル時に実際の型に置き換えられる型パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="64e8e-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="64e8e-105">これらの前にはキャレット (^) 記号が付きます。</span><span class="sxs-lookup"><span data-stu-id="64e8e-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="64e8e-106">構文</span><span class="sxs-lookup"><span data-stu-id="64e8e-106">Syntax</span></span>

```fsharp
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="64e8e-107">解説</span><span class="sxs-lookup"><span data-stu-id="64e8e-107">Remarks</span></span>

<span data-ttu-id="64e8e-108">F# 言語には、異なる 2 種類の型パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="64e8e-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="64e8e-109">1 つ目の種類は、標準のジェネリック型パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="64e8e-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="64e8e-110">これらは、`'T` や `'U` のようにアポストロフィ (') で示されます。</span><span class="sxs-lookup"><span data-stu-id="64e8e-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="64e8e-111">これらは、他の .NET Framework 言語のジェネリック型パラメーターと同じです。</span><span class="sxs-lookup"><span data-stu-id="64e8e-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="64e8e-112">もう 1 つの種類は、静的に解決される型パラメーターであり、`^T` や `^U` のようにキャレット記号で示されます。</span><span class="sxs-lookup"><span data-stu-id="64e8e-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="64e8e-113">静的に解決される型パラメーターは、主にメンバー制約で使用する場合に役立ちます。これは、型引数を使用するために特定のメンバーが必要であることを指定できる制約です。</span><span class="sxs-lookup"><span data-stu-id="64e8e-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="64e8e-114">この種の制約を、標準のジェネリック型パラメーターを使用して作成する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="64e8e-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="64e8e-115">2 種類の型パラメーターの類似点と相違点の概要を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="64e8e-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="64e8e-116">機能</span><span class="sxs-lookup"><span data-stu-id="64e8e-116">Feature</span></span>|<span data-ttu-id="64e8e-117">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="64e8e-117">Generic</span></span>|<span data-ttu-id="64e8e-118">静的に解決される</span><span class="sxs-lookup"><span data-stu-id="64e8e-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="64e8e-119">構文</span><span class="sxs-lookup"><span data-stu-id="64e8e-119">Syntax</span></span>|<span data-ttu-id="64e8e-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="64e8e-120">`'T`, `'U`</span></span>|<span data-ttu-id="64e8e-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="64e8e-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="64e8e-122">解決時期</span><span class="sxs-lookup"><span data-stu-id="64e8e-122">Resolution time</span></span>|<span data-ttu-id="64e8e-123">実行時</span><span class="sxs-lookup"><span data-stu-id="64e8e-123">Run time</span></span>|<span data-ttu-id="64e8e-124">コンパイル時間</span><span class="sxs-lookup"><span data-stu-id="64e8e-124">Compile time</span></span>|
|<span data-ttu-id="64e8e-125">メンバー制約</span><span class="sxs-lookup"><span data-stu-id="64e8e-125">Member constraints</span></span>|<span data-ttu-id="64e8e-126">メンバー制約では使用できません。</span><span class="sxs-lookup"><span data-stu-id="64e8e-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="64e8e-127">メンバー制約で使用できます。</span><span class="sxs-lookup"><span data-stu-id="64e8e-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="64e8e-128">コード生成</span><span class="sxs-lookup"><span data-stu-id="64e8e-128">Code generation</span></span>|<span data-ttu-id="64e8e-129">標準のジェネリック型パラメーターを持つ型 (またはメソッド) では、単一のジェネリック型またはジェネリック メソッドが生成されます。</span><span class="sxs-lookup"><span data-stu-id="64e8e-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="64e8e-130">各型で必要とされる、型およびメソッドの複数のインスタンス化が生成されます。</span><span class="sxs-lookup"><span data-stu-id="64e8e-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="64e8e-131">型での使用</span><span class="sxs-lookup"><span data-stu-id="64e8e-131">Use with types</span></span>|<span data-ttu-id="64e8e-132">型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="64e8e-132">Can be used on types.</span></span>|<span data-ttu-id="64e8e-133">型では使用できません。</span><span class="sxs-lookup"><span data-stu-id="64e8e-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="64e8e-134">インライン関数での使用</span><span class="sxs-lookup"><span data-stu-id="64e8e-134">Use with inline functions</span></span>|<span data-ttu-id="64e8e-135">いいえ。</span><span class="sxs-lookup"><span data-stu-id="64e8e-135">No.</span></span> <span data-ttu-id="64e8e-136">標準のジェネリック型パラメーターではインライン関数をパラメーター化できません。</span><span class="sxs-lookup"><span data-stu-id="64e8e-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="64e8e-137">はい。</span><span class="sxs-lookup"><span data-stu-id="64e8e-137">Yes.</span></span> <span data-ttu-id="64e8e-138">静的に解決される型パラメーターは、インライン以外の関数またはメソッドでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="64e8e-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="64e8e-139">多数の F# コア ライブラリ関数 (特に演算子) には、静的に解決される型パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="64e8e-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="64e8e-140">これらの関数および演算子はインラインであり、数値の計算に効率的なコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="64e8e-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="64e8e-141">演算子を使用するインライン メソッドおよび関数、または静的に解決される型パラメーターを持つ他の関数を使用するインライン メソッドおよび関数では、それらのメソッドおよび関数自体でも静的に解決される型パラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="64e8e-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="64e8e-142">多くの場合、型推論では、それらのインライン関数が静的に解決される型パラメーターを持つと推論されます。</span><span class="sxs-lookup"><span data-stu-id="64e8e-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="64e8e-143">静的に解決される型パラメーターを持つと推論される演算子の定義を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="64e8e-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="64e8e-144">解決された `(+@)` の型は、`(+)` および `(*)` の使用に基づいており、これらの両方では型推論によって、静的に解決される型パラメーターによるメンバー制約が推論されます。</span><span class="sxs-lookup"><span data-stu-id="64e8e-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="64e8e-145">F# インタープリターに表示される解決された型は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="64e8e-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="64e8e-146">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="64e8e-146">The output is as follows.</span></span>

```console
2
1.500000
```

<span data-ttu-id="64e8e-147">F# 4.1 以降では、静的に解決される型パラメーター シグネチャに具象型名を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="64e8e-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="64e8e-148">以前のバージョンの言語では、実際には型名をコンパイラで推論することはできましたが、実際にシグネチャに指定することはできませんでした。</span><span class="sxs-lookup"><span data-stu-id="64e8e-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="64e8e-149">F# 4.1 以降は、静的に解決される型パラメーター シグネチャに具象型名を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="64e8e-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="64e8e-150">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="64e8e-150">Here's an example:</span></span>

```fsharp
let inline konst x _ = x

type CFunctor() =
    static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
    static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

    // default implementation of replace
    static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

    // call overridden replace if present
    static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
        ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a><span data-ttu-id="64e8e-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="64e8e-151">See also</span></span>

- [<span data-ttu-id="64e8e-152">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="64e8e-152">Generics</span></span>](index.md)
- [<span data-ttu-id="64e8e-153">型推論</span><span class="sxs-lookup"><span data-stu-id="64e8e-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="64e8e-154">自動ジェネリック化</span><span class="sxs-lookup"><span data-stu-id="64e8e-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="64e8e-155">制約</span><span class="sxs-lookup"><span data-stu-id="64e8e-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="64e8e-156">インライン関数</span><span class="sxs-lookup"><span data-stu-id="64e8e-156">Inline Functions</span></span>](../functions/inline-functions.md)

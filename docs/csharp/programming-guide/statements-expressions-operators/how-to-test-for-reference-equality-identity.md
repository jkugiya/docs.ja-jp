---
title: 参照の等価性 (同値) をテストする方法 - C# プログラミング ガイド
description: 参照の等価性 (同値) をテストする方法について説明します。 コード例を参照し、使用可能なその他のリソースを確認します。
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 148f37b37639061e84cefafc5f057e6e7b54563f
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899153"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="0664a-104">参照の等価性 (同値) をテストする方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="0664a-104">How to test for reference equality (Identity) (C# Programming Guide)</span></span>

<span data-ttu-id="0664a-105">独自の型で参照の等価性の比較をサポートするためにカスタム ロジックを実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0664a-105">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="0664a-106">この機能は、すべての型に対して <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 静的メソッドとして用意されています。</span><span class="sxs-lookup"><span data-stu-id="0664a-106">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="0664a-107">次の例に、2 つの変数の *参照の等価性*、つまり、それらの変数がメモリ内で同一のオブジェクトを参照しているかどうかを確認する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0664a-107">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="0664a-108">また、<xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> が値型に対して常に `false` を返す理由と、文字列が等しいかどうかを確認するために <xref:System.Object.ReferenceEquals%2A> を使用しない理由を例に示します。</span><span class="sxs-lookup"><span data-stu-id="0664a-108">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0664a-109">例</span><span class="sxs-lookup"><span data-stu-id="0664a-109">Example</span></span>  

 [!code-csharp[TestingReferenceEquality](snippets/how-to-test-for-reference-equality-identity/Program.cs)]  
  
 <span data-ttu-id="0664a-110">`Equals` 汎用基底クラスの <xref:System.Object?displayProperty=nameWithType> の実装では、参照が等しいかどうかのチェックを実行しますが、このチェックを使用しないようにお勧めします。クラスがメソッドをオーバーライドする場合、予期した結果が得られない可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="0664a-110">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="0664a-111">`==` 演算子と `!=` 演算子についても同様です。</span><span class="sxs-lookup"><span data-stu-id="0664a-111">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="0664a-112">参照型を操作しようとしている場合、`==` および `!=` の既定の動作では参照が等しいかどうかのチェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="0664a-112">When they are operating on reference types, the default behavior of `==` and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="0664a-113">ただし、派生クラスは演算子をオーバーロードすることによって、値が等しいかどうかのチェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="0664a-113">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="0664a-114">エラーが発生する可能性を最小限に抑えるために、2 つのオブジェクトの参照が等しいかどうかを確認する必要がある場合は、常に <xref:System.Object.ReferenceEquals%2A> を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0664a-114">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="0664a-115">同じアセンブリ内の定数文字列は、常に、実行時にインターンされます。</span><span class="sxs-lookup"><span data-stu-id="0664a-115">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="0664a-116">つまり、一意のリテラル文字列ごとにそのインスタンスが 1 つだけ保持されます。</span><span class="sxs-lookup"><span data-stu-id="0664a-116">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="0664a-117">ただし、ランタイムは実行時に作成された文字列がインターンされることを保証しません。また、異なるアセンブリの 2 つの等しい定数文字列がインターンされることも保証しません。</span><span class="sxs-lookup"><span data-stu-id="0664a-117">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0664a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="0664a-118">See also</span></span>

- [<span data-ttu-id="0664a-119">等価比較</span><span class="sxs-lookup"><span data-stu-id="0664a-119">Equality Comparisons</span></span>](./equality-comparisons.md)

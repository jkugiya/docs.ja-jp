---
description: var - C# リファレンス
title: var - C# リファレンス
ms.date: 10/02/2020
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: b3590ebbcff0894b7864cd4a227a6ea068de42a2
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075512"
---
# <a name="var-c-reference"></a><span data-ttu-id="19b88-103">var (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="19b88-103">var (C# reference)</span></span>

<span data-ttu-id="19b88-104">C# 3 以降、メソッド スコープで宣言された変数には暗黙的な "型" `var` を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="19b88-104">Beginning with C# 3, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="19b88-105">暗黙的に型指定されたローカル変数では、型を自分で宣言した場合と同様に厳密に型指定されますが、コンパイラが型を決定します。</span><span class="sxs-lookup"><span data-stu-id="19b88-105">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="19b88-106">次の 2 つの `i` の宣言は機能的に等しくなります。</span><span class="sxs-lookup"><span data-stu-id="19b88-106">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

> [!IMPORTANT]
> <span data-ttu-id="19b88-107">`var` を [null 許容参照型](../builtin-types/nullable-reference-types.md)を有効にして使用すると、式の型で null 値が許容されない場合でも、常に null 値を許容する参照型を表します。</span><span class="sxs-lookup"><span data-stu-id="19b88-107">When `var` is used with [nullable reference types](../builtin-types/nullable-reference-types.md) enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

<span data-ttu-id="19b88-108">`var` キーワードは、コンストラクターの呼び出し式と共に使用するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="19b88-108">A common use of the `var` keyword is with constructor invocation expressions.</span></span> <span data-ttu-id="19b88-109">`var` を使用すると、次の例に示すように、変数宣言およびオブジェクトのインスタンス化において型名を繰り返す必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="19b88-109">The use of `var` allows you to not repeat a type name in a variable declaration and object instantiation, as the following example shows:</span></span>

```csharp
var xs = new List<int>();
```

<span data-ttu-id="19b88-110">C# 9.0 以降では、代替としてターゲット型の [`new` 式](../operators/new-operator.md)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="19b88-110">Beginning with C# 9.0, you can use a target-typed [`new` expression](../operators/new-operator.md) as an alternative:</span></span>

```csharp
List<int> xs = new();
List<int>? ys = new();
```

<span data-ttu-id="19b88-111">パターン マッチングでは、`var` キーワードが [`var` パターン](../operators/patterns.md#var-pattern)で使用されます。</span><span class="sxs-lookup"><span data-stu-id="19b88-111">In pattern matching, the `var` keyword is used in a [`var` pattern](../operators/patterns.md#var-pattern).</span></span>

## <a name="example"></a><span data-ttu-id="19b88-112">例</span><span class="sxs-lookup"><span data-stu-id="19b88-112">Example</span></span>

<span data-ttu-id="19b88-113">次の例は、2 つのクエリ式を示しています。</span><span class="sxs-lookup"><span data-stu-id="19b88-113">The following example shows two query expressions.</span></span> <span data-ttu-id="19b88-114">最初の式では、`var` の使用が許可されますが、必須ではありません。クエリ結果の型を `IEnumerable<string>` として明示的に指定できるためです。</span><span class="sxs-lookup"><span data-stu-id="19b88-114">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="19b88-115">一方、2 つ目の式の `var` では、匿名型のコレクションとしての結果が許され、その型の名前にはコンパイラ自体以外はアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="19b88-115">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="19b88-116">`var` を使うと、結果のために新しいクラスを作成する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="19b88-116">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="19b88-117">例 #2 では、`foreach` 繰り返し変数 `item` も暗黙的に型指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19b88-117">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="19b88-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="19b88-118">See also</span></span>

- [<span data-ttu-id="19b88-119">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="19b88-119">C# reference</span></span>](../index.md)
- [<span data-ttu-id="19b88-120">暗黙的に型指定されるローカル変数</span><span class="sxs-lookup"><span data-stu-id="19b88-120">Implicitly typed local variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="19b88-121">LINQ クエリ操作での型の関係</span><span class="sxs-lookup"><span data-stu-id="19b88-121">Type relationships in LINQ query operations</span></span>](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)

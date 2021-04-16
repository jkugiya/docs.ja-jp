---
title: クラス内の let 束縛
description: クラス定義で 'let' バインドを使用して、F# クラスのプライベート フィールドとプライベート関数を定義する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 1366ab8f1f4f606fe5947a8fc4df10de49346b3e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216533"
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="b21ec-103">クラス内の let 束縛</span><span class="sxs-lookup"><span data-stu-id="b21ec-103">let Bindings in Classes</span></span>

<span data-ttu-id="b21ec-104">クラス定義で `let` バインドを使用して、F# クラスのプライベート フィールドとプライベート関数を定義することができます。</span><span class="sxs-lookup"><span data-stu-id="b21ec-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="b21ec-105">構文</span><span class="sxs-lookup"><span data-stu-id="b21ec-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="b21ec-106">解説</span><span class="sxs-lookup"><span data-stu-id="b21ec-106">Remarks</span></span>

<span data-ttu-id="b21ec-107">前の構文は、クラスの見出しと継承宣言の後、メンバー定義の前に使用します。</span><span class="sxs-lookup"><span data-stu-id="b21ec-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="b21ec-108">構文は、クラスの外部の `let` バインドの場合と似ていますが、クラスで定義されている名前には、クラスに限定されたスコープがあります。</span><span class="sxs-lookup"><span data-stu-id="b21ec-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="b21ec-109">`let` バインドでは、プライベート フィールドまたは関数が作成されます。データまたは関数を公開するには、プロパティまたはメンバー メソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="b21ec-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="b21ec-110">静的でない `let` バインドは、インスタンス `let` バインドと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b21ec-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="b21ec-111">インスタンス `let` バインドは、オブジェクトの作成時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="b21ec-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="b21ec-112">静的 `let` バインドはクラスの静的初期化子の一部であり、型が最初に使用される前に確実に実行されます。</span><span class="sxs-lookup"><span data-stu-id="b21ec-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="b21ec-113">インスタンス `let` バインド内のコードでは、プライマリ コンストラクターのパラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b21ec-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="b21ec-114">属性とアクセシビリティ修飾子は、クラス内の `let` バインドでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="b21ec-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="b21ec-115">次のコード例は、クラス内での何種類かの `let` バインドを示しています。</span><span class="sxs-lookup"><span data-stu-id="b21ec-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="b21ec-116">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b21ec-116">The output is as follows.</span></span>

```console
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="b21ec-117">フィールドを作成する別の方法</span><span class="sxs-lookup"><span data-stu-id="b21ec-117">Alternative Ways to Create Fields</span></span>

<span data-ttu-id="b21ec-118">また、`val` キーワードを使用してプライベート フィールドを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b21ec-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="b21ec-119">`val` キーワードを使用する場合、オブジェクトの作成時にフィールドに値は与えられませんが、代わりに既定値を使用して初期化されます。</span><span class="sxs-lookup"><span data-stu-id="b21ec-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="b21ec-120">詳細については、「[明示的なフィールド: val キーワード](explicit-fields-the-val-keyword.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b21ec-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="b21ec-121">メンバー定義を使用し、キーワード `private` を定義に追加することで、クラスのプライベート フィールドを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="b21ec-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="b21ec-122">これは、コードを書き直さずにメンバーのアクセシビリティを変更する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b21ec-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="b21ec-123">詳しくは、「[アクセス制御](../access-control.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b21ec-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b21ec-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="b21ec-124">See also</span></span>

- <span data-ttu-id="b21ec-125">[[メンバー]](index.md)</span><span class="sxs-lookup"><span data-stu-id="b21ec-125">[Members](index.md)</span></span>
- [<span data-ttu-id="b21ec-126">クラス内の `do` バインド</span><span class="sxs-lookup"><span data-stu-id="b21ec-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)
- [<span data-ttu-id="b21ec-127">`let` バインド</span><span class="sxs-lookup"><span data-stu-id="b21ec-127">`let` Bindings</span></span>](../functions/let-bindings.md)

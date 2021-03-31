---
description: init キーワード - C# リファレンス
title: init キーワード - C# リファレンス
ms.date: 03/03/2021
f1_keywords:
- init
- init_CSharpKeyword
helpviewer_keywords:
- init keyword [C#]
ms.openlocfilehash: 2271b5332c8bfd3223d0c034a44eca4e2ca0ca54
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190437"
---
# <a name="init-c-reference"></a><span data-ttu-id="95e5a-103">init (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="95e5a-103">init (C# Reference)</span></span>

<span data-ttu-id="95e5a-104">C# 9 以降では、`init` キーワードによってプロパティ内またはインデクサー内で "*アクセサー*" メソッドが定義されます。</span><span class="sxs-lookup"><span data-stu-id="95e5a-104">In C# 9 and later, the `init` keyword defines an *accessor* method in a property or indexer.</span></span> <span data-ttu-id="95e5a-105">init のみのセッターでは、オブジェクトの構築時のみ、プロパティまたはインデクサー要素に値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="95e5a-105">An init-only setter assigns a value to the property or the indexer element only during object construction.</span></span> <span data-ttu-id="95e5a-106">使用例を含む詳細については、「[プロパティ](../../programming-guide/classes-and-structs/properties.md)」、「[自動実装プロパティ](../../programming-guide/classes-and-structs/auto-implemented-properties.md)」、および「[インデクサー](../../programming-guide/indexers/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95e5a-106">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="95e5a-107">次の例では、`Seconds` という名前のプロパティの `get` アクセサーと `init` アクセサーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="95e5a-107">The following example defines both a `get` and an `init` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="95e5a-108">また、`_seconds` という名前のプライベート フィールドを使って、プロパティの値を戻しています。</span><span class="sxs-lookup"><span data-stu-id="95e5a-108">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[init#1](snippets/InitExample1.cs)]

<span data-ttu-id="95e5a-109">多くの場合、前の例のように、`init` アクセサーは値を割り当てる 1 つのステートメントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="95e5a-109">Often, the `init` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="95e5a-110">式形式のメンバーとして `init` アクセサーを実装できます。</span><span class="sxs-lookup"><span data-stu-id="95e5a-110">You can implement the `init` accessor as an expression-bodied member.</span></span> <span data-ttu-id="95e5a-111">次の例では、`get` アクセサーと `init` アクセサーの両方を、式形式のメンバーとして実装しています。</span><span class="sxs-lookup"><span data-stu-id="95e5a-111">The following example implements both the `get` and the `init` accessors as expression-bodied members.</span></span>

[!code-csharp[init#3](snippets/InitExample3.cs)]
  
<span data-ttu-id="95e5a-112">プロパティの `get` アクセサーと `init` アクセサーがプライベート バッキング フィールドの値の設定と取得以外の操作を実行しない単純な場合では、自動実装プロパティに対する C# コンパイラのサポートを利用できます。</span><span class="sxs-lookup"><span data-stu-id="95e5a-112">For simple cases in which a property's `get` and `init` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="95e5a-113">次の例では、自動実装プロパティとして `Hours` を実装しています。</span><span class="sxs-lookup"><span data-stu-id="95e5a-113">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[init#2](snippets/InitExample2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="95e5a-114">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="95e5a-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="95e5a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="95e5a-115">See also</span></span>

- [<span data-ttu-id="95e5a-116">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="95e5a-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="95e5a-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="95e5a-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="95e5a-118">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="95e5a-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="95e5a-119">プロパティ</span><span class="sxs-lookup"><span data-stu-id="95e5a-119">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

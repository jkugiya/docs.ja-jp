---
title: 明示的なインターフェイスの実装 - C# プログラミング ガイド
description: C# では、クラスによって、シグネチャが同じメンバーを含むインターフェイスを実装できます。 明示的な実装では、1 つのインターフェイスに固有のクラス メンバーが作成されます。
ms.date: 03/24/2021
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.openlocfilehash: 2ca7e8a10c009b01b43e0c09d25d2dd99cbee2ec
ms.sourcegitcommit: 80f38cb67bd02f51d5722fa13d0ea207e3b14a8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2021
ms.locfileid: "105610864"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="15428-104">明示的なインターフェイスの実装 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="15428-104">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="15428-105">シグネチャが同じメンバーが含まれる 2 つのインターフェイスをある[クラス](../../language-reference/keywords/class.md)が実装する場合、そのクラスでそのメンバーを実装することで、実装としてそのメンバーが両方のインターフェイスで使用されます。</span><span class="sxs-lookup"><span data-stu-id="15428-105">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="15428-106">次の例では、`Paint` のすべての呼び出しで同じメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="15428-106">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="15428-107">この最初のサンプルでは、型が定義されます。</span><span class="sxs-lookup"><span data-stu-id="15428-107">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="15428-108">次のサンプルでは、メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="15428-108">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="15428-109">ただし、両方のインターフェイスに対して同じ実装を呼び出さないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="15428-109">But you might not want the same implementation to be called for both interfaces.</span></span> <span data-ttu-id="15428-110">使用中のインターフェイスに応じて異なる実装を呼び出すには、インターフェイス メンバーを明示的に実装します。</span><span class="sxs-lookup"><span data-stu-id="15428-110">To call a different implementation depending on which interface is in use, you can implement an interface member explicitly.</span></span> <span data-ttu-id="15428-111">明示的なインターフェイスの実装は、指定されたインターフェイスを介してのみ呼び出されるクラス メンバーです。</span><span class="sxs-lookup"><span data-stu-id="15428-111">An explicit interface implementation is a class member that is only called through the specified interface.</span></span> <span data-ttu-id="15428-112">インターフェイスの名前とピリオドを使ってプレフィックスを付けて、クラス メンバーに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="15428-112">Name the class member by prefixing it with the name of the interface and a period.</span></span> <span data-ttu-id="15428-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="15428-113">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="15428-114">クラス メンバー `IControl.Paint` は `IControl` インターフェイス経由でのみ利用できます。`ISurface.Paint` は `ISurface` 経由でのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="15428-114">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="15428-115">いずれのメソッド実装も個別であり、どちらもクラスで直接利用できません。</span><span class="sxs-lookup"><span data-stu-id="15428-115">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="15428-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="15428-116">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="15428-117">2 つのインターフェイスで、それぞれが同じ名前の別のメンバー (プロパティやメソッドなど) を宣言するような場合の解決には、明示的な実装も利用されます。</span><span class="sxs-lookup"><span data-stu-id="15428-117">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="15428-118">両方のインターフェイスを実装するには、コンパイラ エラーを回避するために、クラスはプロパティ `P`、メソッド `P`、または両方に明示的な実装を利用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15428-118">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="15428-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="15428-119">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="15428-120">明示的なインターフェイスの実装には、定義されている型のメンバーとしてアクセスできないため、アクセス修飾子がありません。</span><span class="sxs-lookup"><span data-stu-id="15428-120">An explicit interface implementation doesn't have an access modifier since it isn't accessible as a member of the type it's defined in.</span></span> <span data-ttu-id="15428-121">代わりに、インターフェイスのインスタンスを介して呼び出された場合にのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="15428-121">Instead, it's only accessible when called through an instance of the interface.</span></span> <span data-ttu-id="15428-122">明示的なインターフェイスの実装にアクセス修飾子を指定すると、コンパイラ エラー [CS0106](../../language-reference/compiler-messages/cs0106.md) が発生します。</span><span class="sxs-lookup"><span data-stu-id="15428-122">If you specify an access modifier for an explicit interface implementation, you get compiler error [CS0106](../../language-reference/compiler-messages/cs0106.md).</span></span> <span data-ttu-id="15428-123">詳細については、「[`interface` (C# リファレンス)](../../language-reference/keywords/interface.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15428-123">For more information, see [`interface` (C# Reference)](../../language-reference/keywords/interface.md).</span></span>

<span data-ttu-id="15428-124">[C# 8.0](../../whats-new/csharp-8.md#default-interface-methods) 以降では、インターフェイスで宣言されたメンバーの実装を定義できます。</span><span class="sxs-lookup"><span data-stu-id="15428-124">Beginning with [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), you can define an implementation for members declared in an interface.</span></span> <span data-ttu-id="15428-125">クラスでインターフェイスからメソッド実装が継承される場合、そのメソッドにはインターフェイス型の参照を利用する方法でのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="15428-125">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="15428-126">継承したメンバーは、パブリック インターフェイスの一部として表示されません。</span><span class="sxs-lookup"><span data-stu-id="15428-126">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="15428-127">次のサンプルでは、インターフェイス メソッドの既定の実装が定義されます。</span><span class="sxs-lookup"><span data-stu-id="15428-127">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="15428-128">次のサンプルでは、既定の実装が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="15428-128">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="15428-129">`IControl` インターフェイスを実装するあらゆるクラスによって、既定の `Paint` メソッドをパブリック メソッドか明示的なインターフェイス実装としてオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="15428-129">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="15428-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="15428-130">See also</span></span>

- [<span data-ttu-id="15428-131">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="15428-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="15428-132">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="15428-132">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="15428-133">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="15428-133">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="15428-134">継承</span><span class="sxs-lookup"><span data-stu-id="15428-134">Inheritance</span></span>](../classes-and-structs/inheritance.md)

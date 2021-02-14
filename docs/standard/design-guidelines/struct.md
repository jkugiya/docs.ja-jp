---
description: '詳細情報: 構造体のデザイン'
title: 構造体のデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: a28dd3e452d22e61d95ec521fdbde6539e38ed78
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641903"
---
# <a name="struct-design"></a><span data-ttu-id="20608-103">構造体のデザイン</span><span class="sxs-lookup"><span data-stu-id="20608-103">Struct Design</span></span>

<span data-ttu-id="20608-104">汎用の値型は、ほとんどの場合、構造体と呼ばれます。これは C# のキーワードです。</span><span class="sxs-lookup"><span data-stu-id="20608-104">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="20608-105">このセクションでは、一般的な構造体の設計に関するガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="20608-105">This section provides guidelines for general struct design.</span></span>

 <span data-ttu-id="20608-106">❌ 構造体に対して、パラメーターのないコンストラクターを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="20608-106">❌ DO NOT provide a parameterless constructor for a struct.</span></span>

 <span data-ttu-id="20608-107">このガイドラインに従うことで、配列の各項目にコンストラクターを実行することなく、構造体の配列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="20608-107">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="20608-108">C# では、構造体でパラメーターのないコンストラクターは使用できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="20608-108">Notice that C# does not allow structs to have parameterless constructors.</span></span>

 <span data-ttu-id="20608-109">❌ 変更可能な値型を定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="20608-109">❌ DO NOT define mutable value types.</span></span>

 <span data-ttu-id="20608-110">変更可能な値型にはいくつかの問題があります。</span><span class="sxs-lookup"><span data-stu-id="20608-110">Mutable value types have several problems.</span></span> <span data-ttu-id="20608-111">たとえば、プロパティ ゲッターによって値型が返される場合、呼び出し元はコピーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="20608-111">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="20608-112">コピーは暗黙的に作成されるため、開発者は、元の値ではなくコピーを変更していることに気付かないことがあります。</span><span class="sxs-lookup"><span data-stu-id="20608-112">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="20608-113">また、一部の言語 (特に動的言語) では、ローカル変数であっても逆参照されるときにコピーが作成されるため、変更可能な値型の使用で問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="20608-113">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>

 <span data-ttu-id="20608-114">✔️ すべてのインスタンス データが 0、false、または null (必要に応じて) に設定された状態が有効であるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="20608-114">✔️ DO ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>

 <span data-ttu-id="20608-115">これにより、構造体の配列が作成されるときに、無効なインスタンスが誤って作成されることが防止されます。</span><span class="sxs-lookup"><span data-stu-id="20608-115">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>

 <span data-ttu-id="20608-116">✔️ 値型に <xref:System.IEquatable%601> を実装してください。</span><span class="sxs-lookup"><span data-stu-id="20608-116">✔️ DO implement <xref:System.IEquatable%601> on value types.</span></span>

 <span data-ttu-id="20608-117">値型の <xref:System.Object.Equals%2A?displayProperty=nameWithType> メソッドによってボックス化が発生しますが、リフレクションが使用されるため、既定の実装はあまり効率的ではありません。</span><span class="sxs-lookup"><span data-stu-id="20608-117">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="20608-118"><xref:System.IEquatable%601.Equals%2A> のほうがパフォーマンスがはるかに優れており、ボックス化が発生しないように実装できます。</span><span class="sxs-lookup"><span data-stu-id="20608-118"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>

 <span data-ttu-id="20608-119">❌ <xref:System.ValueType> を明示的に拡張しないでください。</span><span class="sxs-lookup"><span data-stu-id="20608-119">❌ DO NOT explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="20608-120">実際、ほとんどの言語ではこれは禁止されています。</span><span class="sxs-lookup"><span data-stu-id="20608-120">In fact, most languages prevent this.</span></span>

 <span data-ttu-id="20608-121">一般に、構造体は非常に有用ですが、頻繁にボックス化されない小さな単一の変更できない値に対してのみ使用するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="20608-121">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>

 <span data-ttu-id="20608-122">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="20608-122">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="20608-123">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="20608-123">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="20608-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="20608-124">See also</span></span>

- [<span data-ttu-id="20608-125">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="20608-125">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="20608-126">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="20608-126">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="20608-127">クラスまたは構造体の選択</span><span class="sxs-lookup"><span data-stu-id="20608-127">Choosing Between Class and Struct</span></span>](choosing-between-class-and-struct.md)

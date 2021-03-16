---
description: '詳細情報: フィールドのデザイン'
title: フィールドのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 88df60c3050035221dc65429bbd543c71d5d69b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642046"
---
# <a name="field-design"></a><span data-ttu-id="df8d0-103">フィールドのデザイン</span><span class="sxs-lookup"><span data-stu-id="df8d0-103">Field Design</span></span>

<span data-ttu-id="df8d0-104">カプセル化の原則は、オブジェクト指向設計で最も重要な概念の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="df8d0-104">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="df8d0-105">この原則では、オブジェクト内に格納されるデータは、そのオブジェクトに対してのみアクセスできるようにする必要であると述べられています。</span><span class="sxs-lookup"><span data-stu-id="df8d0-105">This principle states that data stored inside an object should be accessible only to that object.</span></span>

 <span data-ttu-id="df8d0-106">この原則を解釈するのに役立つ方法は、型のメンバー以外のコードを中断することなく、型のフィールドに対する変更 (名前または型の変更) を実行できるように型を設計する必要があると言うことです。</span><span class="sxs-lookup"><span data-stu-id="df8d0-106">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="df8d0-107">この解釈は、すべてのフィールドをプライベートにする必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="df8d0-107">This interpretation immediately implies that all fields must be private.</span></span>

 <span data-ttu-id="df8d0-108">本書では、この厳格な制限から定数と静的読み取り専用フィールドを除外しています。理由は、そのようなフィールドは、その定義からいって、変更する必要がないからです。</span><span class="sxs-lookup"><span data-stu-id="df8d0-108">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>

 <span data-ttu-id="df8d0-109">❌ パブリックまたは保護されているインスタンス フィールドを用意しないでください。</span><span class="sxs-lookup"><span data-stu-id="df8d0-109">❌ DO NOT provide instance fields that are public or protected.</span></span>

 <span data-ttu-id="df8d0-110">フィールドをパブリックまたは保護するのではなく、フィールドにアクセスするためのプロパティを指定してください。</span><span class="sxs-lookup"><span data-stu-id="df8d0-110">You should provide properties for accessing fields instead of making them public or protected.</span></span>

 <span data-ttu-id="df8d0-111">✔️ 変更されることがない定数には定数フィールドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="df8d0-111">✔️ DO use constant fields for constants that will never change.</span></span>

 <span data-ttu-id="df8d0-112">コンパイラでは、定数フィールドの値が呼び出し側コードに直接書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="df8d0-112">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="df8d0-113">そのため、定数値は、互換性を損なうリスクなしで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="df8d0-113">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>

 <span data-ttu-id="df8d0-114">✔️ 定義済みのオブジェクト インスタンスには、パブリックで静的な `readonly` フィールドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="df8d0-114">✔️ DO use public static `readonly` fields for predefined object instances.</span></span>

 <span data-ttu-id="df8d0-115">型の定義済みインスタンスがある場合は、型自体のパブリックな読み取り専用の静的フィールドとして宣言してください。</span><span class="sxs-lookup"><span data-stu-id="df8d0-115">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>

 <span data-ttu-id="df8d0-116">❌ `readonly` フィールドに変更可能な型のインスタンスを割り当てないでください。</span><span class="sxs-lookup"><span data-stu-id="df8d0-116">❌ DO NOT assign instances of mutable types to `readonly` fields.</span></span>

 <span data-ttu-id="df8d0-117">変更可能な型は、インスタンス化された後で変更できるインスタンスを持つ型です。</span><span class="sxs-lookup"><span data-stu-id="df8d0-117">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="df8d0-118">たとえば、配列、ほとんどのコレクション、およびストリームは変更可能な型ですが、<xref:System.Int32?displayProperty=nameWithType>、<xref:System.Uri?displayProperty=nameWithType>、および <xref:System.String?displayProperty=nameWithType> はすべて不変です。</span><span class="sxs-lookup"><span data-stu-id="df8d0-118">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="df8d0-119">参照型フィールドの読み取り専用修飾子によって、フィールドに格納されているインスタンスの置換が防止されますが、インスタンスを変更する呼び出し元のメンバーによるフィールドのインスタンス データの変更は防止されません。</span><span class="sxs-lookup"><span data-stu-id="df8d0-119">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>

 <span data-ttu-id="df8d0-120">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="df8d0-120">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="df8d0-121">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="df8d0-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="df8d0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="df8d0-122">See also</span></span>

- [<span data-ttu-id="df8d0-123">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="df8d0-123">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="df8d0-124">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="df8d0-124">Framework Design Guidelines</span></span>](index.md)

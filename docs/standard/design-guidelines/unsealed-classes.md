---
description: '詳細情報: シールされていないクラス'
title: シールされていないクラス
ms.date: 10/22/2008
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 6fe30c3a2ef8df6b983d857b9502805e90ab83dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641825"
---
# <a name="unsealed-classes"></a><span data-ttu-id="92566-103">シールされていないクラス</span><span class="sxs-lookup"><span data-stu-id="92566-103">Unsealed Classes</span></span>

<span data-ttu-id="92566-104">シールされたクラスから継承することはできません。これらは拡張できないようになっています。</span><span class="sxs-lookup"><span data-stu-id="92566-104">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="92566-105">対照的に、継承が可能なクラスは、シールされていないクラスと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="92566-105">In contrast, classes that can be inherited from are called unsealed classes.</span></span>

 <span data-ttu-id="92566-106">✔️ コストをかけずにフレームワークに高い拡張性を提供する優れた方法として、シールされていないクラスを、仮想または保護されたメンバーを追加せずに使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="92566-106">✔️ CONSIDER using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>

 <span data-ttu-id="92566-107">開発者は、シールされていないクラスから継承を行って、カスタム コンストラクターや新しいメソッド、メソッド オーバーロードなどの便利なメンバーを追加したいと思うことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="92566-107">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="92566-108">たとえば、`System.Messaging.MessageQueue` はシールされていないため、ユーザーは特定のキューのパスを既定とするカスタム キューを作成したり、特定のシナリオで API を簡略化するカスタム メソッドを追加したりできます。</span><span class="sxs-lookup"><span data-stu-id="92566-108">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>

 <span data-ttu-id="92566-109">ほとんどのプログラミング言語では、クラスは既定でシールされていません。これは、フレームワークのほとんどのクラスに対する既定の設定としても推奨されます。</span><span class="sxs-lookup"><span data-stu-id="92566-109">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="92566-110">シールされていない型によって実現される拡張性は、フレームワーク ユーザーに高く評価されており、シールされていない型に関連するテスト コストが相対的に低いため、コストをかけずに提供されます。</span><span class="sxs-lookup"><span data-stu-id="92566-110">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>

 <span data-ttu-id="92566-111">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="92566-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="92566-112">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="92566-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="92566-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="92566-113">See also</span></span>

- [<span data-ttu-id="92566-114">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="92566-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="92566-115">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="92566-115">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="92566-116">シール</span><span class="sxs-lookup"><span data-stu-id="92566-116">Sealing</span></span>](sealing.md)

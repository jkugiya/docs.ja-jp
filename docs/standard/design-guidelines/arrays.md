---
description: '詳細情報: 配列'
title: 配列
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: 2d919d5e13a03ed1c5d090339f8f0fd9c1a79190
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642448"
---
# <a name="arrays"></a><span data-ttu-id="20a12-103">配列</span><span class="sxs-lookup"><span data-stu-id="20a12-103">Arrays</span></span>

<span data-ttu-id="20a12-104">✔️ パブリック API では、配列よりコレクションを使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="20a12-104">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="20a12-105">コレクションと配列の選択方法の詳細については、「[コレクション](guidelines-for-collections.md)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="20a12-105">The [Collections](guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="20a12-106">❌ 読み取り専用の配列フィールドは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="20a12-106">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="20a12-107">フィールド自体は読み取り専用であり、変更できませんが、配列内の要素は変更できます。</span><span class="sxs-lookup"><span data-stu-id="20a12-107">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="20a12-108">✔️ 多次元配列ではなくジャグ配列を使用することを検討します。</span><span class="sxs-lookup"><span data-stu-id="20a12-108">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="20a12-109">ジャグ配列は、その要素も配列である配列です。</span><span class="sxs-lookup"><span data-stu-id="20a12-109">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="20a12-110">要素を構成する配列のサイズは異なってもよいため、データ セットによっては (スパース マトリックスなど)、多次元配列より無駄な空間が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="20a12-110">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="20a12-111">さらに、ジャグ配列では CLR によってインデックス操作が最適化されるため、一部のシナリオで実行時のパフォーマンスが向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="20a12-111">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="20a12-112">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="20a12-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="20a12-113">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="20a12-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="20a12-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="20a12-114">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="20a12-115">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="20a12-115">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="20a12-116">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="20a12-116">Usage Guidelines</span></span>](usage-guidelines.md)

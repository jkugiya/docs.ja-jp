---
description: '詳細情報: 使用ガイドライン'
title: 使用上のガイドライン
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: a435fab2adb00f671dfde1619a3c1f8db719d9df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641799"
---
# <a name="usage-guidelines"></a><span data-ttu-id="9e58e-103">使用上のガイドライン</span><span class="sxs-lookup"><span data-stu-id="9e58e-103">Usage guidelines</span></span>

<span data-ttu-id="9e58e-104">このセクションには、パブリックにアクセスできる API で共通型を使用するためのガイドラインが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9e58e-104">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="9e58e-105">組み込みのフレームワーク型 (シリアル化属性など) の直接使用と、一般的な演算子のオーバーロードを扱っています。</span><span class="sxs-lookup"><span data-stu-id="9e58e-105">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="9e58e-106"><xref:System.IDisposable?displayProperty=nameWithType> インターフェイスはこのセクションでは説明されていません。[Dispose パターン](../garbage-collection/implementing-dispose.md) セクションで説明されています。</span><span class="sxs-lookup"><span data-stu-id="9e58e-106">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../garbage-collection/implementing-dispose.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="9e58e-107">その他の共通する組み込みの .NET Framework の型のガイドラインとその他の情報については、次に関するリファレンス トピックを参照してください。<xref:System.DateTime?displayProperty=nameWithType>、<xref:System.DateTimeOffset?displayProperty=nameWithType>、<xref:System.ICloneable?displayProperty=nameWithType>、<xref:System.IComparable%601?displayProperty=nameWithType>、<xref:System.IEquatable%601?displayProperty=nameWithType>、<xref:System.Nullable%601?displayProperty=nameWithType>、<xref:System.Object?displayProperty=nameWithType>、<xref:System.Uri?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="9e58e-107">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9e58e-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9e58e-108">In this section</span></span>

[<span data-ttu-id="9e58e-109">配列</span><span class="sxs-lookup"><span data-stu-id="9e58e-109">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="9e58e-110">属性</span><span class="sxs-lookup"><span data-stu-id="9e58e-110">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="9e58e-111">コレクション</span><span class="sxs-lookup"><span data-stu-id="9e58e-111">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="9e58e-112">シリアル化</span><span class="sxs-lookup"><span data-stu-id="9e58e-112">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="9e58e-113">System.Xml の使用法</span><span class="sxs-lookup"><span data-stu-id="9e58e-113">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="9e58e-114">等値演算子</span><span class="sxs-lookup"><span data-stu-id="9e58e-114">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="9e58e-115">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="9e58e-115">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="9e58e-116">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="9e58e-116">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9e58e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e58e-117">See also</span></span>

- [<span data-ttu-id="9e58e-118">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="9e58e-118">Framework Design Guidelines</span></span>](index.md)

---
description: '詳細情報: System.Xml の使用法'
title: System.Xml の使用法
ms.date: 10/22/2008
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 51886c07f0b68bb329c258daa93e809d94839341
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641851"
---
# <a name="systemxml-usage"></a><span data-ttu-id="c4fb1-103">System.Xml の使用法</span><span class="sxs-lookup"><span data-stu-id="c4fb1-103">System.Xml Usage</span></span>

<span data-ttu-id="c4fb1-104">このセクションでは、<xref:System.Xml?displayProperty=nameWithType> 名前空間に存在するさまざまな型で、XML データを表すために使用できる型の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c4fb1-104">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>

 <span data-ttu-id="c4fb1-105">❌ XML データを表すために <xref:System.Xml.XmlNode> または <xref:System.Xml.XmlDocument> を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c4fb1-105">❌ DO NOT use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="c4fb1-106">代わりに、<xref:System.Xml.XPath.IXPathNavigable>、<xref:System.Xml.XmlReader>、または <xref:System.Xml.XmlWriter> のインスタンス、または <xref:System.Xml.Linq.XNode> のサブタイプを優先的に使用してください。</span><span class="sxs-lookup"><span data-stu-id="c4fb1-106">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="c4fb1-107">`XmlNode` と `XmlDocument` は、パブリック API に公開するように設計されていません。</span><span class="sxs-lookup"><span data-stu-id="c4fb1-107">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>

 <span data-ttu-id="c4fb1-108">✔️ XML を受け入れるか返すメンバーの入力または出力として、`XmlReader`、`IXPathNavigable`、または `XNode` のサブタイプを使用してください。</span><span class="sxs-lookup"><span data-stu-id="c4fb1-108">✔️ DO use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>

 <span data-ttu-id="c4fb1-109">これらの抽象化を、`XmlDocument`、`XmlNode`、または <xref:System.Xml.XPath.XPathDocument> の代わりに使用してください。これにより、メモリ内 XML ドキュメントの特定の実装からメソッドが切り離され、`XNode`、`XmlReader`、または <xref:System.Xml.XPath.XPathNavigator> を公開する仮想 XML データ ソースとの連携が可能になります。</span><span class="sxs-lookup"><span data-stu-id="c4fb1-109">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>

 <span data-ttu-id="c4fb1-110">❌ 基になるオブジェクト モデルまたはデータ ソースの XML ビューを表す型を作成する場合に、`XmlDocument` をサブクラス化しないでください。</span><span class="sxs-lookup"><span data-stu-id="c4fb1-110">❌ DO NOT subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>

 <span data-ttu-id="c4fb1-111">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="c4fb1-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c4fb1-112">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="c4fb1-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c4fb1-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4fb1-113">See also</span></span>

- [<span data-ttu-id="c4fb1-114">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c4fb1-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="c4fb1-115">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="c4fb1-115">Usage Guidelines</span></span>](usage-guidelines.md)

---
title: アセンブリと DLL の名前
description: アセンブリとダイナミックリンク ライブラリ (DLL) の名前付けのガイドラインについて説明します。 アセンブリは 1 つ以上のファイルにまたがることができますが、通常は 1 対 1 で DLL にマップされます。
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: 95a90ff66ffc9f2a5a3202d6877b1cc19149ff35
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706529"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="90b75-104">アセンブリと DLL の名前</span><span class="sxs-lookup"><span data-stu-id="90b75-104">Names of Assemblies and DLLs</span></span>

<span data-ttu-id="90b75-105">アセンブリは、マネージド コード プログラムのデプロイと ID の単位です。</span><span class="sxs-lookup"><span data-stu-id="90b75-105">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="90b75-106">アセンブリは 1 つ以上のファイルにまたがることができますが、通常、アセンブリは 1 対 1 で DLL にマップされます。</span><span class="sxs-lookup"><span data-stu-id="90b75-106">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="90b75-107">したがって、このセクションでは DLL の名前付け規則についてのみ説明し、その後アセンブリの名前付け規則にマップできます。</span><span class="sxs-lookup"><span data-stu-id="90b75-107">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>

 <span data-ttu-id="90b75-108">✔️ アセンブリ DLL には、System.Data など、機能の大きなチャンクを示唆する名前を選択してください。</span><span class="sxs-lookup"><span data-stu-id="90b75-108">✔️ DO choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>

 <span data-ttu-id="90b75-109">アセンブリと DLL の名前は、名前空間名に対応している必要はありませんが、アセンブリに名前を付けるときは、名前空間名に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="90b75-109">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="90b75-110">経験則として、アセンブリに含まれる名前空間の共通のプレフィックスに基づいて DLL の名前を指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="90b75-110">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="90b75-111">たとえば、`MyCompany.MyTechnology.FirstFeature` と `MyCompany.MyTechnology.SecondFeature` の 2 つの名前空間を持つアセンブリを `MyCompany.MyTechnology.dll` と呼ぶことができます。</span><span class="sxs-lookup"><span data-stu-id="90b75-111">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>

 <span data-ttu-id="90b75-112">✔️ DLL には、次のパターンに従って名前を付けることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="90b75-112">✔️ CONSIDER naming DLLs according to the following pattern:</span></span>

 `<Company>.<Component>.dll`

 <span data-ttu-id="90b75-113">`<Component>` には 1 つ以上のドット区切り句が含まれています。</span><span class="sxs-lookup"><span data-stu-id="90b75-113">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="90b75-114">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="90b75-114">For example:</span></span>

 <span data-ttu-id="90b75-115">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="90b75-115">`Litware.Controls.dll`.</span></span>

 <span data-ttu-id="90b75-116">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="90b75-116">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="90b75-117">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="90b75-117">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="90b75-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="90b75-118">See also</span></span>

- [<span data-ttu-id="90b75-119">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="90b75-119">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="90b75-120">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="90b75-120">Naming Guidelines</span></span>](naming-guidelines.md)

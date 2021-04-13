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
# <a name="names-of-assemblies-and-dlls"></a>アセンブリと DLL の名前

アセンブリは、マネージド コード プログラムのデプロイと ID の単位です。 アセンブリは 1 つ以上のファイルにまたがることができますが、通常、アセンブリは 1 対 1 で DLL にマップされます。 したがって、このセクションでは DLL の名前付け規則についてのみ説明し、その後アセンブリの名前付け規則にマップできます。

 ✔️ アセンブリ DLL には、System.Data など、機能の大きなチャンクを示唆する名前を選択してください。

 アセンブリと DLL の名前は、名前空間名に対応している必要はありませんが、アセンブリに名前を付けるときは、名前空間名に従うことをお勧めします。 経験則として、アセンブリに含まれる名前空間の共通のプレフィックスに基づいて DLL の名前を指定することをお勧めします。 たとえば、`MyCompany.MyTechnology.FirstFeature` と `MyCompany.MyTechnology.SecondFeature` の 2 つの名前空間を持つアセンブリを `MyCompany.MyTechnology.dll` と呼ぶことができます。

 ✔️ DLL には、次のパターンに従って名前を付けることを検討してください。

 `<Company>.<Component>.dll`

 `<Component>` には 1 つ以上のドット区切り句が含まれています。 次に例を示します。

 `Litware.Controls.dll`.

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [名前付けのガイドライン](naming-guidelines.md)

---
title: フレームワーク デザインのガイドライン
description: API の一貫性と使いやすさを実現するために、.NET を拡張および操作するライブラリをデザインするためのフレームワーク デザインのガイドラインをご覧ください。
titleSuffix: ''
ms.date: 10/22/2008
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 03fa44c1fed219b50cf1a8d22b2c9f79947f4976
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706659"
---
# <a name="framework-design-guidelines"></a>フレームワーク デザインのガイドライン

このセクションでは、.NET Framework を拡張および操作するライブラリをデザインするためのガイドラインを示します。 目標は、開発に使用されるプログラミング言語に依存しない統合プログラミング モデルを提供することにより、ライブラリ デザイナーが API の一貫性と使いやすさを確保できるようにすることです。 .NET Framework を拡張するクラスやコンポーネントを開発する場合は、これらのデザイン ガイドラインに従うことをお勧めします。 一貫性のないライブラリ デザインは、開発者の生産性に悪影響を及ぼし、採用を妨げます。  
  
 ガイドラインは、`Do`、`Consider`、`Avoid`、`Do not` という言葉から始まる単純な推奨事項として編成されています。 これらのガイドラインは、クラス ライブラリ デザイナーがさまざまなソリューション間のトレードオフを理解できるようにすることを目的としています。 優れたライブラリ デザインでは、これらのデザイン ガイドラインに違反することが必要になる場合があります。 このようなケースはまれである必要があり、その決定について明確で説得力のある理由があることが重要です。  
  
 これらのガイドラインは、Krzysztof Cwalina 氏と Brad abrams 氏による『*Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*』(フレームワーク デザインのガイドライン: 再利用可能な .NET ライブラリのための表記規則、慣用句、パターン、第 2 版)からの抜粋です。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [名前付けのガイドライン](naming-guidelines.md)  
 クラス ライブラリ内のアセンブリ、名前空間、型、メンバーの名前付けに関するガイドラインを提供します。  
  
 [型デザインのガイドライン](type.md)  
 静的および抽象クラス、インターフェイス、列挙型、構造体、およびその他の型を使用するためのガイドラインを提供します。  
  
 [メンバーのデザインのガイドライン](member.md)  
 プロパティ、メソッド、コンストラクター、フィールド、イベント、演算子、パラメーターのデザインと使用に関するガイドラインを提供します。  
  
 [機能拡張のデザイン](designing-for-extensibility.md)  
 サブクラス化、イベントの使用、仮想メンバー、コールバックなどの拡張機能のメカニズムについて説明し、フレームワークの要件に最も適したメカニズムを選択する方法について説明します。  
  
 [例外のデザインのガイドライン](exceptions.md)  
 例外をデザイン、スロー、キャッチするためのデザイン ガイドラインについて説明します。  
  
 [使用方法のガイドライン](usage-guidelines.md)  
 配列、属性、コレクションなどの一般的な型の使用、シリアル化のサポート、および等値演算子のオーバーロードに関するガイドラインについて説明します。  
  
 [共通デザイン パターン](common-design-patterns.md)  
 依存関係プロパティの選択と実装に関するガイドラインを提供します。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [概要](../../framework/get-started/overview.md)
- [開発ガイド](../../framework/development-guide.md)

---
title: メンバーのデザインのガイドライン
description: .NET のメンバー デザインのガイドラインについて説明します。 メンバーには、メソッド、プロパティ、イベント、コンストラクター、フィールドが含まれます。
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: 5070f45beccd89d6f051f1b1d8345390e915d471
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706594"
---
# <a name="member-design-guidelines"></a>メンバーのデザインのガイドライン

メソッド、プロパティ、イベント、コンストラクター、フィールドは、総称してメンバーと呼ばれます。 メンバーは最終的に、フレームワークのエンド ユーザーにフレームワーク機能を公開する手段になります。  
  
 メンバーは、仮想または非仮想、具象または抽象、静的またはインスタンスにすることができ、複数の異なるアクセシビリティ スコープを持つことができます。 このすべてのバリエーションにより、非常に優れた表現力が提供されますが、同時に、フレームワーク デザイナーの一部に注意する必要があります。  
  
 この章では、任意の型のメンバーを設計する際に従う必要がある基本的なガイドラインについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [メンバーのオーバーロード](member-overloading.md)  
 [プロパティのデザイン](property.md)  
 [コンストラクターのデザイン](constructor.md)  
 [イベントのデザイン](event.md)  
 [フィールドのデザイン](field.md)  
 [拡張メソッド](extension-methods.md)  
 [演算子のオーバーロード](operator-overloads.md)  
 [パラメーターのデザイン](parameter-design.md)  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)

---
description: アクセシビリティ レベル - C# リファレンス
title: アクセシビリティ レベル - C# リファレンス
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 509902e9998af421c0afd31070b1be36d64df0f8
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604594"
---
# <a name="accessibility-levels-c-reference"></a>アクセシビリティ レベル (C# リファレンス)

以下に示したのは、メンバーに適用されるアクセシビリティ レベルの宣言です。`public`、`protected`、`internal`、`private` の各アクセス修飾子を使用して指定します。  
  
|アクセシビリティの宣言|説明|  
|----------------------------|-------------|  
|[`public`](public.md)|アクセスは無制限です。|  
|[`protected`](protected.md)|コンテナーであるクラスまたはそこから派生した型にアクセスが限定されます。|  
|[`internal`](internal.md)|アクセスは現在のアセンブリに限定されます。|  
|[`protected internal`](protected-internal.md)|現在のアセンブリ、またはコンテナーであるクラスから派生した型にアクセスが限定されます。|  
|[`private`](private.md)|コンテナーである型にアクセスが限定されます。|  
|[`private protected`](private-protected.md)|現在のアセンブリ内の、コンテナーであるクラス、またはコンテナーであるクラスから派生した型にアクセスが制限されます。 C# 7.2 以降で使用可能です。 |  
  
 `protected internal` または `private protected` の組み合わせを使う場合を除き、1 つのメンバーまたは 1 つの型に指定できるアクセス修飾子は 1 つだけです。  
  
 アクセス修飾子を名前空間に適用することはできません。 名前空間には、アクセス制限がありません。  
  
 メンバーが宣言されているコンテキストによっては、決まったアクセシビリティしか宣言できない場合があります。 メンバーの宣言にアクセス修飾子が指定されていない場合は、既定のアクセシビリティが使用されます。  
  
 トップレベルの型 (他の型に対して入れ子にされていない型) に指定できるアクセシビリティは `internal` と `public` だけです。 既定では、そのような型に `internal` のアクセシビリティが適用されます。  
  
 入れ子にされた型 (他の型のメンバーになっている型) には、次の表に示したアクセシビリティを宣言することができます。  
  
|コンテナー|メンバーの既定のアクセシビリティ|メンバーに対して宣言できるアクセシビリティ|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|なし|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`\*<br /><br /> `protected internal` <br /><br />`private protected`|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  

\* `private` アクセシビリティを持つ `interface` メンバーには、既定の実装が必要です。

入れ子にされた型のアクセシビリティは、その型の[アクセシビリティ ドメイン](./accessibility-domain.md)によって決まります。このアクセシビリティ ドメインは、そのメンバーに対して宣言されているアクセシビリティと、そのメンバーの直接のコンテナーである型のアクセシビリティ ドメインの両方によって決定されます。 ただし、入れ子にされた型のアクセシビリティ ドメインが、その型を含んでいる型のアクセシビリティ ドメインを上回ることはできません。  
  
## <a name="c-language-specification"></a>C# 言語仕様  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](./index.md)
- [アクセス修飾子](./access-modifiers.md)
- [アクセシビリティ ドメイン](./accessibility-domain.md)
- [アクセシビリティ レベルの使用に関する制限事項](./restrictions-on-using-accessibility-levels.md)
- [アクセス修飾子](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
- [internal](./internal.md)

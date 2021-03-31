---
description: init キーワード - C# リファレンス
title: init キーワード - C# リファレンス
ms.date: 03/03/2021
f1_keywords:
- init
- init_CSharpKeyword
helpviewer_keywords:
- init keyword [C#]
ms.openlocfilehash: 2271b5332c8bfd3223d0c034a44eca4e2ca0ca54
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190437"
---
# <a name="init-c-reference"></a>init (C# リファレンス)

C# 9 以降では、`init` キーワードによってプロパティ内またはインデクサー内で "*アクセサー*" メソッドが定義されます。 init のみのセッターでは、オブジェクトの構築時のみ、プロパティまたはインデクサー要素に値が割り当てられます。 使用例を含む詳細については、「[プロパティ](../../programming-guide/classes-and-structs/properties.md)」、「[自動実装プロパティ](../../programming-guide/classes-and-structs/auto-implemented-properties.md)」、および「[インデクサー](../../programming-guide/indexers/index.md)」を参照してください。

次の例では、`Seconds` という名前のプロパティの `get` アクセサーと `init` アクセサーを定義しています。 また、`_seconds` という名前のプライベート フィールドを使って、プロパティの値を戻しています。

[!code-csharp[init#1](snippets/InitExample1.cs)]

多くの場合、前の例のように、`init` アクセサーは値を割り当てる 1 つのステートメントで構成されます。 式形式のメンバーとして `init` アクセサーを実装できます。 次の例では、`get` アクセサーと `init` アクセサーの両方を、式形式のメンバーとして実装しています。

[!code-csharp[init#3](snippets/InitExample3.cs)]
  
プロパティの `get` アクセサーと `init` アクセサーがプライベート バッキング フィールドの値の設定と取得以外の操作を実行しない単純な場合では、自動実装プロパティに対する C# コンパイラのサポートを利用できます。 次の例では、自動実装プロパティとして `Hours` を実装しています。

[!code-csharp[init#2](snippets/InitExample2.cs)]
  
## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [プロパティ](../../programming-guide/classes-and-structs/properties.md)

---
title: 自動実装するプロパティ - C# プログラミング ガイド
description: C# の自動実装プロパティの場合、プロパティの get アクセサーと set アクセサーでのみアクセスできるプライベートの匿名バッキング フィールドがこのコンパイラによって作成されます。
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: ef3e2d6dd5851801ea06d65b87c2274d8e44b4f1
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190282"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>自動実装するプロパティ (C# プログラミング ガイド)

C# 3.0 以降では、自動実装プロパティを使用することで、プロパティ アクセサーに追加のロジックが必要ない場合は、プロパティをより簡潔に宣言できます。 これにより、クライアント コードでオブジェクトを作成することも可能になります。 次の例に示すようにプロパティを宣言する場合、コンパイラによって、プロパティの `get` および `set` アクセサーを介してのみアクセスできる、プライベートの匿名バッキング フィールドが作成されます。 C# 9 以降では、`init` アクセサーを自動実装プロパティとして宣言することもできます。
  
## <a name="example"></a>例

次の例に、自動実装プロパティを持つ簡単なクラスを示します。  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

インターフェイスで自動実装プロパティを宣言することはできません。 自動実装プロパティでは、プライベートのインスタンス バッキング フィールドが宣言されます。インターフェイスでは、インスタンス フィールドを宣言できません。 本文を定義せずにインターフェイスでプロパティを宣言すると、アクセサーを利用してプロパティが宣言されますが、そのアクセサーは、そのインターフェイスを実装する型ごとに実装する必要があります。

C# 6 以降では、フィールドと同様に自動実装プロパティを初期化することができます。  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

前の例に示したクラスは、変更可能です。 クライアント コードでは、作成後、オブジェクト内の値を変更できます。 データだけでなく、重要な動作 (メソッド) も含まれる複雑なクラスでは、多くの場合、パブリック プロパティが必要です。 ただし、値のセット (データ) をカプセル化するだけで動作がほとんどまたはまったくない小さなクラスまたは構造体の場合は、次のいずれかのオプションを使用して、オブジェクトを変更不可にする必要があります。

* `get` アクセサーのみを宣言します (コンストラクター以外のすべての場所で変更できません)。
* `get`アクセサーと `init` アクセサーを宣言します (オブジェクトの構築時を除き、すべての場所で変更できません)。
* `set` アクセサーを[プライベート](../../language-reference/keywords/private.md)として宣言します (コンシューマーには変更できません)。

詳細については、「[自動実装するプロパティを使用して簡易クラスを実装する方法](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [プロパティ](./properties.md)
- [修飾子](../../language-reference/keywords/index.md)

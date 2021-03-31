---
title: プロパティ - C# プログラミング ガイド
description: C# のプロパティは、プライベート フィールドの値の読み取り、書き込み、または計算を行うアクセサー メソッドを使用した、パブリック データのメンバーとしてのメンバーです。
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: 6079fc5d2611ed1111d39d3f39e4c91817db528f
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103189879"
---
# <a name="properties-c-programming-guide"></a>プロパティ (C# プログラミング ガイド)

プロパティは、プライベート フィールドの値の読み取り、書き込み、または計算を行う、柔軟な機構が用意されたメンバーです。 プロパティは、パブリック データのメンバーと同様に使用できますが、実際は *アクセサー* という特殊なメソッドです。 メソッドの安全性と柔軟性を高めながら、簡単にデータにアクセスできます。  

## <a name="properties-overview"></a>プロパティの概要  
  
- プロパティを使えば、実装や検査コードを隠したままで、値の取得と設定についてパブリックな方法をクラスが公開できます。  
  
- [get](../../language-reference/keywords/get.md) プロパティ アクセサーはプロパティ値を取得するために使用し、[set](../../language-reference/keywords/set.md) プロパティ アクセサーは新しい値を割り当てるために使用します。 C# 9 以降では、オブジェクトの構築時にのみ、[init](../../language-reference/keywords/init.md) プロパティ アクセサーを使用して新しい値が割り当てられます。 これらのアクセサーには異なるアクセス レベルを指定できます。 詳細については、「[アクセサーのアクセシビリティの制限](./restricting-accessor-accessibility.md)」を参照してください。  
  
- `set` または `init` アクセサーで割り当てる値は [value](../../language-reference/keywords/value.md) キーワードを使用して定義します。  
- プロパティの種類には、*読み取り/書き込み* (`get` アクセサーと `set` アクセサーの両方を備える)、*読み取り専用* (`get` アクセサーのみで `set` アクセサーはない)、*書き込み専用* (`set` アクセサーのみで `get` アクセサーはない) があります。 書き込み専用のプロパティの使用頻度は低く、ほとんどの場合、機密データへのアクセスを制限するために使用されます。

- カスタムのアクセサー コードを必要としない単純なプロパティは、式本体の定義として、または[自動実装プロパティ](./auto-implemented-properties.md)として実装できます。

## <a name="properties-with-backing-fields"></a>バッキング フィールドを持つプロパティ

プロパティを実装する基本的な手法の 1 つとして、プロパティ値の設定と取得にプライベート バッキング フィールドを使用する方法があります。 この方法では、`get` アクセサーはプライベート フィールドの値を返します。`set` アクセサーはプライベート フィールドに値を割り当てる前にデータ検証を実行できます。 また、どちらのアクセサーも、データの変換や計算を行ってから、データを格納したり返したりすることができます。

このパターンを説明する例を下に示します。 この例では、`TimePeriod` クラスは時間間隔を表しています。 クラスの内部では、`_seconds` という名前のプライベート フィールドに時間間隔が秒単位で格納されます。 `Hours` という読み取り/書き込みプロパティでは、ユーザーが時間間隔を時間単位で指定できます。 `get` アクセサーと `set` アクセサーの両方で、必要に応じて時間と秒の変換が実行されます。 また、`set` アクセサーは、データを検証し、時間数が無効である場合に <xref:System.ArgumentOutOfRangeException> をスローします。

 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>式本体の定義  

 プロパティ アクセサーは、通常、式の結果を割り当てるか返すだけの 1 行のステートメントで構成されます。 プロパティは、本体が式形式のメンバーとして実装できます。 式本体の定義は、`=>` 記号の後に、プロパティに割り当てるかプロパティから取得するための式を続けて構成します。

 C# 6 以降では、読み取り専用プロパティに `get` アクセサーを式形式のメンバーとして実装できます。 この場合、`get` アクセサー キーワードと `return` キーワードはどちらも使用しません。 次の例では、読み取り専用 `Name` プロパティを式形式のメンバーとして実装しています。

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 C# 7.0 以降では、`get` アクセサーと `set` アクセサーのどちらも、式形式のメンバーとして実装できます。 この場合、`get` キーワードと `set` キーワードを使用する必要があります。 両方のアクセサーに式本体の定義を使用する例を次に示します。 `get` アクセサーで `return` キーワードが使用されていない点に注意してください。

  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>自動実装プロパティ

ロジックを追加しなくても、プロパティの `get` アクセサーと `set` アクセサーはバッキング フィールドに値を割り当てたりバッキング フィールドから取得したりすることができます。 この自動実装プロパティを使用すると、C# コンパイラによってバッキング フィールドが透過的に提供されるため、コードを簡略化できます。

プロパティに `get` と `set` (または `get` と `init`) の両方のアクセサーがある場合は、どちらも自動実装する必要があります。 自動実装プロパティを定義するには、実装を省略して `get` キーワードと `set` キーワードを使用します。 次の例は前の例と似ていますが、`Name` と `Price` が自動実装プロパティである点が異なります。 この例では、パラメーター化されたコンストラクターも削除されているため、`SaleItem` オブジェクトがパラメーターなしのコンストラクターの呼び出しと[オブジェクト初期化子](object-and-collection-initializers.md)を使用して初期化されています。

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>関連項目  
  
- [プロパティの使用](./using-properties.md)  
  
- [インターフェイスのプロパティ](./interface-properties.md)  
  
- [プロパティとインデクサーの比較](../indexers/comparison-between-properties-and-indexers.md)  
  
- [アクセサーのアクセシビリティの制限](./restricting-accessor-accessibility.md)  
  
- [自動実装プロパティ](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  

詳細については、「[C# 言語の仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の[プロパティ](~/_csharplang/spec/classes.md#properties)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [プロパティの使用](./using-properties.md)
- [インデクサー](../indexers/index.md)
- [get キーワード](../../language-reference/keywords/get.md)
- [set キーワード](../../language-reference/keywords/set.md)

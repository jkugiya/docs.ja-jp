---
description: '詳細情報: 属性を適用する'
title: 属性の適用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET], attributes
- attributes [.NET], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 18825d3b4d6fc20b23755f58f355c783c0734041
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732164"
---
# <a name="apply-attributes"></a>属性を適用する

コードの要素に属性を適用するには、次のプロセスを使用します。

1. 新しい属性を定義するか、既存の .NET 属性を使用します。

2. 属性をコード要素の直前に記述することで、その要素に属性を適用します。

     各言語には独自の属性構文があります。 C++ および C# では、属性が角かっこで囲まれ、要素とは空白で区切られます。属性と要素の間には改行を入れることもできます。 Visual Basic では、属性が山かっこで囲まれ、同じ論理行に記述されている必要があります。改行が必要な場合は、行連結文字を使用できます。

3. 属性に、位置指定パラメーターと名前付きパラメーターを指定します。

     "*位置指定*" パラメーターは必須で、名前付きパラメーターの前に指定する必要があり、1 つの属性のコンストラクターのパラメーターに対応します。 "*名前付き*" パラメーターは省略可能で、属性の読み取り/書き込みプロパティに対応します。 C++ と C# では、オプションのパラメーターごとに `name=value` を指定します。`name` はプロパティの名前です。 Visual Basic では、`name:=value` を指定します。

 コードをコンパイルすると属性がメタデータに格納され、ランタイム リフレクション サービスを通じて共通言語ランタイム、すべてのカスタム ツールやアプリケーションで使用できるようになります。

 規則では、属性の名前の最後は "Attribute" にします。 ただし、Visual Basic や C# など、ランタイムを対象とする言語では、属性をフルネームで指定する必要はありません。 たとえば、<xref:System.ObsoleteAttribute?displayProperty=nameWithType> を初期化する場合は、**Obsolete** と指定するだけで参照できます。

## <a name="apply-an-attribute-to-a-method"></a>メソッドに属性を適用する

 次のコードからは、コードに非推奨を指定する **System.ObsoleteAttribute** の使用方法を確認できます。 文字列 `"Will be removed in next version"` が属性に渡されます。 属性が記述されているコードが呼び出された時点で、渡された文字列を示すコンパイラの警告が表示されます。

 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]

## <a name="apply-attributes-at-the-assembly-level"></a>アセンブリ レベルで属性を適用する

 アセンブリ レベルで属性を適用する場合は、キーワード `assembly` (Visual Basic では `Assembly`) を使用します。 **AssemblyTitleAttribute** をアセンブリ レベルで適用するコードを次に示します。

 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]

 この属性が適用されると、ファイルのメタデータ部分のアセンブリ マニフェストの中に、文字列 `"My Assembly"` が挿入されます。 この属性を表示するには、[MSIL 逆アセンブラー (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) を使用するか、または属性を取得するためのプログラムを作成します。

## <a name="see-also"></a>参照

- [属性](index.md)
- [属性に格納されている情報の取得](retrieving-information-stored-in-attributes.md)
- [概念](/cpp/windows/attributed-programming-concepts)
- [属性 (C#)](../../csharp/programming-guide/concepts/attributes/index.md)
- [属性の概要 (Visual Basic)](../../visual-basic/programming-guide/concepts/attributes/index.md)

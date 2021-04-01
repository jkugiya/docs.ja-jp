---
description: '詳細情報: .NET でのその他の文字列の解析'
title: .NET でのその他の文字列の解析
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
ms.openlocfilehash: 10d8d9686c451334929471d06e4e3136fca80c68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642722"
---
# <a name="parsing-other-strings-in-net"></a>.NET でのその他の文字列の解析

数値および <xref:System.DateTime> 文字列だけでなく、<xref:System.Char>、<xref:System.Boolean>、<xref:System.Enum> 型を表す文字列をデータ型に解析することもできます。  
  
## <a name="char"></a>Char  

 **Char** データ型に関連付けられている静的解析メソッドは、1 つの文字を含む文字列をUnicode 値に変換するのに便利です。 次のコードの例では、文字列を Unicode 文字に解析します。  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>ブール値  

 **Boolean** データ型には、**Parse** メソッドが含まれ、Boolean 値を示す文字列を実際の **Boolean** 型に変換するために使用できます。 このメソッドは大文字と小文字を区別しません。また、"True" または "False" を含む文字列を正常に解析することができます。 **Boolean** 型に関連付けられる **Parse** メソッドは、空白で囲まれた文字列を解析することもできます。 その他の文字列が渡された場合、<xref:System.FormatException> がスローされます。  
  
 次のコードの例では、**Parse** メソッドを使用して、文字列を Boolean 値に変換します。  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>列挙  

 静的 **Parse** メソッドを使用して、列挙型を文字列の値に初期化できます。 このメソッドでは、解析している列挙型、解析する文字列、および解析が大文字小文字を区別するかどうかを示す省略可能な Boolean フラグを受け入れます。 解析している文字列は、コンマで区切られた複数の値を含めることができます。これは、1 つ以上の空の領域 (空白とも呼ばれます) が前後にある場合があります。 文字列に複数の値がある場合、返されたオブジェクトの値は、ビット演算 OR 演算と組み合わされたすべての指定された値の値です。  
  
 次の例では、**Parse** メソッドを使用して、文字列形式を列挙値に変換します。 <xref:System.DayOfWeek> 列挙体は、文字列から **Thursday** に初期化されます。  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>関連項目

- [文字列の解析](parsing-strings.md)
- [型の書式設定](formatting-types.md)
- [.NET での型変換](type-conversion.md)

---
title: ユーザー フィルター例外ハンドラーを使用する
description: C# および Visual Basic でユーザー フィルター例外ハンドラーを使用する方法について説明します。
ms.date: 12/14/2020
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2dba43ad2fc685a6555ab43fc973814fd7f359a3
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512672"
---
# <a name="use-user-filtered-exception-handlers"></a>ユーザー フィルター例外ハンドラーを使用する

ユーザー フィルター例外ハンドラーは、ユーザーが例外に対して定義した要件に基づいて、例外をキャッチして処理します。 これらのハンドラーからは、`catch` ステートメントが `when` キーワード (Visual Basic では `Catch` と `When`) と共に使用されます。  
  
 この手法は、特定の例外オブジェクトが複数のエラーに対応する場合に便利です。 その場合、オブジェクトには通常、エラーに関連付けられた特定のエラー コードが格納されているプロパティがあります。 エラー コード プロパティを式で使用すると、その `catch` 句で処理する特定のエラーだけを選択することができます。  
  
 `catch`/`when` ステートメントの例を次に示します。

```csharp
try
{
    //Try statements.  
}
catch (Exception ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 ユーザー フィルター句の式が制限されることはありません。 ユーザー フィルター式の実行中に例外が発生した場合、その例外は破棄され、フィルター式は false と評価されたものと見なされます。 その場合、共通言語ランタイムは、現在の例外に対応するハンドラーの検索を継続します。  
  
## <a name="combine-the-specific-exception-and-the-user-filtered-clauses"></a>特定の例外とユーザー フィルター句の結合  

 `catch` ステートメントには、特定の例外とユーザー フィルター句の両方を含めることができます。 ランタイムは、最初に特定の例外をテストします。 特定の例外がテストを通過すると、ランタイムはユーザー フィルターを実行します。 汎用フィルターには、クラス フィルターで宣言されている変数への参照を含めることができます。 なお、2 つのフィルター句の順序をが逆にすることはできません。  
  
 次の例は、特定の例外が指定された **catch** ステートメントと、**when** キーワードを使用したユーザー フィルター句を示しています。  
  
```csharp
try
{
    //Try statements.  
}
catch (System.Net.Http.HttpRequestException ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a>関連項目

- [例外](index.md)

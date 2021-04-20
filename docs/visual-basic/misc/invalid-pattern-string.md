---
description: '詳細情報: 無効なパターン文字列'
title: 無効なパターン文字列
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 4fbf16dd43ac4ae44e1a99d85caae4a7baf99109
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462062"
---
# <a name="invalid-pattern-string"></a>無効なパターン文字列

検索の `Like` 演算で指定されているパターン文字列が正しくありません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. リスト式に使用できる文字を確認します。  
  
2. パターン範囲の指定で、 `[a-z]`のように、範囲の開始文字が終了文字より小さいことを確認します。  
  
3. パターン範囲の指定で、 `[a--z]`のように、複数のハイフンが続けて指定されていないことを確認します。  
  
4. パターン範囲を右角かっこで終了します。  
  
## <a name="see-also"></a>関連項目

- [Like 演算子](../language-reference/operators/like-operator.md)

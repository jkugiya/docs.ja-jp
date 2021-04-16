---
description: Checked と Unchecked - C# リファレンス
title: Checked と Unchecked - C# リファレンス
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 0121090265881bfa8287e2f9e83ad4b886bf17c1
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477484"
---
# <a name="checked-and-unchecked-c-reference"></a>Checked と Unchecked (C# リファレンス)

C# のステートメントは、checked または unchecked のいずれかのコンテキストで実行できます。 checked コンテキストでは、算術オーバーフローにより例外が発生します。 unchecked コンテキストでは、算術オーバーフローが無視され、結果の格納先の型に収まらない上位ビットが破棄されて、結果が切り詰められます。  
  
- [checked](checked.md): checked コンテキストを指定します。  
  
- [unchecked](unchecked.md): unchecked コンテキストを指定します。  
  
 オーバーフロー チェックにより、次の操作が影響を受けます。  
  
- 整数型で次の定義済み演算子を使用する式:  
  
     `++`、`--`、(単項) `-`、`+`、`-`、`*`、`/`  
  
- 整数型間か、`float` または `double` から整数型へのの明示的な数値変換。  
  
 `checked` と `unchecked` のいずれも指定されない場合、非定数式 (実行時に評価される式) の既定のコンテキストは [**CheckForOverflowUnderflow**](../compiler-options/language.md#checkforoverflowunderflow) コンパイラ オプションの値によって定義されます。 既定では、そのオプションの値の設定が解除され、算術演算が unchecked コンテキストで実行されます。

 定数式 (コンパイル時に完全に評価される式) の場合、既定のコンテキストは常に確認されます。 定数式が unchecked コンテキストに明示的に配置されていない限り、式のコンパイル時の評価中に発生するオーバーフローによってコンパイル時エラーが発生します。
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [ステートメントのキーワード](statement-keywords.md)

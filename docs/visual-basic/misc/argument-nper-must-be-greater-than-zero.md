---
description: "詳細情報: 引数 'NPer' は 0 より大きくなければなりません"
title: 引数 'NPer' は 0 より大きくなければなりません
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: ece5e775e2f05f757b2af53594c626f5a023161e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433409"
---
# <a name="argument-nper-must-be-greater-than-zero"></a>引数 'NPer' は 0 より大きくなければなりません

`NPer` 関数 (定期定額払いおよび固定金利に基づいて年金の期間を指定する `Double` を返します) には、0 を超える引数が必要です。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 式の引数のスペルを確認します。 変数名のスペルが間違っていると、0 に初期化される数値型の変数が暗黙的に生成されることがあります。  
  
- 式の変数 (特に、他のプロシージャから引数としてプロシージャに渡されたもの) に対してこれまで実行した操作を確認します。  
  
## <a name="see-also"></a>関連項目

- [引数の値渡しと参照渡し](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)

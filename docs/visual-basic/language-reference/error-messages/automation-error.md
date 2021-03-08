---
description: '詳細情報: オートメーション エラーです。'
title: オートメーション エラーです。
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: bf3e61bb9b8fec9a831d211b70abdca322c1fe06
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106606"
---
# <a name="automation-error"></a>オートメーション エラーです。

メソッドの実行中、またはオブジェクト変数のプロパティの取得中または設定中にエラーが発生しました。 エラーは、オブジェクトを作成したアプリケーションによって報告されました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. `Err` オブジェクトのプロパティをチェックし、エラーの原因と性質を確認します。  
  
2. アクセス ステートメントの直前で `On Error Resume Next` ステートメントを使用し、アクセス ステートメントの直後のエラーを確認します。  
  
## <a name="see-also"></a>関連項目

- [エラーの種類](../../programming-guide/language-features/error-types.md)
- [Visual Studio フィードバック オプション](/visualstudio/ide/feedback-options)

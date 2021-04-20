---
description: '詳細情報: ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした'
title: ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 5fb0bf1d761faf9d3d0c64e8815e28e14841b1fd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463521"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a>ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした

循環操作が失敗しました。 循環操作は循環しているため、完了できません。 たとえば、オブジェクト A がオブジェクト B の継承を試行し、同様にオブジェクト B がオブジェクト A の継承を試行するような場合です。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 継承を行うときには、参照の循環がないことを確認します。  
  
## <a name="see-also"></a>関連項目

- [エラーの種類](../programming-guide/language-features/error-types.md)
- [Visual Studio デバッガーでブレークポイントを使用する](/visualstudio/debugger/using-breakpoints)

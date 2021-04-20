---
description: "詳細情報: 引数 'Period' は 'Life' 引数以下でなければなりません"
title: 引数 'Period' は 'Life' 引数以下でなければなりません
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_PeriodLELife
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
ms.openlocfilehash: 451defc2e9015b12bd6b340c3c32782ea4d4774f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100458630"
---
# <a name="argument-period-must-be-less-than-or-equal-to-argument-life"></a>引数 'Period' は 'Life' 引数以下でなければなりません

資産の減価償却費計算の対象期間を指定する `Period` 引数の値が `Life` 引数の値より大きくなっています。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- `Life` 引数と `Period` 引数の両方が同じ単位で指定されていることを確認します。 たとえば、 `Life` を月単位で指定する場合は、 `Period` も月単位で指定します。  
  
## <a name="see-also"></a>関連項目

- [引数の値渡しと参照渡し](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)

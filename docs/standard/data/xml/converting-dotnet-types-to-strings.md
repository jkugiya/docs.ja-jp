---
description: '詳細情報: .NET 型から文字列への変換'
title: .NET 型から文字列への変換
ms.date: 03/30/2017
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: 5a3e391eb0e6dc21ae800ede43247d24199efd0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642527"
---
# <a name="convert-net-types-to-strings"></a>.NET 型を文字列に変換する

.NET 型を文字列に変換する場合は、**ToString** メソッドを使用します。 **ToString** メソッドは、渡された型の文字列表現を返します。 XML スキーマ (XSD) 仕様に対応する形式で文字列を返す .NET 型を、次の表に示します。  
  
|.NET の種類|返される文字列型|  
|-------------------------|--------------------------|  
|ブール型|"true"、"false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|形式は、yyyy-MM-ddTHH:mm:sszzzzzz およびそのサブセットです。|  
|Timespan|PnYnMnTnHnMnS の形式。たとえば、`P2Y10M15DT10H30M20S` は 2 年 10 か月 15 日 10 時間 30 分 20 秒の期間です。|  
  
## <a name="see-also"></a>関連項目

- [XML データ型の変換](conversion-of-xml-data-types.md)
- [文字列から .NET データ型への変換](converting-strings-to-dotnet-data-types.md)

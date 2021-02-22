---
title: '方法: WebRequest に一致するプロトコル固有の WebResponse を取得する'
description: .NET Framework で WebRequest に一致するプロトコル固有の WebResponse を取得する方法について学習します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 920704bedce478ed5a4f7906379a634a3b2a4e31
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584343"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a>方法: WebRequest に一致するプロトコル固有の WebResponse を取得する

この例では、WebRequest に一致するプロトコル固有の WebResponse を取得する方法を説明します。  
  
## <a name="example"></a>例  
  
```csharp  
HttpWebRequest req = (HttpWebRequest)WebRequest.Create("http://www.contoso.com/");
HttpWebResponse resp = (HttpWebResponse)req.GetResponse();
```  
  
```vb  
Dim req As HttpWebRequest = CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)
Dim resp As HttpWebResponse = CType(req.GetResponse(), HttpWebResponse)
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  

 この例で必要な要素は次のとおりです。  
  
- **System.Net** 名前空間への参照。  
  
## <a name="see-also"></a>関連項目

- [データの要求](requesting-data.md)

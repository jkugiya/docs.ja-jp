---
description: '詳細情報: 方法:WebRequest を型キャストしてプロトコル固有のプロパティにアクセスする'
title: '方法: WebRequest を型キャストしてプロトコル固有のプロパティにアクセスする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: 24c07a3f2d77dec180476dec3c58f07b40e00c8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662742"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a><span data-ttu-id="f1e2a-103">方法: WebRequest を型キャストしてプロトコル固有のプロパティにアクセスする</span><span class="sxs-lookup"><span data-stu-id="f1e2a-103">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>

<span data-ttu-id="f1e2a-104">この例では、WebRequest を型キャストしてプロトコル固有のプロパティにアクセスできるようにする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="f1e2a-104">This example shows how to typecast a WebRequest so that you can access protocol specific properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1e2a-105">例</span><span class="sxs-lookup"><span data-stu-id="f1e2a-105">Example</span></span>  
  
```csharp  
HttpWebRequest httpreq =
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1e2a-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1e2a-106">See also</span></span>

- [<span data-ttu-id="f1e2a-107">プラグ可能なプロトコルのプログラミング</span><span class="sxs-lookup"><span data-stu-id="f1e2a-107">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)

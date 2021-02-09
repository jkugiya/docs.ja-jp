---
description: '詳細情報: 方法:WebRequest を使用してカスタム プロトコルを登録する'
title: '方法: WebRequest を使用してカスタム プロトコルを登録する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 7415017f20c0c6ed80570992e249fb8121907de2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785758"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="042cd-103">方法: WebRequest を使用してカスタム プロトコルを登録する</span><span class="sxs-lookup"><span data-stu-id="042cd-103">How to: Register a Custom Protocol Using WebRequest</span></span>

<span data-ttu-id="042cd-104">この例では、他の場所で定義されているプロトコル固有のクラスを登録する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="042cd-104">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="042cd-105">この例では、`CustomWebRequestCreator` は、`CustomWebRequest` オブジェクトを返す **Create** メソッドを実装するユーザー実装のオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="042cd-105">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="042cd-106">このコード例では、カスタム プロトコルを実装する `CustomWebRequest` コードが既に作成されているものとします。</span><span class="sxs-lookup"><span data-stu-id="042cd-106">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="042cd-107">例</span><span class="sxs-lookup"><span data-stu-id="042cd-107">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="042cd-108">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="042cd-108">Compiling the Code</span></span>  

 <span data-ttu-id="042cd-109">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="042cd-109">This example requires:</span></span>  
  
 <span data-ttu-id="042cd-110"><xref:System.Net> 名前空間への参照。</span><span class="sxs-lookup"><span data-stu-id="042cd-110">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="042cd-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="042cd-111">See also</span></span>

- [<span data-ttu-id="042cd-112">プラグ可能なプロトコルのプログラミング</span><span class="sxs-lookup"><span data-stu-id="042cd-112">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)

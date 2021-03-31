---
description: '詳細情報: XML ドキュメントの名前空間宣言の変更'
title: XML ドキュメントの名前空間宣言の変更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
ms.openlocfilehash: 9c0f24d271734871b8ff665f729bddb6f34b908e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783444"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="49d5d-103">XML ドキュメントの名前空間宣言の変更</span><span class="sxs-lookup"><span data-stu-id="49d5d-103">Changing Namespace Declarations in an XML Document</span></span>

<span data-ttu-id="49d5d-104">**XmlDocument** は、名前空間宣言と **xmlns** 属性をドキュメント オブジェクト モデルの一部として公開します。</span><span class="sxs-lookup"><span data-stu-id="49d5d-104">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="49d5d-105">名前空間宣言と xmlns 属性は **XmlDocument** に格納されるため、ドキュメントの保存時にはこれらの属性の場所を保持できます。</span><span class="sxs-lookup"><span data-stu-id="49d5d-105">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="49d5d-106">これらの属性を変更しても、ツリーに既に存在する別のノードの **Name**、**NamespaceURI**、**Prefix** プロパティは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="49d5d-106">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="49d5d-107">たとえば、次のドキュメントを読み込むと、`test` 要素の **NamespaceURI** は `123.` になります。</span><span class="sxs-lookup"><span data-stu-id="49d5d-107">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="49d5d-108">その後、次のように `xmlns` 要素を削除しても、`test` 要素の **NamespaceURI** は `123` のまま変わりません。</span><span class="sxs-lookup"><span data-stu-id="49d5d-108">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="49d5d-109">同様に、次のように別の `xmlns` 属性を `doc` 要素に追加しても、`test` 要素の **NamespaceURI** は `123` のまま変わりません。</span><span class="sxs-lookup"><span data-stu-id="49d5d-109">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="49d5d-110">つまり、`xmlns` 属性を変更しても、**XmlDocument** オブジェクトを保存して再び読み込むまで、プロパティは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="49d5d-110">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d5d-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="49d5d-111">See also</span></span>

- [<span data-ttu-id="49d5d-112">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="49d5d-112">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)

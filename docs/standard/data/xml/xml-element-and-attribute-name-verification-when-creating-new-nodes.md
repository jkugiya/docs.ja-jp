---
description: '詳細情報: 新しいノードの作成時における XML 要素名および属性名の検証'
title: 新しいノードの作成時における XML 要素名および属性名の検証
ms.date: 03/30/2017
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 07b878424df57c34c5dc2b614fdff9a5dcef26bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782716"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="2618b-103">新しいノードの作成時における XML 要素名および属性名の検証</span><span class="sxs-lookup"><span data-stu-id="2618b-103">XML Element and Attribute Name Verification when Creating New Nodes</span></span>

<span data-ttu-id="2618b-104">XML ドキュメント オブジェクト モデル (DOM) は、新しい要素ノードまたは属性ノードを作成するときに名前の有効性を確認します。</span><span class="sxs-lookup"><span data-stu-id="2618b-104">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="2618b-105">名前に無効な文字が含まれていると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2618b-105">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="2618b-106">名前が正しくエンコードされ、有効であることを保証するには、**XmlConvert** クラスを使用して名前をエンコードし、アプリケーション レベルで名前をデコードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2618b-106">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="2618b-107">**XmlWriter** には、整形式の XML を生成するための追加の処理を行うメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="2618b-107">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2618b-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="2618b-108">See also</span></span>

- [<span data-ttu-id="2618b-109">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="2618b-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)

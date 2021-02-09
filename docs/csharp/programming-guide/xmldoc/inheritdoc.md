---
description: '詳細情報: <inheritdoc> (C# プログラミング ガイド)'
title: <inheritdoc> - C# プログラミング ガイド
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 960bdfbcec1e3f6a89675273f63b6d398e44947e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719397"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="e6424-103">\<inheritdoc> (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e6424-103">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="e6424-104">構文</span><span class="sxs-lookup"><span data-stu-id="e6424-104">Syntax</span></span>  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a><span data-ttu-id="e6424-105">InheritDoc</span><span class="sxs-lookup"><span data-stu-id="e6424-105">InheritDoc</span></span>

<span data-ttu-id="e6424-106">基底クラス、インターフェイス、および同様のメソッドから、XML コメントを継承します。</span><span class="sxs-lookup"><span data-stu-id="e6424-106">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="e6424-107">これにより、重複する XML コメントの不要なコピーと貼り付けを行う必要がなくなり、XML コメントが自動的に同期されたままになります。</span><span class="sxs-lookup"><span data-stu-id="e6424-107">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="e6424-108">解説</span><span class="sxs-lookup"><span data-stu-id="e6424-108">Remarks</span></span>  

<span data-ttu-id="e6424-109">基底クラスまたはインターフェイスに XML コメントを追加し、InheritDoc によってそのコメントが実装するクラスにコピーされるようにします。</span><span class="sxs-lookup"><span data-stu-id="e6424-109">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="e6424-110">同期メソッドに XML コメントを追加し、InheritDoc によってそのコメントが同じメソッドの非同期バージョンにコピーされるようにします。</span><span class="sxs-lookup"><span data-stu-id="e6424-110">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="e6424-111">特定のメンバーからコメントをコピーしたい場合は、`cref` 属性を使用してそのメンバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e6424-111">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="e6424-112">例</span><span class="sxs-lookup"><span data-stu-id="e6424-112">Examples</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="e6424-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6424-113">See also</span></span>

- [<span data-ttu-id="e6424-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e6424-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e6424-115">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="e6424-115">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)

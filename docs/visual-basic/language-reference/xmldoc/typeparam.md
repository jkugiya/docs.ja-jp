---
description: 詳細については、以下をご覧ください。 <typeparam> (Visual Basic)
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: efb4394ee2badcf52bac75d7d9e317c732789746
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640265"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="93460-103">\<typeparam> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93460-103">\<typeparam> (Visual Basic)</span></span>

<span data-ttu-id="93460-104">型パラメーターの名前と説明を定義します。</span><span class="sxs-lookup"><span data-stu-id="93460-104">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93460-105">構文</span><span class="sxs-lookup"><span data-stu-id="93460-105">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="93460-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="93460-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="93460-107">型パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="93460-107">The name of the type parameter.</span></span> <span data-ttu-id="93460-108">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="93460-108">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="93460-109">型パラメーターの説明。</span><span class="sxs-lookup"><span data-stu-id="93460-109">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93460-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="93460-110">Remarks</span></span>  

 <span data-ttu-id="93460-111">ジェネリック型のコメントまたはジェネリック メンバー宣言で `<typeparam>` タグを使用して、型パラメーターの 1 つについて記述します。</span><span class="sxs-lookup"><span data-stu-id="93460-111">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="93460-112">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="93460-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93460-113">例</span><span class="sxs-lookup"><span data-stu-id="93460-113">Example</span></span>  

 <span data-ttu-id="93460-114">この例では、`<typeparam>` タグを使用して `id` パラメーターを記述します。</span><span class="sxs-lookup"><span data-stu-id="93460-114">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="93460-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="93460-115">See also</span></span>

- [<span data-ttu-id="93460-116">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="93460-116">XML Comment Tags</span></span>](index.md)

---
description: 詳細については、以下をご覧ください。 <para> (Visual Basic)
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 51dd9ff300d980b4c0576566cad5d17375889ba1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740770"
---
# <a name="para-visual-basic"></a><span data-ttu-id="37123-103">\<para> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37123-103">\<para> (Visual Basic)</span></span>

<span data-ttu-id="37123-104">コンテンツが段落として書式設定されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="37123-104">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37123-105">構文</span><span class="sxs-lookup"><span data-stu-id="37123-105">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="37123-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="37123-106">Parameters</span></span>  

 `content`  
 <span data-ttu-id="37123-107">段落のテキストです。</span><span class="sxs-lookup"><span data-stu-id="37123-107">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37123-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="37123-108">Remarks</span></span>  

 <span data-ttu-id="37123-109">`<para>` タグは、[\<summary>](summary.md)、[\<remarks>](remarks.md)、または [\<returns>](returns.md) などのタグ内で使用します。このタグを使用すると、テキストに構造を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="37123-109">The `<para>` tag is for use inside a tag, such as [\<summary>](summary.md), [\<remarks>](remarks.md), or [\<returns>](returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="37123-110">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="37123-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37123-111">例</span><span class="sxs-lookup"><span data-stu-id="37123-111">Example</span></span>  

 <span data-ttu-id="37123-112">この例では、`<para>` タグを使用して、`UpdateRecord` メソッドの解説セクションを 2 つの段落に分割します。</span><span class="sxs-lookup"><span data-stu-id="37123-112">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="37123-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="37123-113">See also</span></span>

- [<span data-ttu-id="37123-114">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="37123-114">XML Comment Tags</span></span>](index.md)

---
description: '詳細情報: <paramref> (Visual Basic)'
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 0ce748213e26c258b290828c42454b0e7fd316f1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456836"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="b0eef-102">\<paramref> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0eef-102">\<paramref> (Visual Basic)</span></span>

<span data-ttu-id="b0eef-103">ワードをパラメーターとして書式設定します。</span><span class="sxs-lookup"><span data-stu-id="b0eef-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0eef-104">構文</span><span class="sxs-lookup"><span data-stu-id="b0eef-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0eef-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b0eef-105">Parameters</span></span>  

 `name`  
 <span data-ttu-id="b0eef-106">参照されるパラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="b0eef-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="b0eef-107">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="b0eef-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0eef-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="b0eef-108">Remarks</span></span>  

 <span data-ttu-id="b0eef-109">`<paramref>` タグは、単語がパラメーターであることを示す方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="b0eef-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="b0eef-110">XML ファイルを処理することで、いくつかの独自の方法でこのパラメーターの書式設定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b0eef-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="b0eef-111">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="b0eef-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0eef-112">例</span><span class="sxs-lookup"><span data-stu-id="b0eef-112">Example</span></span>  

 <span data-ttu-id="b0eef-113">この例では、`<paramref>` タグを使用して `id` パラメーターを参照します。</span><span class="sxs-lookup"><span data-stu-id="b0eef-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b0eef-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0eef-114">See also</span></span>

- [<span data-ttu-id="b0eef-115">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="b0eef-115">XML Comment Tags</span></span>](index.md)

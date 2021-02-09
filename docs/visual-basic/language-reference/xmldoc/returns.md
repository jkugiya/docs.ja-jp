---
description: 詳細については、以下をご覧ください。 <returns> (Visual Basic)
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: ba5f1e231502a67e86ffbb92cf8868c3aecb05d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640382"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="de5c8-103">\<returns> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de5c8-103">\<returns> (Visual Basic)</span></span>

<span data-ttu-id="de5c8-104">プロパティまたは関数の戻り値を指定します。</span><span class="sxs-lookup"><span data-stu-id="de5c8-104">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de5c8-105">構文</span><span class="sxs-lookup"><span data-stu-id="de5c8-105">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="de5c8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="de5c8-106">Parameters</span></span>  

 `description`  
 <span data-ttu-id="de5c8-107">戻り値の説明。</span><span class="sxs-lookup"><span data-stu-id="de5c8-107">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de5c8-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="de5c8-108">Remarks</span></span>  

 <span data-ttu-id="de5c8-109">メソッド宣言のコメントで `<returns>` タグを使用して、戻り値を記述します。</span><span class="sxs-lookup"><span data-stu-id="de5c8-109">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="de5c8-110">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="de5c8-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de5c8-111">例</span><span class="sxs-lookup"><span data-stu-id="de5c8-111">Example</span></span>  

 <span data-ttu-id="de5c8-112">この例では、`<returns>` タグを使用して `DoesRecordExist` 関数が返す内容を説明します。</span><span class="sxs-lookup"><span data-stu-id="de5c8-112">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="de5c8-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="de5c8-113">See also</span></span>

- [<span data-ttu-id="de5c8-114">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="de5c8-114">XML Comment Tags</span></span>](index.md)

---
description: 詳細については、以下をご覧ください。 <param> (Visual Basic)
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 94fe5e11d5846f7fa00eb73c1c4363990ae23b2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700293"
---
# <a name="param-visual-basic"></a><span data-ttu-id="97e5c-103">\<param> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97e5c-103">\<param> (Visual Basic)</span></span>

<span data-ttu-id="97e5c-104">パラメーターの名前と説明を定義します。</span><span class="sxs-lookup"><span data-stu-id="97e5c-104">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97e5c-105">構文</span><span class="sxs-lookup"><span data-stu-id="97e5c-105">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="97e5c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="97e5c-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="97e5c-107">メソッド パラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="97e5c-107">The name of a method parameter.</span></span> <span data-ttu-id="97e5c-108">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="97e5c-108">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="97e5c-109">パラメーターの説明です。</span><span class="sxs-lookup"><span data-stu-id="97e5c-109">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97e5c-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="97e5c-110">Remarks</span></span>  

 <span data-ttu-id="97e5c-111">`<param>` タグは、メソッドのいずれかのパラメーターを記述するために、メソッド宣言のコメントで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97e5c-111">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="97e5c-112">`<param>` タグのテキストは次の場所に表示されます。</span><span class="sxs-lookup"><span data-stu-id="97e5c-112">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="97e5c-113">IntelliSense のパラメーター ヒント。</span><span class="sxs-lookup"><span data-stu-id="97e5c-113">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="97e5c-114">詳細については、「[IntelliSense の使用](/visualstudio/ide/using-intellisense)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97e5c-114">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="97e5c-115">オブジェクト ブラウザー。</span><span class="sxs-lookup"><span data-stu-id="97e5c-115">Object Browser.</span></span> <span data-ttu-id="97e5c-116">詳細については、「[コードの構造の表示](/visualstudio/ide/viewing-the-structure-of-code)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97e5c-116">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="97e5c-117">コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="97e5c-117">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97e5c-118">例</span><span class="sxs-lookup"><span data-stu-id="97e5c-118">Example</span></span>  

 <span data-ttu-id="97e5c-119">この例では、`<param>` タグを使用して `id` パラメーターを記述します。</span><span class="sxs-lookup"><span data-stu-id="97e5c-119">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="97e5c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="97e5c-120">See also</span></span>

- [<span data-ttu-id="97e5c-121">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="97e5c-121">XML Comment Tags</span></span>](index.md)

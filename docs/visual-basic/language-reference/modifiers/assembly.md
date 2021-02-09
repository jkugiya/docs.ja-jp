---
description: '詳細情報: Assembly (Visual Basic)'
title: Assembly
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 60b8ce4ed2b8b5cb7deeabb702c33d1e561d765f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701184"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="d906d-103">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d906d-103">Assembly (Visual Basic)</span></span>

<span data-ttu-id="d906d-104">ソース ファイルの先頭の属性がアセンブリ全体に適用されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d906d-104">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d906d-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="d906d-105">Remarks</span></span>  

 <span data-ttu-id="d906d-106">個々のプログラミング要素には、クラスやプロパティなどの多くの属性が関連しています。</span><span class="sxs-lookup"><span data-stu-id="d906d-106">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="d906d-107">そのような属性を適用するには、山かっこ (`< >`) 内の属性ブロックを宣言ステートメントに直接アタッチします。</span><span class="sxs-lookup"><span data-stu-id="d906d-107">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="d906d-108">属性が次の要素だけでなく、アセンブリ全体に関連する場合は、属性ブロックをソース ファイルの先頭に配置し、`Assembly` キーワードで属性を識別します。</span><span class="sxs-lookup"><span data-stu-id="d906d-108">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="d906d-109">それを現在のアセンブリ モジュールに適用する場合、[Module](module-keyword.md) キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="d906d-109">If it applies to the current assembly module, you use the [Module](module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="d906d-110">また、AssemblyInfo.vb ファイル内のアセンブリに属性を適用することもできます。この場合、メイン ソースコード ファイルで属性ブロックを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d906d-110">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d906d-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="d906d-111">See also</span></span>

- [<span data-ttu-id="d906d-112">Module \<keyword></span><span class="sxs-lookup"><span data-stu-id="d906d-112">Module \<keyword></span></span>](module-keyword.md)
- [<span data-ttu-id="d906d-113">属性の概要</span><span class="sxs-lookup"><span data-stu-id="d906d-113">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)

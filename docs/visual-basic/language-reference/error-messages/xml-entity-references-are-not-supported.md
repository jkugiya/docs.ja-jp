---
description: '詳細情報: BC31180:XML エンティティの参照はサポートされていません'
title: XML エンティティの参照はサポートされていません
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: c45202fbd97d2343caf6bf4cdccf9368d0a7a295
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701418"
---
# <a name="bc31180-xml-entity-references-are-not-supported"></a><span data-ttu-id="3202f-103">BC31180:XML エンティティの参照はサポートされていません</span><span class="sxs-lookup"><span data-stu-id="3202f-103">BC31180: XML entity references are not supported</span></span>

<span data-ttu-id="3202f-104">XML 1.0 仕様で定義されていないエンティティ参照 (`©` など) が、XML リテラルの値として含まれています。</span><span class="sxs-lookup"><span data-stu-id="3202f-104">An entity reference (for example, `©`) that is not defined in the XML 1.0 specification is included as a value for an XML literal.</span></span> <span data-ttu-id="3202f-105">XML リテラルでは、`&`、`"`、`<`、`>`、および `'` の XML エンティティ参照のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3202f-105">Only `&`, `"`, `<`, `>`, and `'` XML entity references are supported in XML literals.</span></span>

 <span data-ttu-id="3202f-106">**エラー ID:** BC31180</span><span class="sxs-lookup"><span data-stu-id="3202f-106">**Error ID:** BC31180</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3202f-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3202f-107">To correct this error</span></span>

- <span data-ttu-id="3202f-108">サポートされていないエンティティ参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="3202f-108">Remove the unsupported entity reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="3202f-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3202f-109">See also</span></span>

- [<span data-ttu-id="3202f-110">XML リテラルと XML 1.0 仕様</span><span class="sxs-lookup"><span data-stu-id="3202f-110">XML Literals and the XML 1.0 Specification</span></span>](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [<span data-ttu-id="3202f-111">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="3202f-111">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="3202f-112">XML</span><span class="sxs-lookup"><span data-stu-id="3202f-112">XML</span></span>](../../programming-guide/language-features/xml/index.md)

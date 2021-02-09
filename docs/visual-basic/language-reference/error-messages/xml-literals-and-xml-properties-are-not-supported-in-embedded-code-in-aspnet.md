---
description: '詳細情報: BC31200:XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません'
title: XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 0a5328676ee38a56334b77f665a464daa586ce3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701405"
---
# <a name="bc31200-xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="2a617-103">BC31200:XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません</span><span class="sxs-lookup"><span data-stu-id="2a617-103">BC31200: XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>

<span data-ttu-id="2a617-104">XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="2a617-104">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="2a617-105">XML 機能を使用するには、コードをコードビハインドに移動します。</span><span class="sxs-lookup"><span data-stu-id="2a617-105">To use XML features, move the code to code-behind.</span></span>

 <span data-ttu-id="2a617-106">XML リテラルまたは XML 軸プロパティは、ASP.NET ファイルの埋め込みコード (`<%= =>`) 内で定義されます。</span><span class="sxs-lookup"><span data-stu-id="2a617-106">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>

 <span data-ttu-id="2a617-107">**エラー ID:** BC31200</span><span class="sxs-lookup"><span data-stu-id="2a617-107">**Error ID:** BC31200</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2a617-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="2a617-108">To correct this error</span></span>

- <span data-ttu-id="2a617-109">XML リテラルまたは XML 軸プロパティが含まれているコードを、ASP.NET 分離コード ファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="2a617-109">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a617-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a617-110">See also</span></span>

- [<span data-ttu-id="2a617-111">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="2a617-111">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="2a617-112">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="2a617-112">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="2a617-113">XML</span><span class="sxs-lookup"><span data-stu-id="2a617-113">XML</span></span>](../../programming-guide/language-features/xml/index.md)

---
description: "詳細情報: BC31194:型 'type1' の値を 'type2' に変換できません"
title: 型 'type1' の値を 'type2' に変換できません
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 8cdb5206f0bc09a447ce241921b0efda63792c28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674780"
---
# <a name="bc31194-value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="81f72-103">BC31194:型 'type1' の値を 'type2' に変換できません</span><span class="sxs-lookup"><span data-stu-id="81f72-103">BC31194: Value of type 'type1' cannot be converted to 'type2'</span></span>

<span data-ttu-id="81f72-104">型 'type1' の値を 'type2' に変換できません。</span><span class="sxs-lookup"><span data-stu-id="81f72-104">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="81f72-105">'\<parentElement>' の最初の要素の文字列値は、'Value' プロパティを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="81f72-105">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>

 <span data-ttu-id="81f72-106">XML リテラルを特定の型を暗黙的にキャストしようとしました。</span><span class="sxs-lookup"><span data-stu-id="81f72-106">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="81f72-107">XML リテラルは、指定した型に暗黙的にキャストできません。</span><span class="sxs-lookup"><span data-stu-id="81f72-107">The XML literal cannot be implicitly cast to the specified type.</span></span>

 <span data-ttu-id="81f72-108">**エラー ID:** BC31194</span><span class="sxs-lookup"><span data-stu-id="81f72-108">**Error ID:** BC31194</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="81f72-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="81f72-109">To correct this error</span></span>

- <span data-ttu-id="81f72-110">XML リテラルの `Value` プロパティを使用して、その値を `String`として参照します。</span><span class="sxs-lookup"><span data-stu-id="81f72-110">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="81f72-111">`CType` 関数、別の型変換関数、または <xref:System.Convert> クラスを使用して、指定した型として値をキャストします。</span><span class="sxs-lookup"><span data-stu-id="81f72-111">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>

## <a name="see-also"></a><span data-ttu-id="81f72-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="81f72-112">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="81f72-113">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="81f72-113">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="81f72-114">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="81f72-114">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="81f72-115">XML</span><span class="sxs-lookup"><span data-stu-id="81f72-115">XML</span></span>](../../programming-guide/language-features/xml/index.md)

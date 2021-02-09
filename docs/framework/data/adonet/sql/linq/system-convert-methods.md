---
description: '詳細情報: System.Convert メソッド'
title: System.Convert メソッド
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: a323f8d0c3c4a8d1248409d2ec27565acdc58222
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681410"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="d7444-103">System.Convert メソッド</span><span class="sxs-lookup"><span data-stu-id="d7444-103">System.Convert Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="d7444-104">は、次の <xref:System.Convert> メソッドをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d7444-104">does not support the following <xref:System.Convert> methods.</span></span>

- <span data-ttu-id="d7444-105"><xref:System.IFormatProvider> パラメーターを持つ形式。</span><span class="sxs-lookup"><span data-stu-id="d7444-105">Versions with an <xref:System.IFormatProvider> parameter.</span></span>

- <span data-ttu-id="d7444-106">文字配列またはバイト配列を扱うメソッド。</span><span class="sxs-lookup"><span data-stu-id="d7444-106">Methods that involve char arrays or byte arrays:</span></span>

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- <span data-ttu-id="d7444-107">次のメソッド。</span><span class="sxs-lookup"><span data-stu-id="d7444-107">The following methods:</span></span>

  - <span data-ttu-id="d7444-108">`public static <Type2> To<Type2>(<Type1> value);` (</span><span class="sxs-lookup"><span data-stu-id="d7444-108">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>

    <span data-ttu-id="d7444-109">`Type1` および `Type2` は `sbyte`、`uint`、`ulong`、`ushort` のいずれか)</span><span class="sxs-lookup"><span data-stu-id="d7444-109">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>

  - <span data-ttu-id="d7444-110">C#:</span><span class="sxs-lookup"><span data-stu-id="d7444-110">C#:</span></span>

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - <span data-ttu-id="d7444-111">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="d7444-111">Visual Basic:</span></span>

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a><span data-ttu-id="d7444-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7444-112">See also</span></span>

- [<span data-ttu-id="d7444-113">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="d7444-113">Data Types and Functions</span></span>](data-types-and-functions.md)

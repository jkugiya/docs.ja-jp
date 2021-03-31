---
description: '詳細情報: .NET 型から文字列への変換'
title: .NET 型から文字列への変換
ms.date: 03/30/2017
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: 5a3e391eb0e6dc21ae800ede43247d24199efd0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642527"
---
# <a name="convert-net-types-to-strings"></a><span data-ttu-id="4f22d-103">.NET 型を文字列に変換する</span><span class="sxs-lookup"><span data-stu-id="4f22d-103">Convert .NET types to strings</span></span>

<span data-ttu-id="4f22d-104">.NET 型を文字列に変換する場合は、**ToString** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4f22d-104">If you want to convert a .NET type to a string, use the **ToString** method.</span></span> <span data-ttu-id="4f22d-105">**ToString** メソッドは、渡された型の文字列表現を返します。</span><span class="sxs-lookup"><span data-stu-id="4f22d-105">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="4f22d-106">XML スキーマ (XSD) 仕様に対応する形式で文字列を返す .NET 型を、次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="4f22d-106">The following table lists the .NET types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="4f22d-107">.NET の種類</span><span class="sxs-lookup"><span data-stu-id="4f22d-107">.NET type</span></span>|<span data-ttu-id="4f22d-108">返される文字列型</span><span class="sxs-lookup"><span data-stu-id="4f22d-108">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="4f22d-109">ブール型</span><span class="sxs-lookup"><span data-stu-id="4f22d-109">Boolean</span></span>|<span data-ttu-id="4f22d-110">"true"、"false"</span><span class="sxs-lookup"><span data-stu-id="4f22d-110">"true", "false"</span></span>|  
|<span data-ttu-id="4f22d-111">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="4f22d-111">Single.PositiveInfinity</span></span>|<span data-ttu-id="4f22d-112">"INF"</span><span class="sxs-lookup"><span data-stu-id="4f22d-112">"INF"</span></span>|  
|<span data-ttu-id="4f22d-113">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="4f22d-113">Single.NegativeInfinity</span></span>|<span data-ttu-id="4f22d-114">"-INF"</span><span class="sxs-lookup"><span data-stu-id="4f22d-114">"-INF"</span></span>|  
|<span data-ttu-id="4f22d-115">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="4f22d-115">Double.PositiveInfinity</span></span>|<span data-ttu-id="4f22d-116">"INF"</span><span class="sxs-lookup"><span data-stu-id="4f22d-116">"INF"</span></span>|  
|<span data-ttu-id="4f22d-117">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="4f22d-117">Double.NegativeInfinity</span></span>|<span data-ttu-id="4f22d-118">"-INF"</span><span class="sxs-lookup"><span data-stu-id="4f22d-118">"-INF"</span></span>|  
|<span data-ttu-id="4f22d-119">DateTime</span><span class="sxs-lookup"><span data-stu-id="4f22d-119">DateTime</span></span>|<span data-ttu-id="4f22d-120">形式は、yyyy-MM-ddTHH:mm:sszzzzzz およびそのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="4f22d-120">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="4f22d-121">Timespan</span><span class="sxs-lookup"><span data-stu-id="4f22d-121">Timespan</span></span>|<span data-ttu-id="4f22d-122">PnYnMnTnHnMnS の形式。たとえば、`P2Y10M15DT10H30M20S` は 2 年 10 か月 15 日 10 時間 30 分 20 秒の期間です。</span><span class="sxs-lookup"><span data-stu-id="4f22d-122">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f22d-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f22d-123">See also</span></span>

- [<span data-ttu-id="4f22d-124">XML データ型の変換</span><span class="sxs-lookup"><span data-stu-id="4f22d-124">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="4f22d-125">文字列から .NET データ型への変換</span><span class="sxs-lookup"><span data-stu-id="4f22d-125">Converting Strings to .NET Data Types</span></span>](converting-strings-to-dotnet-data-types.md)

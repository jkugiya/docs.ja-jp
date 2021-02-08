---
description: '詳細情報: SqlChars. Stream プロパティ'
title: SqlChars. Stream プロパティ (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9af0df98b268a749d890ab1b40dddbbe98ced8d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802646"
---
# <a name="sqlcharsstream-property"></a><span data-ttu-id="1bbe1-103">SqlChars.Stream プロパティ</span><span class="sxs-lookup"><span data-stu-id="1bbe1-103">SqlChars.Stream Property</span></span>

<span data-ttu-id="1bbe1-104">文字ストリームを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="1bbe1-104">Gets or sets the character stream.</span></span> <span data-ttu-id="1bbe1-105">このプロパティを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。</span><span class="sxs-lookup"><span data-stu-id="1bbe1-105">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="1bbe1-106">SQL Server での使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="1bbe1-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="1bbe1-107">他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="1bbe1-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="1bbe1-108">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="1bbe1-108">Property value</span></span>

`System.Data.SqlTypes.SqlStreamChars`\
<span data-ttu-id="1bbe1-109">文字ストリーム。</span><span class="sxs-lookup"><span data-stu-id="1bbe1-109">The character stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="1bbe1-110">解説</span><span class="sxs-lookup"><span data-stu-id="1bbe1-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="1bbe1-111">`SqlChars.Stream`プロパティは内部であり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="1bbe1-111">The `SqlChars.Stream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="1bbe1-112">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1bbe1-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="1bbe1-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="1bbe1-113">Requirements</span></span>

<span data-ttu-id="1bbe1-114">**名前空間:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="1bbe1-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="1bbe1-115">**アセンブリ:** System.Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="1bbe1-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="1bbe1-116">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1bbe1-116">**.NET Framework versions:** Available since 2.0.</span></span>

---
description: '詳細情報: SqlStreamChars. Length プロパティ'
title: SqlStreamChars. Length プロパティ (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: b0a9686cadc6d4018c7f291f0326b71195fd5cf5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802594"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="5ba1a-103">SqlStreamChars. Length プロパティ</span><span class="sxs-lookup"><span data-stu-id="5ba1a-103">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="5ba1a-104">派生クラスでオーバーライドされた場合、現在のストリームの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ba1a-104">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="5ba1a-105">このプロパティを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。</span><span class="sxs-lookup"><span data-stu-id="5ba1a-105">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="5ba1a-106">SQL Server での使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="5ba1a-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="5ba1a-107">他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="5ba1a-107">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ba1a-108">構文</span><span class="sxs-lookup"><span data-stu-id="5ba1a-108">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="5ba1a-109">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="5ba1a-109">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="5ba1a-110">ストリーム長。</span><span class="sxs-lookup"><span data-stu-id="5ba1a-110">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ba1a-111">解説</span><span class="sxs-lookup"><span data-stu-id="5ba1a-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="5ba1a-112">`SqlStreamChars.Length`プロパティはプライベートであり、コード内で直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="5ba1a-112">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="5ba1a-113">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5ba1a-113">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ba1a-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="5ba1a-114">Requirements</span></span>

<span data-ttu-id="5ba1a-115">**名前空間:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="5ba1a-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="5ba1a-116">**アセンブリ:** System.Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="5ba1a-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="5ba1a-117">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ba1a-117">**.NET Framework versions:** Available since 2.0.</span></span>

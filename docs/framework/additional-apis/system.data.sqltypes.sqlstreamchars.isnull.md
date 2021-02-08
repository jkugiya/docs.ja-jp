---
description: 詳細については、「SqlStreamChars. IsNull プロパティ」を参照してください。
title: SqlStreamChars. IsNull プロパティ (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: b1408a8ba9cd1c38f73d5fa6b818f441d6223bc8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791921"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="e5f02-103">SqlStreamChars. IsNull プロパティ</span><span class="sxs-lookup"><span data-stu-id="e5f02-103">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="e5f02-104">派生クラスでオーバーライドされた場合、ストリームがであるかどうかを示す値を取得し `null` ます。</span><span class="sxs-lookup"><span data-stu-id="e5f02-104">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="e5f02-105">このプロパティを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。</span><span class="sxs-lookup"><span data-stu-id="e5f02-105">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e5f02-106">SQL Server での使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="e5f02-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e5f02-107">他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="e5f02-107">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5f02-108">構文</span><span class="sxs-lookup"><span data-stu-id="e5f02-108">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="e5f02-109">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="e5f02-109">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="e5f02-110">`true` ストリームがの場合は `null` 。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="e5f02-110">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5f02-111">解説</span><span class="sxs-lookup"><span data-stu-id="e5f02-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e5f02-112">`SqlStreamChars.IsNull`プロパティはプライベートであり、コード内で直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="e5f02-112">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e5f02-113">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e5f02-113">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5f02-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="e5f02-114">Requirements</span></span>

<span data-ttu-id="e5f02-115">**名前空間:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e5f02-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e5f02-116">**アセンブリ:** System.Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="e5f02-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e5f02-117">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e5f02-117">**.NET Framework versions:** Available since 2.0.</span></span>

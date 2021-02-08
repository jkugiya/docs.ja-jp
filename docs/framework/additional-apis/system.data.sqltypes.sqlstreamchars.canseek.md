---
description: 詳細については、「SqlStreamChars. CanSeek プロパティ」を参照してください。
title: SqlStreamChars. CanSeek プロパティ (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 5919a66bef9ac31e0ef15ad4af64b456700605f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802620"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="61536-103">SqlStreamChars. CanSeek プロパティ</span><span class="sxs-lookup"><span data-stu-id="61536-103">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="61536-104">派生クラスでオーバーライドされた場合、現在のストリームがシーク操作をサポートしているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="61536-104">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="61536-105">このプロパティを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。</span><span class="sxs-lookup"><span data-stu-id="61536-105">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="61536-106">SQL Server での使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="61536-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="61536-107">他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="61536-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="61536-108">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="61536-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="61536-109">`true` 現在のストリームがシーク操作をサポートしている場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="61536-109">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="61536-110">解説</span><span class="sxs-lookup"><span data-stu-id="61536-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="61536-111">`SqlStreamChars.CanSeek`プロパティはプライベートであり、コード内で直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="61536-111">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="61536-112">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="61536-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="61536-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="61536-113">Requirements</span></span>

<span data-ttu-id="61536-114">**名前空間:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="61536-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="61536-115">**アセンブリ:** System.Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="61536-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="61536-116">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="61536-116">**.NET Framework versions:** Available since 2.0.</span></span>

---
description: '詳細情報: SmiOrderProperty プロパティ'
title: SmiOrderProperty プロパティ (Microsoft. SqlServer. Server)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: fc2151d3f36a6746e80e2fd6d611a803b2c3162e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767987"
---
# <a name="smiorderpropertyitem-property"></a><span data-ttu-id="d2f14-103">SmiOrderProperty プロパティ</span><span class="sxs-lookup"><span data-stu-id="d2f14-103">SmiOrderProperty.Item Property</span></span>

<span data-ttu-id="d2f14-104">エンティティの列の順序を取得します。</span><span class="sxs-lookup"><span data-stu-id="d2f14-104">Gets the column order for the entity.</span></span> <span data-ttu-id="d2f14-105">このプロパティを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。</span><span class="sxs-lookup"><span data-stu-id="d2f14-105">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="d2f14-106">SQL Server での使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="d2f14-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="d2f14-107">他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="d2f14-107">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2f14-108">構文</span><span class="sxs-lookup"><span data-stu-id="d2f14-108">Syntax</span></span>

```csharp
internal SmiColumnOrder Item { get; }
```

## <a name="property-value"></a><span data-ttu-id="d2f14-109">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="d2f14-109">Property value</span></span>

<span data-ttu-id="d2f14-110">列の順序。</span><span class="sxs-lookup"><span data-stu-id="d2f14-110">The column order.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2f14-111">解説</span><span class="sxs-lookup"><span data-stu-id="d2f14-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d2f14-112">`SmiOrderProperty.Item`プロパティは内部であり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="d2f14-112">The `SmiOrderProperty.Item` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d2f14-113">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d2f14-113">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2f14-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="d2f14-114">Requirements</span></span>

<span data-ttu-id="d2f14-115">**名前空間:** <xref:Microsoft.SqlServer.Server></span><span class="sxs-lookup"><span data-stu-id="d2f14-115">**Namespace:** <xref:Microsoft.SqlServer.Server></span></span>

<span data-ttu-id="d2f14-116">**アセンブリ:** System.Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="d2f14-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="d2f14-117">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2f14-117">**.NET Framework versions:** Available since 2.0.</span></span>

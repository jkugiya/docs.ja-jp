---
description: 詳細については、「SqlStreamChars. Dispose (Boolean) メソッド」を参照してください。
title: SqlStreamChars. Dispose (Boolean) メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ce24cc885d87a3ff0bbcdbea7992ca78ee592454
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802607"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="d2e11-103">SqlStreamChars. Dispose (Boolean) メソッド</span><span class="sxs-lookup"><span data-stu-id="d2e11-103">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="d2e11-104">派生クラスでオーバーライドされると、ストリームによって使用されるリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="d2e11-104">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="d2e11-105">このメソッドを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。</span><span class="sxs-lookup"><span data-stu-id="d2e11-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="d2e11-106">SQL Server での使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="d2e11-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="d2e11-107">他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="d2e11-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="d2e11-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d2e11-108">Parameters</span></span>

`disposing`\
<span data-ttu-id="d2e11-109">マネージド リソースとアンマネージド リソースの両方を解放する場合は `true`。アンマネージド リソースだけを解放する場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="d2e11-109">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2e11-110">解説</span><span class="sxs-lookup"><span data-stu-id="d2e11-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d2e11-111">`SqlStreamChars.Dispose`メソッドはプライベートであり、コード内で直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="d2e11-111">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d2e11-112">Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d2e11-112">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2e11-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="d2e11-113">Requirements</span></span>

<span data-ttu-id="d2e11-114">**名前空間:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="d2e11-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="d2e11-115">**アセンブリ:** System.Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="d2e11-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="d2e11-116">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2e11-116">**.NET Framework versions:** Available since 2.0.</span></span>

---
description: '詳細情報: SqlStreamChars. Close メソッド'
title: SqlStreamChars. Close メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 27f2ea6e288d166f3b63979a83a1cf80eeced334
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782378"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="5552e-103">SqlStreamChars. Close メソッド</span><span class="sxs-lookup"><span data-stu-id="5552e-103">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="5552e-104">現在のストリームを閉じ、ストリームに関連付けられているすべてのシステムリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="5552e-104">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="5552e-105">このメソッドを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。</span><span class="sxs-lookup"><span data-stu-id="5552e-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="5552e-106">SQL Server での使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="5552e-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="5552e-107">他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="5552e-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="5552e-108">解説</span><span class="sxs-lookup"><span data-stu-id="5552e-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="5552e-109">`SqlStreamChars.Close`メソッドはプライベートであり、コード内で直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="5552e-109">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="5552e-110">Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5552e-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="5552e-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="5552e-111">Requirements</span></span>

<span data-ttu-id="5552e-112">**名前空間:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="5552e-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="5552e-113">**アセンブリ:** System.Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="5552e-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="5552e-114">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="5552e-114">**.NET Framework versions:** Available since 2.0.</span></span>

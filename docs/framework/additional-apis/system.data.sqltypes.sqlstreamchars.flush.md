---
description: 詳細については、「SqlStreamChars. Flush メソッド」を参照してください。
title: SqlStreamChars. Flush メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 8f519ffb8248a17608319eb0fbfe598f9ee3487a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684465"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="17c46-103">SqlStreamChars. Flush メソッド</span><span class="sxs-lookup"><span data-stu-id="17c46-103">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="17c46-104">派生クラスによってオーバーライドされた場合は、ストリームに対応するすべてのバッファーをクリアし、バッファー内のデータを基になるデバイスに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="17c46-104">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="17c46-105">このメソッドを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。</span><span class="sxs-lookup"><span data-stu-id="17c46-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="17c46-106">SQL Server での使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="17c46-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="17c46-107">他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="17c46-107">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="17c46-108">構文</span><span class="sxs-lookup"><span data-stu-id="17c46-108">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="17c46-109">解説</span><span class="sxs-lookup"><span data-stu-id="17c46-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="17c46-110">`SqlStreamChars.Flush`メソッドはプライベートであり、コード内で直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="17c46-110">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="17c46-111">Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="17c46-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="17c46-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="17c46-112">Requirements</span></span>

<span data-ttu-id="17c46-113">**名前空間:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="17c46-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="17c46-114">**アセンブリ:** System.Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="17c46-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="17c46-115">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="17c46-115">**.NET Framework versions:** Available since 2.0.</span></span>

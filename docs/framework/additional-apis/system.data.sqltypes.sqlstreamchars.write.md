---
description: 詳細については、「SqlStreamChars. Write (Char [], Int32, Int32) メソッド」を参照してください。
title: SqlStreamChars. Write (Char [], Int32, Int32) メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 3031b57902215df01c5c30625281a99be73ba2d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802555"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="ba8f3-103">SqlStreamChars. Write (Char [], Int32, Int32) メソッド</span><span class="sxs-lookup"><span data-stu-id="ba8f3-103">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="ba8f3-104">派生クラスでオーバーライドされた場合、現在のストリームに文字シーケンスを書き込み、書き込んだ文字数だけストリーム内の現在位置を進めます。</span><span class="sxs-lookup"><span data-stu-id="ba8f3-104">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="ba8f3-105">このメソッドを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。</span><span class="sxs-lookup"><span data-stu-id="ba8f3-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="ba8f3-106">SQL Server での使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="ba8f3-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="ba8f3-107">他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba8f3-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="ba8f3-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ba8f3-108">Parameters</span></span>

`buffer`  
<span data-ttu-id="ba8f3-109">書き込む文字配列。</span><span class="sxs-lookup"><span data-stu-id="ba8f3-109">A char array to write.</span></span>

`offset`  
<span data-ttu-id="ba8f3-110">Origin を基準とするオフセット。</span><span class="sxs-lookup"><span data-stu-id="ba8f3-110">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="ba8f3-111">現在のストリームに書き込む文字数。</span><span class="sxs-lookup"><span data-stu-id="ba8f3-111">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba8f3-112">解説</span><span class="sxs-lookup"><span data-stu-id="ba8f3-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="ba8f3-113">`SqlStreamChars.Write`メソッドはプライベートであり、コード内で直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="ba8f3-113">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ba8f3-114">Microsoft では、この方法を使用した運用アプリケーションの作成をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="ba8f3-114">Microsoft does not support the use of this method write in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba8f3-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="ba8f3-115">Requirements</span></span>

<span data-ttu-id="ba8f3-116">**名前空間:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="ba8f3-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="ba8f3-117">**アセンブリ:** System.Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="ba8f3-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="ba8f3-118">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba8f3-118">**.NET Framework versions:** Available since 2.0.</span></span>

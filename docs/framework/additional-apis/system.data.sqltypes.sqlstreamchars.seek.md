---
description: 詳細については、「SqlStreamChars. Seek (Int64, SeekOrigin) メソッド」を参照してください。
title: SqlStreamChars. Seek (Int64, SeekOrigin) メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 00f71aff95045d566b7932aec3f7e18259b4dfa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802568"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="1cc87-103">SqlStreamChars. Seek (Int64, SeekOrigin) メソッド</span><span class="sxs-lookup"><span data-stu-id="1cc87-103">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="1cc87-104">派生クラスでオーバーライドされた場合は、現在のストリーム内の位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="1cc87-104">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="1cc87-105">このメソッドを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。</span><span class="sxs-lookup"><span data-stu-id="1cc87-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="1cc87-106">SQL Server での使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="1cc87-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="1cc87-107">他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="1cc87-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="1cc87-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1cc87-108">Parameters</span></span>

`offset`\
<span data-ttu-id="1cc87-109">`origin` からのバイト オフセット。</span><span class="sxs-lookup"><span data-stu-id="1cc87-109">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="1cc87-110">新しい位置を取得する参照ポイントを示す列挙値の1つ。</span><span class="sxs-lookup"><span data-stu-id="1cc87-110">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="1cc87-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="1cc87-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="1cc87-112">現在のストリーム内の新しい位置。</span><span class="sxs-lookup"><span data-stu-id="1cc87-112">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="1cc87-113">解説</span><span class="sxs-lookup"><span data-stu-id="1cc87-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="1cc87-114">`SqlStreamChars.Seek`メソッドはプライベートであり、コード内で直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="1cc87-114">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="1cc87-115">Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1cc87-115">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="1cc87-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="1cc87-116">Requirements</span></span>

<span data-ttu-id="1cc87-117">**名前空間:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="1cc87-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="1cc87-118">**アセンブリ:** System.Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="1cc87-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="1cc87-119">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1cc87-119">**.NET Framework versions:** Available since 2.0.</span></span>

---
description: 詳細については、次を参照してください。 SqlStreamChars. 読み取り (Char [], Int32, Int32) メソッド
title: SqlStreamChars. Read (Char [], Int32, Int32) メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: a899ddff7b7242fcc32aaf7b7f7794970596027b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802581"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="a6625-103">SqlStreamChars. Read (Char [], Int32, Int32) メソッド</span><span class="sxs-lookup"><span data-stu-id="a6625-103">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="a6625-104">派生クラスでオーバーライドされると、入力ストリームから次の文字セットを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="a6625-104">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="a6625-105">このメソッドを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。</span><span class="sxs-lookup"><span data-stu-id="a6625-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="a6625-106">SQL Server での使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="a6625-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="a6625-107">他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="a6625-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="a6625-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a6625-108">Parameters</span></span>

`buffer`\
<span data-ttu-id="a6625-109">読み取る文字配列。</span><span class="sxs-lookup"><span data-stu-id="a6625-109">A char array to read.</span></span>

`offset`\
<span data-ttu-id="a6625-110">Origin を基準とするオフセット。</span><span class="sxs-lookup"><span data-stu-id="a6625-110">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="a6625-111">現在のストリームから読み取る文字数。</span><span class="sxs-lookup"><span data-stu-id="a6625-111">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="a6625-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="a6625-112">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="a6625-113">バッファーに読み取られた合計文字数。</span><span class="sxs-lookup"><span data-stu-id="a6625-113">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6625-114">解説</span><span class="sxs-lookup"><span data-stu-id="a6625-114">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="a6625-115">`SqlStreamChars.Read`メソッドはプライベートであり、コード内で直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="a6625-115">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a6625-116">Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a6625-116">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6625-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="a6625-117">Requirements</span></span>

<span data-ttu-id="a6625-118">**名前空間:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="a6625-118">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="a6625-119">**アセンブリ:** System.Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="a6625-119">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="a6625-120">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6625-120">**.NET Framework versions:** Available since 2.0.</span></span>

---
description: 詳細については、次を参照してください。 PooledStream. NetworkStream プロパティ
title: PooledStream. NetworkStream プロパティ (System.Net)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.PooledStream.NetworkStream
- System.Net.PooledStream.get_NetworkStream
- System.Net.PooledStream.set_NetworkStream
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 8a4f1d6bd9297028e763ef73bf96f85cbbfdafd6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699637"
---
# <a name="pooledstreamnetworkstream-property"></a><span data-ttu-id="eddaf-103">PooledStream. NetworkStream プロパティ</span><span class="sxs-lookup"><span data-stu-id="eddaf-103">PooledStream.NetworkStream Property</span></span>

<span data-ttu-id="eddaf-104">ソケットのネットワークストリームを取得または設定し `PooledStream` ます。</span><span class="sxs-lookup"><span data-stu-id="eddaf-104">Gets or sets the network stream for the `PooledStream` socket.</span></span>

## <a name="syntax"></a><span data-ttu-id="eddaf-105">構文</span><span class="sxs-lookup"><span data-stu-id="eddaf-105">Syntax</span></span>

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="eddaf-106">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="eddaf-106">Property value</span></span>

<xref:System.Net.Sockets.NetworkStream>  
<span data-ttu-id="eddaf-107">ソケットのネットワークストリーム `PooledStream` 。</span><span class="sxs-lookup"><span data-stu-id="eddaf-107">The network stream for the `PooledStream` socket.</span></span>

## <a name="remarks"></a><span data-ttu-id="eddaf-108">解説</span><span class="sxs-lookup"><span data-stu-id="eddaf-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="eddaf-109">`PooledStream.NetworkStream`プロパティは内部であり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="eddaf-109">The `PooledStream.NetworkStream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="eddaf-110">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="eddaf-110">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="eddaf-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="eddaf-111">Requirements</span></span>

<span data-ttu-id="eddaf-112">**名前空間:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="eddaf-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="eddaf-113">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="eddaf-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="eddaf-114">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="eddaf-114">**.NET Framework versions:** Available since 2.0.</span></span>

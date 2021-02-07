---
description: '詳細情報: TlsStream.m_Worker フィールド'
title: TlsStream.m_Worker フィールド (System.Net)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.TlsStream.m_Worker
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: d929b0b1949bc1902425c016bfd770d4c66a3257
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699520"
---
# <a name="tlsstreamm_worker-field"></a><span data-ttu-id="56e3b-103">TlsStream.m_Worker フィールド</span><span class="sxs-lookup"><span data-stu-id="56e3b-103">TlsStream.m_Worker Field</span></span>

<span data-ttu-id="56e3b-104">SSL ストリームの状態を表します。</span><span class="sxs-lookup"><span data-stu-id="56e3b-104">Represents the state of the SSL stream.</span></span>

## <a name="syntax"></a><span data-ttu-id="56e3b-105">構文</span><span class="sxs-lookup"><span data-stu-id="56e3b-105">Syntax</span></span>

```csharp
private SslState m_Worker;
```

## <a name="field-value"></a><span data-ttu-id="56e3b-106">フィールド値</span><span class="sxs-lookup"><span data-stu-id="56e3b-106">Field value</span></span>

`System.Net.Security.SslState`  
<span data-ttu-id="56e3b-107">SSL ストリームの状態。</span><span class="sxs-lookup"><span data-stu-id="56e3b-107">The state of the SSL stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="56e3b-108">解説</span><span class="sxs-lookup"><span data-stu-id="56e3b-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="56e3b-109">`TlsStream.m_Worker`フィールドはプライベートであり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="56e3b-109">The `TlsStream.m_Worker` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="56e3b-110">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのフィールドの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="56e3b-110">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="56e3b-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="56e3b-111">Requirements</span></span>

<span data-ttu-id="56e3b-112">**名前空間:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="56e3b-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="56e3b-113">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="56e3b-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="56e3b-114">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="56e3b-114">**.NET Framework versions:** Available since 2.0.</span></span>

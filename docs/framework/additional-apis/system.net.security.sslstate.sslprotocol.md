---
description: 詳細については、「Sslstate プロパティ」を参照してください。
title: SslState. Sslstate プロパティ (システム .Net. Security)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Security.SslState.SslProtocol
- System.Net.Security.SslState.get_SslProtocol
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: b0b9bebf23fcd8d643d06f1cff10c260c77a7c08
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699624"
---
# <a name="sslstatesslprotocol-property"></a><span data-ttu-id="725fb-103">SslState. Sslstate プロパティ</span><span class="sxs-lookup"><span data-stu-id="725fb-103">SslState.SslProtocol Property</span></span>

<span data-ttu-id="725fb-104">SSL プロトコルのバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="725fb-104">Gets the SSL protocol versions.</span></span>

## <a name="syntax"></a><span data-ttu-id="725fb-105">構文</span><span class="sxs-lookup"><span data-stu-id="725fb-105">Syntax</span></span>

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a><span data-ttu-id="725fb-106">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="725fb-106">Property value</span></span>

<xref:System.Security.Authentication.SslProtocols>  
<span data-ttu-id="725fb-107">SSL プロトコルのバージョンを指定する列挙値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="725fb-107">A bitwise combination of the enumeration values that specify the SSL protocol versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="725fb-108">解説</span><span class="sxs-lookup"><span data-stu-id="725fb-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="725fb-109">`SslState.SslProtocol`プロパティは内部であり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="725fb-109">The `SslState.SslProtocol` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="725fb-110">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="725fb-110">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="725fb-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="725fb-111">Requirements</span></span>

<span data-ttu-id="725fb-112">**名前空間:** <xref:System.Net.Security></span><span class="sxs-lookup"><span data-stu-id="725fb-112">**Namespace:** <xref:System.Net.Security></span></span>

<span data-ttu-id="725fb-113">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="725fb-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="725fb-114">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="725fb-114">**.NET Framework versions:** Available since 2.0.</span></span>

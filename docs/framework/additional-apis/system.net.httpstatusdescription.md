---
description: '詳細情報: HttpStatusDescription クラス'
title: HttpStatusDescription クラス (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fa135a6421397ce6b7be2af05d66aa8e81beafb7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802503"
---
# <a name="httpstatusdescription-class"></a><span data-ttu-id="55aed-103">HttpStatusDescription クラス</span><span class="sxs-lookup"><span data-stu-id="55aed-103">HttpStatusDescription class</span></span>

<span data-ttu-id="55aed-104">標準の HTTP 状態の説明を提供します。</span><span class="sxs-lookup"><span data-stu-id="55aed-104">Provides standard HTTP status descriptions.</span></span> <span data-ttu-id="55aed-105">このクラスは継承できません。</span><span class="sxs-lookup"><span data-stu-id="55aed-105">This class cannot be inherited.</span></span>

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> <span data-ttu-id="55aed-106">このクラスは内部的なものであり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="55aed-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="55aed-107">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのクラスの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="55aed-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="get-method"></a><span data-ttu-id="55aed-108">Get メソッド</span><span class="sxs-lookup"><span data-stu-id="55aed-108">Get method</span></span>

<span data-ttu-id="55aed-109">指定された HTTP ステータスコードに関連付けられている説明を返します。</span><span class="sxs-lookup"><span data-stu-id="55aed-109">Returns the description associated with the specified HTTP status code.</span></span>

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a><span data-ttu-id="55aed-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="55aed-110">Parameters</span></span>

<span data-ttu-id="55aed-111">`code` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="55aed-111">`code` <xref:System.Int32></span></span>

<span data-ttu-id="55aed-112">HTTP 状態コード (など) `404` 。</span><span class="sxs-lookup"><span data-stu-id="55aed-112">The HTTP status code, for example, `404`.</span></span>

### <a name="return-value"></a><span data-ttu-id="55aed-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="55aed-113">Return value</span></span>

<xref:System.String?displayProperty=nameWithType>

<span data-ttu-id="55aed-114">HTTP 状態の説明。</span><span class="sxs-lookup"><span data-stu-id="55aed-114">The HTTP status description.</span></span>

## <a name="requirements"></a><span data-ttu-id="55aed-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="55aed-115">Requirements</span></span>

<span data-ttu-id="55aed-116">**名前空間:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="55aed-116">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="55aed-117">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="55aed-117">**Assembly:** System (in System.dll)</span></span>

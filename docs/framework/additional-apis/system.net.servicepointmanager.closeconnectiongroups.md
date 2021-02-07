---
description: '詳細については、次を参照してください: ServicePointManager. CloseConnectionGroups メソッド'
title: ServicePointManager. CloseConnectionGroups メソッド (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.CloseConnectionGroups
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 8cd1a1f0f4dbdaeaee117e6a7ae4219680363a6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699559"
---
# <a name="servicepointmanagercloseconnectiongroups-method"></a><span data-ttu-id="04d25-103">ServicePointManager. CloseConnectionGroups メソッド</span><span class="sxs-lookup"><span data-stu-id="04d25-103">ServicePointManager.CloseConnectionGroups method</span></span>

<span data-ttu-id="04d25-104">すべてのサービスポイントを反復処理し、指定された名前の接続グループを閉じます。</span><span class="sxs-lookup"><span data-stu-id="04d25-104">Iterates through all service points and closes connection groups that have the specified name.</span></span>

```csharp
internal static void CloseConnectionGroups(string connectionGroupName)
```

> [!WARNING]
> <span data-ttu-id="04d25-105">このメソッドは内部であり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="04d25-105">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="04d25-106">Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="04d25-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="04d25-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="04d25-107">Parameters</span></span>

<span data-ttu-id="04d25-108">`connectionGroupName` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="04d25-108">`connectionGroupName` <xref:System.String></span></span>

<span data-ttu-id="04d25-109">閉じる接続グループの名前。</span><span class="sxs-lookup"><span data-stu-id="04d25-109">The name of the connection group to close.</span></span>

## <a name="requirements"></a><span data-ttu-id="04d25-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="04d25-110">Requirements</span></span>

<span data-ttu-id="04d25-111">**名前空間:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="04d25-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="04d25-112">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="04d25-112">**Assembly:** System (in System.dll)</span></span>

---
description: '詳細情報: ComNetOS クラス'
title: ComNetOS クラス (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ComNetOS
- System.Net.ComNetOS.IsWin7orLater
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 7376fe4a5e02818907cb71573451fffb3a3667cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802529"
---
# <a name="comnetos-class"></a><span data-ttu-id="c48d8-103">ComNetOS クラス</span><span class="sxs-lookup"><span data-stu-id="c48d8-103">ComNetOS class</span></span>

<span data-ttu-id="c48d8-104">バージョンやインストールの種類 (クライアントまたはサーバー) など、現在のオペレーティングシステムに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c48d8-104">Provides information about the current operating system, such as its version and installation type (client or server).</span></span> <span data-ttu-id="c48d8-105">このクラスは継承できません。</span><span class="sxs-lookup"><span data-stu-id="c48d8-105">This class cannot be inherited.</span></span>
  
```csharp  
internal static class ComNetOS
```

> [!WARNING]
> <span data-ttu-id="c48d8-106">このクラスは内部的なものであり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="c48d8-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="c48d8-107">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのクラスの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="c48d8-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="iswin7orlater-field"></a><span data-ttu-id="c48d8-108">IsWin7orLater フィールド</span><span class="sxs-lookup"><span data-stu-id="c48d8-108">IsWin7orLater field</span></span>

<span data-ttu-id="c48d8-109">オペレーティングシステムのバージョンが Windows 7 以降であるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c48d8-109">Specifies whether the operating system version is Windows 7 or later.</span></span>

```csharp
internal static readonly bool IsWin7orLater
```

## <a name="requirements"></a><span data-ttu-id="c48d8-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="c48d8-110">Requirements</span></span>

<span data-ttu-id="c48d8-111">**名前空間:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="c48d8-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="c48d8-112">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="c48d8-112">**Assembly:** System (in System.dll)</span></span>

---
description: 詳細については、「WebHeaderCollection. AddInternal メソッド」を参照してください。
title: WebHeaderCollection. AddInternal メソッド (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 7bc84f84e6656dba5230b627fe9decfc4e0b4746
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699481"
---
# <a name="webheadercollectionaddinternal-method"></a><span data-ttu-id="9cfb1-103">WebHeaderCollection. AddInternal メソッド</span><span class="sxs-lookup"><span data-stu-id="9cfb1-103">WebHeaderCollection.AddInternal method</span></span>

<span data-ttu-id="9cfb1-104">指定された名前と値を持つ新しいヘッダーをコレクションに追加し、チェックをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="9cfb1-104">Adds a new header with the specified name and value to the collection, bypassing checks.</span></span>

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> <span data-ttu-id="9cfb1-105">このメソッドは内部であり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="9cfb1-105">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="9cfb1-106">Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9cfb1-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="9cfb1-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9cfb1-107">Parameters</span></span>

- <span data-ttu-id="9cfb1-108">`name` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="9cfb1-108">`name` <xref:System.String></span></span>

  <span data-ttu-id="9cfb1-109">ヘッダーの名前。</span><span class="sxs-lookup"><span data-stu-id="9cfb1-109">The name of the header.</span></span>

- <span data-ttu-id="9cfb1-110">`value` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="9cfb1-110">`value` <xref:System.String></span></span>

  <span data-ttu-id="9cfb1-111">ヘッダーの値です。</span><span class="sxs-lookup"><span data-stu-id="9cfb1-111">The value of the header.</span></span>

## <a name="requirements"></a><span data-ttu-id="9cfb1-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="9cfb1-112">Requirements</span></span>

<span data-ttu-id="9cfb1-113">**名前空間:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="9cfb1-113">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="9cfb1-114">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="9cfb1-114">**Assembly:** System (in System.dll)</span></span>

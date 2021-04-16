---
description: '詳細情報: EnumImportTypes メソッド'
title: EnumImportTypes メソッド
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
ms.openlocfilehash: 39570740f3560f5bfef8ba80b95c0eb2aca41f59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638120"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="d87f0-103">EnumImportTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="d87f0-103">EnumImportTypes Method</span></span>

<span data-ttu-id="d87f0-104">各スコープ内の各型を列挙します。</span><span class="sxs-lookup"><span data-stu-id="d87f0-104">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="d87f0-105">構文</span><span class="sxs-lookup"><span data-stu-id="d87f0-105">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="d87f0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d87f0-106">Parameters</span></span>

`hEnum`\
<span data-ttu-id="d87f0-107">列挙子のハンドル。</span><span class="sxs-lookup"><span data-stu-id="d87f0-107">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="d87f0-108">取得する型の最大数。</span><span class="sxs-lookup"><span data-stu-id="d87f0-108">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="d87f0-109">型トークンを受け取ります (`dwMax` を超えることはできません)。</span><span class="sxs-lookup"><span data-stu-id="d87f0-109">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="d87f0-110">`aTypeDefs` 内の実際の型数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d87f0-110">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="d87f0-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="d87f0-111">Return Value</span></span>

<span data-ttu-id="d87f0-112">メソッドが成功した場合は、S_OK が返されます。</span><span class="sxs-lookup"><span data-stu-id="d87f0-112">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="d87f0-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="d87f0-113">Requirements</span></span>

<span data-ttu-id="d87f0-114">alink.h を必要とします</span><span class="sxs-lookup"><span data-stu-id="d87f0-114">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="d87f0-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d87f0-115">See also</span></span>

- [<span data-ttu-id="d87f0-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d87f0-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d87f0-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d87f0-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d87f0-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="d87f0-118">ALink API</span></span>](index.md)

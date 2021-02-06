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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638120"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="22113-103">EnumImportTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="22113-103">EnumImportTypes Method</span></span>

<span data-ttu-id="22113-104">各スコープ内の各型を列挙します。</span><span class="sxs-lookup"><span data-stu-id="22113-104">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="22113-105">構文</span><span class="sxs-lookup"><span data-stu-id="22113-105">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="22113-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="22113-106">Parameters</span></span>

`hEnum`\
<span data-ttu-id="22113-107">列挙子のハンドル。</span><span class="sxs-lookup"><span data-stu-id="22113-107">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="22113-108">取得する型の最大数。</span><span class="sxs-lookup"><span data-stu-id="22113-108">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="22113-109">は、を超えない型トークンを受け取り `dwMax` ます。</span><span class="sxs-lookup"><span data-stu-id="22113-109">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="22113-110">の実際の型数を受け取り `aTypeDefs` ます。</span><span class="sxs-lookup"><span data-stu-id="22113-110">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="22113-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="22113-111">Return Value</span></span>

<span data-ttu-id="22113-112">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="22113-112">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="22113-113">要件</span><span class="sxs-lookup"><span data-stu-id="22113-113">Requirements</span></span>

<span data-ttu-id="22113-114">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="22113-114">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="22113-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="22113-115">See also</span></span>

- [<span data-ttu-id="22113-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="22113-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="22113-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="22113-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="22113-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="22113-118">ALink API</span></span>](index.md)

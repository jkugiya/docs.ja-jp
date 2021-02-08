---
description: '詳細については、次を参照してください: CorDebugEHClause 構造体'
title: CorDebugEHClause 構造体
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
ms.openlocfilehash: ecb00e2a110719ab82de32fb1f1c861e2033a528
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801671"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="4f8fd-103">CorDebugEHClause 構造体</span><span class="sxs-lookup"><span data-stu-id="4f8fd-103">CorDebugEHClause Structure</span></span>

<span data-ttu-id="4f8fd-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="4f8fd-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4f8fd-105">中間言語 (IL) コードの特定の部分の例外処理 (EH) 句を表しています。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-105">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f8fd-106">構文</span><span class="sxs-lookup"><span data-stu-id="4f8fd-106">Syntax</span></span>  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a><span data-ttu-id="4f8fd-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="4f8fd-107">Members</span></span>  
  
|<span data-ttu-id="4f8fd-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="4f8fd-108">Member</span></span>|<span data-ttu-id="4f8fd-109">説明</span><span class="sxs-lookup"><span data-stu-id="4f8fd-109">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="4f8fd-110">EH 句の例外情報について説明しているビット フィールド。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-110">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="4f8fd-111">詳細については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-111">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="4f8fd-112">メソッド本体の先頭からの `try` ブロックのオフセット (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-112">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="4f8fd-113">`try` ブロックの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-113">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="4f8fd-114">この `try` ブロックのハンドラーの場所。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-114">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="4f8fd-115">ハンドラー コードのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-115">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="4f8fd-116">型に基づく例外ハンドラーのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-116">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="4f8fd-117">フィルターに基づく例外ハンドラーのメソッド本体の先頭からのオフセット (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-117">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f8fd-118">解説</span><span class="sxs-lookup"><span data-stu-id="4f8fd-118">Remarks</span></span>  

 <span data-ttu-id="4f8fd-119">値の配列 `CoreDebugEHClause` は、 [GetEHClauses](icordebugilcode-getehclauses-method.md) メソッドによって返されます。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-119">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="4f8fd-120">EH 句の情報は CLI 仕様によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-120">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="4f8fd-121">詳細については、「 [STANDARD ECMA-355: 共通言語基盤 (CLI)、第6版](https://www.ecma-international.org/publications/standards/Ecma-335.htm)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-121">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="4f8fd-122">`flags` フィールドには、次のフラグを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-122">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="4f8fd-123">これらは、CorDebug.idl または CorDebug.h に定義されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-123">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="4f8fd-124">フラグ</span><span class="sxs-lookup"><span data-stu-id="4f8fd-124">Flag</span></span>|<span data-ttu-id="4f8fd-125">値</span><span class="sxs-lookup"><span data-stu-id="4f8fd-125">Value</span></span>|<span data-ttu-id="4f8fd-126">説明</span><span class="sxs-lookup"><span data-stu-id="4f8fd-126">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="4f8fd-127">0x00000000</span><span class="sxs-lookup"><span data-stu-id="4f8fd-127">0x00000000</span></span>|<span data-ttu-id="4f8fd-128">入力された例外句。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-128">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="4f8fd-129">0x00000001</span><span class="sxs-lookup"><span data-stu-id="4f8fd-129">0x00000001</span></span>|<span data-ttu-id="4f8fd-130">例外フィルターおよびハンドラー句。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-130">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="4f8fd-131">0x00000002</span><span class="sxs-lookup"><span data-stu-id="4f8fd-131">0x00000002</span></span>|<span data-ttu-id="4f8fd-132">`finally` 句。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-132">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="4f8fd-133">0x00000004</span><span class="sxs-lookup"><span data-stu-id="4f8fd-133">0x00000004</span></span>|<span data-ttu-id="4f8fd-134">fault 句 (例外がスローされた場合にのみ `finally` 句が呼び出される)。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-134">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f8fd-135">要件</span><span class="sxs-lookup"><span data-stu-id="4f8fd-135">Requirements</span></span>  

 <span data-ttu-id="4f8fd-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f8fd-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f8fd-137">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f8fd-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f8fd-138">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f8fd-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f8fd-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f8fd-139">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f8fd-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f8fd-140">See also</span></span>

- [<span data-ttu-id="4f8fd-141">GetEHClauses メソッド</span><span class="sxs-lookup"><span data-stu-id="4f8fd-141">GetEHClauses Method</span></span>](icordebugilcode-getehclauses-method.md)
- [<span data-ttu-id="4f8fd-142">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="4f8fd-142">Debugging Structures</span></span>](debugging-structures.md)

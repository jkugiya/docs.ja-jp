---
description: CreateAssemblyEnum 関数の詳細について説明します。
title: CreateAssemblyEnum 関数
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
ms.openlocfilehash: 47177fcf0cd9e1b492fa89b9fb80c5cdaaced689
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761142"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="1e1a4-103">CreateAssemblyEnum 関数</span><span class="sxs-lookup"><span data-stu-id="1e1a4-103">CreateAssemblyEnum Function</span></span>

<span data-ttu-id="1e1a4-104">指定された[IAssemblyName](iassemblyname-interface.md)を持つアセンブリ内のオブジェクトを列挙できる[iassemblyenum](iassemblyenum-interface.md)インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="1e1a4-104">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e1a4-105">構文</span><span class="sxs-lookup"><span data-stu-id="1e1a4-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e1a4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e1a4-106">Parameters</span></span>  

 `pEnum`  
 <span data-ttu-id="1e1a4-107">入出力要求されたポインターを格納しているメモリ位置へのポインター `IAssemblyEnum` 。</span><span class="sxs-lookup"><span data-stu-id="1e1a4-107">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="1e1a4-108">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="1e1a4-108">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="1e1a4-109">`pUnkReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e1a4-109">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="1e1a4-110">から `IAssemblyName` 要求されたアセンブリの。</span><span class="sxs-lookup"><span data-stu-id="1e1a4-110">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="1e1a4-111">この名前は、列挙をフィルター処理するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e1a4-111">This name is used to filter the enumeration.</span></span> <span data-ttu-id="1e1a4-112">グローバルアセンブリキャッシュ内のすべてのアセンブリを列挙するには null を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1e1a4-112">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1e1a4-113">から列挙子の動作を変更するためのフラグ。</span><span class="sxs-lookup"><span data-stu-id="1e1a4-113">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="1e1a4-114">このパラメーターには、 [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) 列挙体とのビットが1つだけ含まれます。</span><span class="sxs-lookup"><span data-stu-id="1e1a4-114">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="1e1a4-115">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="1e1a4-115">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="1e1a4-116">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e1a4-116">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e1a4-117">解説</span><span class="sxs-lookup"><span data-stu-id="1e1a4-117">Remarks</span></span>  

 <span data-ttu-id="1e1a4-118">パラメーターには `dwFlags` 、列挙体のビットが1つだけ含まれ `ASM_CACHE_FLAGS` ます。</span><span class="sxs-lookup"><span data-stu-id="1e1a4-118">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e1a4-119">要件</span><span class="sxs-lookup"><span data-stu-id="1e1a4-119">Requirements</span></span>  

 <span data-ttu-id="1e1a4-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e1a4-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e1a4-121">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="1e1a4-121">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1e1a4-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1e1a4-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e1a4-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e1a4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e1a4-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e1a4-124">See also</span></span>

- [<span data-ttu-id="1e1a4-125">IAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e1a4-125">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
- [<span data-ttu-id="1e1a4-126">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e1a4-126">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="1e1a4-127">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="1e1a4-127">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)

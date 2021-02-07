---
description: '詳細について: ICLRDataTarget2:: AllocVirtual Method'
title: ICLRDataTarget2::AllocVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
ms.openlocfilehash: d81474e4067599178285b6fa876919298617919d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729342"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="ee5ce-103">ICLRDataTarget2::AllocVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="ee5ce-103">ICLRDataTarget2::AllocVirtual Method</span></span>

<span data-ttu-id="ee5ce-104">このターゲットプロセスのアドレス空間にメモリを割り当てるために、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ee5ce-104">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee5ce-105">構文</span><span class="sxs-lookup"><span data-stu-id="ee5ce-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee5ce-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ee5ce-106">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="ee5ce-107">から `CLRDATA_ADDRESS` 割り当てられるメモリの、要求された開始アドレスを示す値です。</span><span class="sxs-lookup"><span data-stu-id="ee5ce-107">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="ee5ce-108">から割り当てるメモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="ee5ce-108">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="ee5ce-109">からメモリの割り当てを制御するフラグ。</span><span class="sxs-lookup"><span data-stu-id="ee5ce-109">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="ee5ce-110">Win32 関数を参照してください `VirtualAlloc` 。</span><span class="sxs-lookup"><span data-stu-id="ee5ce-110">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="ee5ce-111">から割り当てられたメモリの保護属性。</span><span class="sxs-lookup"><span data-stu-id="ee5ce-111">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="ee5ce-112">Win32 関数を参照してください `VirtualAlloc` 。</span><span class="sxs-lookup"><span data-stu-id="ee5ce-112">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="ee5ce-113">入出力割り当てられた `CLRDATA_ADDRESS` メモリの実際の開始アドレスを指定する値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ee5ce-113">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee5ce-114">解説</span><span class="sxs-lookup"><span data-stu-id="ee5ce-114">Remarks</span></span>  

 <span data-ttu-id="ee5ce-115">この `AllocVirtual` メソッドは、Win32 関数の論理ラッパーとして機能し `VirtualAlloc` ます。</span><span class="sxs-lookup"><span data-stu-id="ee5ce-115">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="ee5ce-116">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="ee5ce-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee5ce-117">要件</span><span class="sxs-lookup"><span data-stu-id="ee5ce-117">Requirements</span></span>  

 <span data-ttu-id="ee5ce-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee5ce-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee5ce-119">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="ee5ce-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ee5ce-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee5ce-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee5ce-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee5ce-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee5ce-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee5ce-122">See also</span></span>

- [<span data-ttu-id="ee5ce-123">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee5ce-123">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="ee5ce-124">FreeVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="ee5ce-124">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)

---
description: '詳細について: ICLRDataTarget2:: FreeVirtual メソッド'
title: ICLRDataTarget2::FreeVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
ms.openlocfilehash: ef4048f421fcdc7d284663036f8cc9f2614f4e13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729251"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="f5bea-103">ICLRDataTarget2::FreeVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="f5bea-103">ICLRDataTarget2::FreeVirtual Method</span></span>

<span data-ttu-id="f5bea-104">ターゲットプロセスのアドレス空間で以前に割り当てられたメモリを解放するために、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f5bea-104">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5bea-105">構文</span><span class="sxs-lookup"><span data-stu-id="f5bea-105">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5bea-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f5bea-106">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="f5bea-107">から `CLRDATA_ADDRESS` 解放されるメモリの開始アドレスを指定する値。</span><span class="sxs-lookup"><span data-stu-id="f5bea-107">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="f5bea-108">から解放されるメモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="f5bea-108">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="f5bea-109">からメモリの解放を制御するフラグ。</span><span class="sxs-lookup"><span data-stu-id="f5bea-109">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="f5bea-110">Win32 関数を参照してください `VirtualFree` 。</span><span class="sxs-lookup"><span data-stu-id="f5bea-110">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5bea-111">解説</span><span class="sxs-lookup"><span data-stu-id="f5bea-111">Remarks</span></span>  

 <span data-ttu-id="f5bea-112">この `FreeVirtual` メソッドは、Win32 関数の論理ラッパーとして機能し `VirtualFree` ます。</span><span class="sxs-lookup"><span data-stu-id="f5bea-112">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="f5bea-113">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="f5bea-113">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5bea-114">要件</span><span class="sxs-lookup"><span data-stu-id="f5bea-114">Requirements</span></span>  

 <span data-ttu-id="f5bea-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5bea-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5bea-116">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="f5bea-116">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f5bea-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5bea-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5bea-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5bea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5bea-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5bea-119">See also</span></span>

- [<span data-ttu-id="f5bea-120">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5bea-120">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="f5bea-121">AllocVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="f5bea-121">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)

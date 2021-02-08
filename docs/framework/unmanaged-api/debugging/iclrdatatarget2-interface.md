---
description: 詳細については、「ICLRDataTarget2 インターフェイス」を参照してください。
title: ICLRDataTarget2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
ms.openlocfilehash: 9ba6d11ea043d3b6ba85544b47e063f585854af8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794846"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="dd8fb-103">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd8fb-103">ICLRDataTarget2 Interface</span></span>

<span data-ttu-id="dd8fb-104">ターゲットプロセスの仮想メモリ領域を操作するためにデータアクセスサービス層によって使用される [ICLRDataTarget](iclrdatatarget-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="dd8fb-104">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd8fb-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dd8fb-105">Methods</span></span>  
  
|<span data-ttu-id="dd8fb-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="dd8fb-106">Method</span></span>|<span data-ttu-id="dd8fb-107">説明</span><span class="sxs-lookup"><span data-stu-id="dd8fb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dd8fb-108">AllocVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="dd8fb-108">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="dd8fb-109">ターゲットプロセスのアドレス空間にメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="dd8fb-109">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="dd8fb-110">FreeVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="dd8fb-110">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="dd8fb-111">ターゲットプロセスのアドレス空間で以前に割り当てられたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="dd8fb-111">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd8fb-112">解説</span><span class="sxs-lookup"><span data-stu-id="dd8fb-112">Remarks</span></span>  

 <span data-ttu-id="dd8fb-113">API クライアント (つまりデバッガー) は、特定のターゲット プロセスに応じてこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd8fb-113">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="dd8fb-114">たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。</span><span class="sxs-lookup"><span data-stu-id="dd8fb-114">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="dd8fb-115">ターゲットは、メモリ領域の変更をサポートしない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dd8fb-115">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd8fb-116">要件</span><span class="sxs-lookup"><span data-stu-id="dd8fb-116">Requirements</span></span>  

 <span data-ttu-id="dd8fb-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd8fb-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd8fb-118">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="dd8fb-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="dd8fb-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd8fb-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd8fb-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd8fb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8fb-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd8fb-121">See also</span></span>

- [<span data-ttu-id="dd8fb-122">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd8fb-122">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="dd8fb-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd8fb-123">Debugging Interfaces</span></span>](debugging-interfaces.md)

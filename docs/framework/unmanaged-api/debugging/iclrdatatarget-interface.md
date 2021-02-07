---
description: 詳細については、「ICLRDataTarget インターフェイス」を参照してください。
title: ICLRDataTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
ms.openlocfilehash: f24760f638705a1bde7e055069cbc3a18a0896fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738222"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="8c302-103">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c302-103">ICLRDataTarget Interface</span></span>

<span data-ttu-id="8c302-104">共通言語ランタイム (CLR) のターゲット項目と対話するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8c302-104">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c302-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8c302-105">Methods</span></span>  
  
|<span data-ttu-id="8c302-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8c302-106">Method</span></span>|<span data-ttu-id="8c302-107">説明</span><span class="sxs-lookup"><span data-stu-id="8c302-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c302-108">GetCurrentThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="8c302-108">GetCurrentThreadID Method</span></span>](iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="8c302-109">現在のスレッドのオペレーティングシステム id を取得します。</span><span class="sxs-lookup"><span data-stu-id="8c302-109">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="8c302-110">GetImageBase メソッド</span><span class="sxs-lookup"><span data-stu-id="8c302-110">GetImageBase Method</span></span>](iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="8c302-111">指定したイメージのベースメモリアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="8c302-111">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="8c302-112">GetMachineType メソッド</span><span class="sxs-lookup"><span data-stu-id="8c302-112">GetMachineType Method</span></span>](iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="8c302-113">ターゲットプロセスが使用している命令セットの種類の識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8c302-113">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="8c302-114">GetPointerSize メソッド</span><span class="sxs-lookup"><span data-stu-id="8c302-114">GetPointerSize Method</span></span>](iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="8c302-115">現在のターゲットへのポインターのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="8c302-115">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="8c302-116">GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="8c302-116">GetThreadContext Method</span></span>](iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="8c302-117">指定した識別子を持つスレッドのコンテキストへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="8c302-117">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="8c302-118">GetTLSValue メソッド</span><span class="sxs-lookup"><span data-stu-id="8c302-118">GetTLSValue Method</span></span>](iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="8c302-119">指定したスレッドの指定したインデックスにあるスレッドローカルストレージ (TLS) の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="8c302-119">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="8c302-120">ReadVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="8c302-120">ReadVirtual Method</span></span>](iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="8c302-121">指定された仮想メモリアドレスから指定されたバッファーにデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="8c302-121">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="8c302-122">Request Method (要求メソッド)</span><span class="sxs-lookup"><span data-stu-id="8c302-122">Request Method</span></span>](iclrdatatarget-request-method.md)|<span data-ttu-id="8c302-123">実装で定義されているように、操作を要求するために、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8c302-123">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="8c302-124">SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="8c302-124">SetThreadContext Method</span></span>](iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="8c302-125">ターゲットプロセス内の指定されたスレッドの現在のコンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="8c302-125">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="8c302-126">SetTLSValue メソッド</span><span class="sxs-lookup"><span data-stu-id="8c302-126">SetTLSValue Method</span></span>](iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="8c302-127">ターゲットプロセス内の指定したスレッドのスレッドローカルストレージ (TLS) の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="8c302-127">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="8c302-128">WriteVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="8c302-128">WriteVirtual Method</span></span>](iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="8c302-129">指定されたバッファーから指定された仮想メモリアドレスにデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="8c302-129">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c302-130">解説</span><span class="sxs-lookup"><span data-stu-id="8c302-130">Remarks</span></span>  

 <span data-ttu-id="8c302-131">API クライアント (つまり、デバッガー) は、特定のターゲット項目に適した方法でこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c302-131">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="8c302-132">たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。</span><span class="sxs-lookup"><span data-stu-id="8c302-132">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c302-133">要件</span><span class="sxs-lookup"><span data-stu-id="8c302-133">Requirements</span></span>  

 <span data-ttu-id="8c302-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c302-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c302-135">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="8c302-135">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8c302-136">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c302-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c302-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c302-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c302-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c302-138">See also</span></span>

- [<span data-ttu-id="8c302-139">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c302-139">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="8c302-140">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c302-140">Debugging Interfaces</span></span>](debugging-interfaces.md)

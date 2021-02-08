---
description: 詳細については、「ICLRDataTarget3 インターフェイス」を参照してください。
title: ICLRDataTarget3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
ms.openlocfilehash: deea609298563e60897f9bedab9fb1e175dc7b73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794790"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="a383d-103">ICLRDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a383d-103">ICLRDataTarget3 Interface</span></span>

<span data-ttu-id="a383d-104">例外情報へのアクセスを提供する [ICLRDataTarget2](iclrdatatarget2-interface.md) のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="a383d-104">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a383d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a383d-105">Methods</span></span>  
  
|<span data-ttu-id="a383d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a383d-106">Method</span></span>|<span data-ttu-id="a383d-107">説明</span><span class="sxs-lookup"><span data-stu-id="a383d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a383d-108">GetExceptionRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="a383d-108">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="a383d-109">ターゲット プロセスに関連付けられた例外レコードを取得するために、共通言語ランタイム (CLR: Common Language Runtime) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a383d-109">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="a383d-110">GetExceptionContextRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="a383d-110">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="a383d-111">ターゲット プロセスに関連付けられているコンテキスト レコードを取得するために、CLR データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a383d-111">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="a383d-112">GetExceptionThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="a383d-112">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="a383d-113">例外をスローしたスレッドの ID を取得するために、CLR データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a383d-113">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a383d-114">解説</span><span class="sxs-lookup"><span data-stu-id="a383d-114">Remarks</span></span>  

 <span data-ttu-id="a383d-115">API クライアント (つまりデバッガー) は、特定のターゲット プロセスに応じてこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a383d-115">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="a383d-116">たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。</span><span class="sxs-lookup"><span data-stu-id="a383d-116">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="a383d-117">ターゲットは、メモリ領域の変更をサポートしない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a383d-117">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a383d-118">要件</span><span class="sxs-lookup"><span data-stu-id="a383d-118">Requirements</span></span>  

 <span data-ttu-id="a383d-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a383d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a383d-120">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="a383d-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a383d-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a383d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a383d-122">**.NET Framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a383d-122">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a383d-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a383d-123">See also</span></span>

- [<span data-ttu-id="a383d-124">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a383d-124">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="a383d-125">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a383d-125">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="a383d-126">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a383d-126">Debugging Interfaces</span></span>](debugging-interfaces.md)

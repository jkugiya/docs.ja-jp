---
description: '詳細について: ICLRDataTarget:: SetTLSValue メソッド'
title: ICLRDataTarget::SetTLSValue メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type:
- apiref
ms.openlocfilehash: 2432cd66f604575e35f171c98a0fb313c5ccd94e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785684"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="1a42e-103">ICLRDataTarget::SetTLSValue メソッド</span><span class="sxs-lookup"><span data-stu-id="1a42e-103">ICLRDataTarget::SetTLSValue Method</span></span>

<span data-ttu-id="1a42e-104">ターゲットプロセス内の指定したスレッドのスレッドローカルストレージ (TLS) の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1a42e-104">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="1a42e-105">このメソッドは、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1a42e-105">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a42e-106">構文</span><span class="sxs-lookup"><span data-stu-id="1a42e-106">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a42e-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1a42e-107">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="1a42e-108">からターゲットプロセス内のスレッドのオペレーティングシステム識別子。</span><span class="sxs-lookup"><span data-stu-id="1a42e-108">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="1a42e-109">から位置のインデックス。</span><span class="sxs-lookup"><span data-stu-id="1a42e-109">[in] The index of the location.</span></span> <span data-ttu-id="1a42e-110">この値は、指定されたスレッドのローカルストア内の有効なインデックスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a42e-110">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="1a42e-111">から `CLRDATA_ADDRESS` 指定された TLS の場所に格納する値を指定する値。</span><span class="sxs-lookup"><span data-stu-id="1a42e-111">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a42e-112">解説</span><span class="sxs-lookup"><span data-stu-id="1a42e-112">Remarks</span></span>  

 <span data-ttu-id="1a42e-113">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="1a42e-113">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a42e-114">要件</span><span class="sxs-lookup"><span data-stu-id="1a42e-114">Requirements</span></span>  

 <span data-ttu-id="1a42e-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a42e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a42e-116">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="1a42e-116">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="1a42e-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a42e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a42e-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a42e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a42e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a42e-119">See also</span></span>

- [<span data-ttu-id="1a42e-120">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a42e-120">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)

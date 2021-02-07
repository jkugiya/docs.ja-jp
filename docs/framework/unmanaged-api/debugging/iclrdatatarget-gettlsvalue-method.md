---
description: '詳細について: ICLRDataTarget:: GetTLSValue メソッド'
title: ICLRDataTarget::GetTLSValue メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
ms.openlocfilehash: 5c0c4a462d89c2eceada4180ea532f36fc9e48b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718045"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="c1fc8-103">ICLRDataTarget::GetTLSValue メソッド</span><span class="sxs-lookup"><span data-stu-id="c1fc8-103">ICLRDataTarget::GetTLSValue Method</span></span>

<span data-ttu-id="c1fc8-104">ターゲットプロセス内の指定したスレッドのスレッドローカルストレージ (TLS) から値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-104">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="c1fc8-105">このメソッドは、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-105">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1fc8-106">構文</span><span class="sxs-lookup"><span data-stu-id="c1fc8-106">Syntax</span></span>  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1fc8-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c1fc8-107">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="c1fc8-108">からターゲットプロセス内のスレッドのオペレーティングシステム識別子。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-108">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="c1fc8-109">から位置のインデックス。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-109">[in] The index of the location.</span></span> <span data-ttu-id="c1fc8-110">この値は、指定されたスレッドのローカルストア内の有効なインデックスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-110">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="c1fc8-111">入出力指定された `CLRDATA_ADDRESS` TLS の場所から返される値を指定する値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-111">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1fc8-112">解説</span><span class="sxs-lookup"><span data-stu-id="c1fc8-112">Remarks</span></span>  

 <span data-ttu-id="c1fc8-113">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-113">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1fc8-114">要件</span><span class="sxs-lookup"><span data-stu-id="c1fc8-114">Requirements</span></span>  

 <span data-ttu-id="c1fc8-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1fc8-116">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="c1fc8-116">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c1fc8-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1fc8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1fc8-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1fc8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1fc8-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1fc8-119">See also</span></span>

- [<span data-ttu-id="c1fc8-120">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1fc8-120">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)

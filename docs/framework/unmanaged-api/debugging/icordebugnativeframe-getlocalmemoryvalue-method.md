---
description: 詳細については、次の情報を参照してください:、テキストの表示方法
title: ICorDebugNativeFrame::GetLocalMemoryValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
ms.openlocfilehash: 5fbdf9474ca8c5849b7d917ecddff491b329113b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729238"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="b7a0b-103">ICorDebugNativeFrame::GetLocalMemoryValue メソッド</span><span class="sxs-lookup"><span data-stu-id="b7a0b-103">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>

<span data-ttu-id="b7a0b-104">このネイティブフレームの指定したメモリ位置に格納されている引数またはローカル変数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b7a0b-104">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a0b-105">構文</span><span class="sxs-lookup"><span data-stu-id="b7a0b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7a0b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b7a0b-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="b7a0b-107">から値を格納して `CORDB_ADDRESS` いるメモリ位置を指定する値。</span><span class="sxs-lookup"><span data-stu-id="b7a0b-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b7a0b-108">からパラメーターによって参照されるバイナリメタデータシグネチャのサイズを指定する整数 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="b7a0b-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b7a0b-109">から `PCCOR_SIGNATURE` 値の型のバイナリメタデータシグネチャを指す値。</span><span class="sxs-lookup"><span data-stu-id="b7a0b-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b7a0b-110">入出力指定されたメモリ位置に格納されている取得値を表す "ICorDebugValue" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b7a0b-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7a0b-111">要件</span><span class="sxs-lookup"><span data-stu-id="b7a0b-111">Requirements</span></span>  

 <span data-ttu-id="b7a0b-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7a0b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7a0b-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7a0b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7a0b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7a0b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7a0b-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7a0b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a0b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7a0b-116">See also</span></span>

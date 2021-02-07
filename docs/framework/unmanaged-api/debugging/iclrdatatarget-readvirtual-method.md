---
description: '詳細について: ICLRDataTarget:: ReadVirtual メソッド'
title: ICLRDataTarget::ReadVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.ReadVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type:
- apiref
ms.openlocfilehash: 740a89c95092cfad7974d6bc708c5d8b0d2a9172
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738202"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="9a28b-103">ICLRDataTarget::ReadVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="9a28b-103">ICLRDataTarget::ReadVirtual Method</span></span>

<span data-ttu-id="9a28b-104">指定された仮想メモリアドレスから指定されたバッファーにデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="9a28b-104">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a28b-105">構文</span><span class="sxs-lookup"><span data-stu-id="9a28b-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a28b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a28b-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="9a28b-107">から仮想メモリアドレスを格納する CLRDATA_ADDRESS。</span><span class="sxs-lookup"><span data-stu-id="9a28b-107">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="9a28b-108">入出力データを受け取るバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9a28b-108">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="9a28b-109">からバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="9a28b-109">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="9a28b-110">入出力返されたバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9a28b-110">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a28b-111">要件</span><span class="sxs-lookup"><span data-stu-id="9a28b-111">Requirements</span></span>  

 <span data-ttu-id="9a28b-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a28b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a28b-113">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="9a28b-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9a28b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a28b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a28b-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a28b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a28b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a28b-116">See also</span></span>

- [<span data-ttu-id="9a28b-117">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a28b-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)

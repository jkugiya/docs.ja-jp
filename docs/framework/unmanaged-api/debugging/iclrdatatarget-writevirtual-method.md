---
description: '詳細について: ICLRDataTarget:: WriteVirtual メソッド'
title: ICLRDataTarget::WriteVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
ms.openlocfilehash: 29ff8d629c5797099dab155802fff99786f4ce15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794859"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="628bc-103">ICLRDataTarget::WriteVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="628bc-103">ICLRDataTarget::WriteVirtual Method</span></span>

<span data-ttu-id="628bc-104">指定されたバッファーから指定された仮想メモリアドレスにデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="628bc-104">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="628bc-105">構文</span><span class="sxs-lookup"><span data-stu-id="628bc-105">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="628bc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="628bc-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="628bc-107">から仮想メモリアドレスを格納する CLRDATA_ADDRESS。</span><span class="sxs-lookup"><span data-stu-id="628bc-107">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="628bc-108">から書き込まれるデータを格納するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="628bc-108">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="628bc-109">から書き込むバイト数。</span><span class="sxs-lookup"><span data-stu-id="628bc-109">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="628bc-110">入出力書き込まれた実際のバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="628bc-110">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="628bc-111">要件</span><span class="sxs-lookup"><span data-stu-id="628bc-111">Requirements</span></span>  

 <span data-ttu-id="628bc-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="628bc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="628bc-113">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="628bc-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="628bc-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="628bc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="628bc-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="628bc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="628bc-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="628bc-116">See also</span></span>

- [<span data-ttu-id="628bc-117">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="628bc-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)

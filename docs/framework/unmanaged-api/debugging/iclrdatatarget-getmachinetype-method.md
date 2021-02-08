---
description: '詳細について: ICLRDataTarget:: GetMachineType メソッド'
title: ICLRDataTarget::GetMachineType メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetMachineType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type:
- apiref
ms.openlocfilehash: 5624f734a77f51b4ea6cd9dd0c9df393c72e7d26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801346"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="9779f-103">ICLRDataTarget::GetMachineType メソッド</span><span class="sxs-lookup"><span data-stu-id="9779f-103">ICLRDataTarget::GetMachineType Method</span></span>

<span data-ttu-id="9779f-104">ターゲットプロセスが使用している命令セットの種類の識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="9779f-104">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9779f-105">構文</span><span class="sxs-lookup"><span data-stu-id="9779f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9779f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9779f-106">Parameters</span></span>  

 `machineType`  
 <span data-ttu-id="9779f-107">入出力ターゲットプロセスが使用している命令セットを示す値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9779f-107">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="9779f-108">返されるは、 `machineType` winnt.h ヘッダーファイルで定義されている IMAGE_FILE_MACHINE 定数の1つです。</span><span class="sxs-lookup"><span data-stu-id="9779f-108">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9779f-109">要件</span><span class="sxs-lookup"><span data-stu-id="9779f-109">Requirements</span></span>  

 <span data-ttu-id="9779f-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9779f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9779f-111">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="9779f-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9779f-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9779f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9779f-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9779f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9779f-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9779f-114">See also</span></span>

- [<span data-ttu-id="9779f-115">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9779f-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)

---
description: '詳細について: ICorDebugMergedAssemblyRecord:: GetPublicKey メソッド'
title: ICorDebugMergedAssemblyRecord::GetPublicKey メソッド
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 15175b0d02773bcbce46bfaec9ce1de3021b7dde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801099"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="611b6-103">ICorDebugMergedAssemblyRecord::GetPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="611b6-103">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>

<span data-ttu-id="611b6-104">アセンブリの公開キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="611b6-104">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="611b6-105">構文</span><span class="sxs-lookup"><span data-stu-id="611b6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="611b6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="611b6-106">Parameters</span></span>  

 `cbPublicKey`  
 <span data-ttu-id="611b6-107">[in] `pbPublicKey` 配列の最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="611b6-107">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="611b6-108">[out] `pbPublicKey` 配列への実際の書き込みバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="611b6-108">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="611b6-109">[out] アセンブリの公開キーを含むバイト配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="611b6-109">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="611b6-110">解説</span><span class="sxs-lookup"><span data-stu-id="611b6-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="611b6-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="611b6-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="611b6-112">要件</span><span class="sxs-lookup"><span data-stu-id="611b6-112">Requirements</span></span>  

 <span data-ttu-id="611b6-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="611b6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="611b6-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="611b6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="611b6-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="611b6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="611b6-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="611b6-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="611b6-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="611b6-117">See also</span></span>

- [<span data-ttu-id="611b6-118">ICorDebugMergedAssemblyRecord インターフェイス</span><span class="sxs-lookup"><span data-stu-id="611b6-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="611b6-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="611b6-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

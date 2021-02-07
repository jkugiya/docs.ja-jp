---
description: '詳細について: ICorDebugDataTarget2:: GetImageFromPointer メソッド'
title: ICorDebugDataTarget2::GetImageFromPointer メソッド
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: bcf73fa522072707a7b08d90965fcd38188c2bb5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764399"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="7dd44-103">ICorDebugDataTarget2::GetImageFromPointer メソッド</span><span class="sxs-lookup"><span data-stu-id="7dd44-103">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>

<span data-ttu-id="7dd44-104">モジュールのアドレスから、そのモジュールのベース アドレスとサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="7dd44-104">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dd44-105">構文</span><span class="sxs-lookup"><span data-stu-id="7dd44-105">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dd44-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7dd44-106">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="7dd44-107">モジュール内のアドレスを表す [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) 値。</span><span class="sxs-lookup"><span data-stu-id="7dd44-107">A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="7dd44-108">入出力モジュールのベースアドレスを表す [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) 値。</span><span class="sxs-lookup"><span data-stu-id="7dd44-108">[out] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="7dd44-109">モジュールのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7dd44-109">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dd44-110">解説</span><span class="sxs-lookup"><span data-stu-id="7dd44-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7dd44-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7dd44-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dd44-112">要件</span><span class="sxs-lookup"><span data-stu-id="7dd44-112">Requirements</span></span>  

 <span data-ttu-id="7dd44-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7dd44-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dd44-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7dd44-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7dd44-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7dd44-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7dd44-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dd44-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd44-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7dd44-117">See also</span></span>

- [<span data-ttu-id="7dd44-118">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7dd44-118">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="7dd44-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7dd44-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

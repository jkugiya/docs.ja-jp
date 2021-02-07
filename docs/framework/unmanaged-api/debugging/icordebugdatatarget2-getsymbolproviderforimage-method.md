---
description: '詳細については、次を参照してください: ICorDebugDataTarget2:: Getシンボル Providerforimage メソッド'
title: ICorDebugDataTarget2::GetSymbolProviderForImage メソッド
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 7b4493b6c0959dc39d955d7691a22ac6905034b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764386"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="47f11-103">ICorDebugDataTarget2::GetSymbolProviderForImage メソッド</span><span class="sxs-lookup"><span data-stu-id="47f11-103">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>

<span data-ttu-id="47f11-104">モジュールのベース アドレスからそのモジュールのシンボル プロバイダーを返します。</span><span class="sxs-lookup"><span data-stu-id="47f11-104">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47f11-105">構文</span><span class="sxs-lookup"><span data-stu-id="47f11-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47f11-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="47f11-106">Parameters</span></span>  

 `imageBaseAddress`  
 <span data-ttu-id="47f11-107">からモジュールのベースアドレスを表す [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) 値。</span><span class="sxs-lookup"><span data-stu-id="47f11-107">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="47f11-108">入出力ツール [プロバイダー](icordebugsymbolprovider-interface.md) オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="47f11-108">[out] A pointer to the address of an [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47f11-109">解説</span><span class="sxs-lookup"><span data-stu-id="47f11-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47f11-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="47f11-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47f11-111">要件</span><span class="sxs-lookup"><span data-stu-id="47f11-111">Requirements</span></span>  

 <span data-ttu-id="47f11-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47f11-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47f11-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47f11-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47f11-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47f11-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47f11-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47f11-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f11-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="47f11-116">See also</span></span>

- [<span data-ttu-id="47f11-117">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47f11-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="47f11-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="47f11-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

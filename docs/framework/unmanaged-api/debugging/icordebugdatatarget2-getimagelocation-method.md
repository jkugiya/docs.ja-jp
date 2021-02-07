---
description: '詳細について: ICorDebugDataTarget2:: GetImageLocation メソッド'
title: ICorDebugDataTarget2::GetImageLocation メソッド
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: f79ba89d3ba467c2e81224d64147c2b5dd5db079
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710492"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="eb527-103">ICorDebugDataTarget2::GetImageLocation メソッド</span><span class="sxs-lookup"><span data-stu-id="eb527-103">ICorDebugDataTarget2::GetImageLocation Method</span></span>

<span data-ttu-id="eb527-104">モジュールのベース アドレスからモジュールのパスを返します。</span><span class="sxs-lookup"><span data-stu-id="eb527-104">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb527-105">構文</span><span class="sxs-lookup"><span data-stu-id="eb527-105">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb527-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eb527-106">Parameters</span></span>  

 `baseAddress`  
 <span data-ttu-id="eb527-107">からモジュールのベースアドレスを表す [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) 値。</span><span class="sxs-lookup"><span data-stu-id="eb527-107">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="eb527-108">[入力] モジュールのパスを受け取るバッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="eb527-108">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="eb527-109">[出力] `szName` バッファーに書き込まれる文字数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="eb527-109">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="eb527-110">[出力] モジュールのパス。</span><span class="sxs-lookup"><span data-stu-id="eb527-110">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb527-111">解説</span><span class="sxs-lookup"><span data-stu-id="eb527-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb527-112">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="eb527-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb527-113">要件</span><span class="sxs-lookup"><span data-stu-id="eb527-113">Requirements</span></span>  

 <span data-ttu-id="eb527-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb527-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb527-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb527-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb527-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb527-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb527-117">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb527-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb527-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb527-118">See also</span></span>

- [<span data-ttu-id="eb527-119">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb527-119">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="eb527-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb527-120">Debugging Interfaces</span></span>](debugging-interfaces.md)

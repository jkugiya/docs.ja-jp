---
description: '詳細については、次を参照してください: ICorDebugILCode2:: GetLocalVarSigToken メソッド'
title: ICorDebugILCode2::GetLocalVarSigToken メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
ms.openlocfilehash: cdf2725274a132528123534ddd36ae95e265af44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791427"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="0905b-103">ICorDebugILCode2::GetLocalVarSigToken メソッド</span><span class="sxs-lookup"><span data-stu-id="0905b-103">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>

<span data-ttu-id="0905b-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="0905b-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0905b-105">このインスタンスで示される関数について、ローカル変数のシグネチャのメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="0905b-105">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0905b-106">構文</span><span class="sxs-lookup"><span data-stu-id="0905b-106">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0905b-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0905b-107">Parameters</span></span>  

 `pmdSig`  
 <span data-ttu-id="0905b-108">[out] この機能のローカル変数シグネチャの `mdSignature` トークンへのポインター、またはシグネチャがない場合 (つまり、機能にローカル変数がない場合) は `mdSignatureNil`。</span><span class="sxs-lookup"><span data-stu-id="0905b-108">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0905b-109">解説</span><span class="sxs-lookup"><span data-stu-id="0905b-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0905b-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="0905b-110">Requirements</span></span>  

 <span data-ttu-id="0905b-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0905b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0905b-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0905b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0905b-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0905b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0905b-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0905b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0905b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0905b-115">See also</span></span>

- [<span data-ttu-id="0905b-116">ICorDebugILCode2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0905b-116">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="0905b-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="0905b-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

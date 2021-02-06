---
description: '詳細情報: ヘルプモジュール:: GetToken メソッド'
title: ICorDebugModule::GetToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
ms.openlocfilehash: fd1bc4bc397e7f81c77f2fe784c68dbaaceb2695
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660168"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="dd3f0-103">ICorDebugModule::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="dd3f0-103">ICorDebugModule::GetToken Method</span></span>

<span data-ttu-id="dd3f0-104">このモジュールのテーブルエントリのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="dd3f0-104">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd3f0-105">構文</span><span class="sxs-lookup"><span data-stu-id="dd3f0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd3f0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd3f0-106">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="dd3f0-107">入出力 `mdModule` モジュールのメタデータを参照するトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dd3f0-107">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd3f0-108">解説</span><span class="sxs-lookup"><span data-stu-id="dd3f0-108">Remarks</span></span>  

 <span data-ttu-id="dd3f0-109">トークンは、 [IMetaDataImport](../metadata/imetadataimport-interface.md)、 [IMetaDataImport2](../metadata/imetadataimport2-interface.md)、および [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) メタデータインポートインターフェイスに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="dd3f0-109">The token can be passed to the [IMetaDataImport](../metadata/imetadataimport-interface.md), [IMetaDataImport2](../metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd3f0-110">要件</span><span class="sxs-lookup"><span data-stu-id="dd3f0-110">Requirements</span></span>  

 <span data-ttu-id="dd3f0-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd3f0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd3f0-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd3f0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd3f0-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd3f0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd3f0-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd3f0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd3f0-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd3f0-115">See also</span></span>

- [<span data-ttu-id="dd3f0-116">Metadata</span><span class="sxs-lookup"><span data-stu-id="dd3f0-116">Metadata</span></span>](../metadata/index.md)

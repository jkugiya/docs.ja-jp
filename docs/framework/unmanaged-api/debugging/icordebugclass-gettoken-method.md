---
description: '詳細については、次を参照してください: のクラス:: GetToken メソッド'
title: ICorDebugClass::GetToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type:
- apiref
ms.openlocfilehash: f87b71800410fc3a95790e6d35cf4bd10a5ce747
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711533"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="7c874-103">ICorDebugClass::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="7c874-103">ICorDebugClass::GetToken Method</span></span>

<span data-ttu-id="7c874-104">`TypeDef`このクラスの定義を参照するメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="7c874-104">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c874-105">構文</span><span class="sxs-lookup"><span data-stu-id="7c874-105">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c874-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7c874-106">Parameters</span></span>  

 `pTypeDef`  
 <span data-ttu-id="7c874-107">入出力 `mdTypeDef` このクラスの定義を参照するトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7c874-107">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c874-108">要件</span><span class="sxs-lookup"><span data-stu-id="7c874-108">Requirements</span></span>  

 <span data-ttu-id="7c874-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c874-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c874-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c874-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c874-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c874-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c874-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c874-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c874-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c874-113">See also</span></span>

- [<span data-ttu-id="7c874-114">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c874-114">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)

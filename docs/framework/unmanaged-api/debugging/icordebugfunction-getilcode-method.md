---
description: '詳細については、次の情報を参照してください: GetILCode メソッド'
title: ICorDebugFunction::GetILCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
ms.openlocfilehash: 3b7bb29a028b189b24d3fbf02edc8190d9989a51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692525"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="9246d-103">ICorDebugFunction::GetILCode メソッド</span><span class="sxs-lookup"><span data-stu-id="9246d-103">ICorDebugFunction::GetILCode Method</span></span>

<span data-ttu-id="9246d-104">このオブジェクトに関連付けられている MSIL (Microsoft 中間言語) コードを表す、コードインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="9246d-104">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9246d-105">構文</span><span class="sxs-lookup"><span data-stu-id="9246d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9246d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9246d-106">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="9246d-107">入出力インスタンスへのポインター。 `ICorDebugCode` 関数が MSIL にコンパイルされなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="9246d-107">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9246d-108">解説</span><span class="sxs-lookup"><span data-stu-id="9246d-108">Remarks</span></span>  

 <span data-ttu-id="9246d-109">この関数でエディットコンティニュが許可されている場合、メソッドは、 `GetILCode` 共通言語ランタイム (CLR) で、この関数の編集されたバージョンのコードに対応する MSIL コードを取得します。</span><span class="sxs-lookup"><span data-stu-id="9246d-109">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9246d-110">要件</span><span class="sxs-lookup"><span data-stu-id="9246d-110">Requirements</span></span>  

 <span data-ttu-id="9246d-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9246d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9246d-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9246d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9246d-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9246d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9246d-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9246d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

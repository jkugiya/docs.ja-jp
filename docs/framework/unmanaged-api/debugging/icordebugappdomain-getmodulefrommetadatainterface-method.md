---
description: '詳細については、次のページを参照してください: いいね。:、GetModuleFromMetaDataInterface メソッド'
title: ICorDebugAppDomain::GetModuleFromMetaDataInterface メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetModuleFromMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDataInterface
helpviewer_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDatainterface method [.NET Framework debugging]
- GetModuleFromMetaDatainterface method [.NET Framework debugging]
ms.assetid: f35225b3-5dda-4d5a-913d-b3373e9ab81e
topic_type:
- apiref
ms.openlocfilehash: 7b0c74bd04024f9f4bf26b5ee8abe18a3a7059e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754239"
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a><span data-ttu-id="fdabf-103">ICorDebugAppDomain::GetModuleFromMetaDataInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="fdabf-103">ICorDebugAppDomain::GetModuleFromMetaDataInterface Method</span></span>

<span data-ttu-id="fdabf-104">指定されたメタデータインターフェイスに対応するモジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="fdabf-104">Gets the module that corresponds to the given metadata interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdabf-105">構文</span><span class="sxs-lookup"><span data-stu-id="fdabf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdabf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fdabf-106">Parameters</span></span>  

 `pIMetaData`  
 <span data-ttu-id="fdabf-107">から [メタデータインターフェイス](../metadata/metadata-interfaces.md)の1つであるオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fdabf-107">[in] A pointer to an object that is one of the [Metadata interfaces](../metadata/metadata-interfaces.md).</span></span>  
  
 `ppModule`  
 <span data-ttu-id="fdabf-108">入出力指定されたメタデータインターフェイスに対応するモジュールを表す、モジュールオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fdabf-108">[out] A pointer to the address of an ICorDebugModule object that represents the module corresponding to the given metadata interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdabf-109">要件</span><span class="sxs-lookup"><span data-stu-id="fdabf-109">Requirements</span></span>  

 <span data-ttu-id="fdabf-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fdabf-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdabf-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fdabf-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fdabf-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdabf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdabf-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdabf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

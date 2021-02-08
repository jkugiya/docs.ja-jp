---
description: '詳細について: IMetaDataValidate:: ValidatorInit メソッド'
title: IMetaDataValidate::ValidatorInit メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataValidate.ValidatorInit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type:
- apiref
ms.openlocfilehash: 99435eeab542e9cb3bb679ad146b546ce51c8df4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799188"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="0627e-103">IMetaDataValidate::ValidatorInit メソッド</span><span class="sxs-lookup"><span data-stu-id="0627e-103">IMetaDataValidate::ValidatorInit Method</span></span>

<span data-ttu-id="0627e-104">現在のメタデータ スコープ内にあるモジュールの種類を指定するフラグを設定し、指定されたコールバック メソッドを検証エラー用に登録します。</span><span class="sxs-lookup"><span data-stu-id="0627e-104">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0627e-105">構文</span><span class="sxs-lookup"><span data-stu-id="0627e-105">Syntax</span></span>  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0627e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0627e-106">Parameters</span></span>  

 `dwModule`  
 <span data-ttu-id="0627e-107">から現在のメタデータスコープ内のモジュールの型を指定する [Corvalidatormoduletype](corvalidatormoduletype-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="0627e-107">[in] A value of the [CorValidatorModuleType](corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="0627e-108">から検証エラーの関数コールバックとして機能する [IUnknown](/cpp/atl/iunknown) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0627e-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0627e-109">要件</span><span class="sxs-lookup"><span data-stu-id="0627e-109">Requirements</span></span>  

 <span data-ttu-id="0627e-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0627e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0627e-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0627e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0627e-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="0627e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0627e-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0627e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0627e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="0627e-114">See also</span></span>

- [<span data-ttu-id="0627e-115">IMetaDataValidate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0627e-115">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)

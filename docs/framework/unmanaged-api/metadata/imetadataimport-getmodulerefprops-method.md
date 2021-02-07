---
description: '詳細について: IMetaDataImport:: GetModuleRefProps メソッド'
title: IMetaDataImport::GetModuleRefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: 3e6b212ddad5eefb06942c3fd4b89411b277f761
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753355"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="89e81-103">IMetaDataImport::GetModuleRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="89e81-103">IMetaDataImport::GetModuleRefProps Method</span></span>

<span data-ttu-id="89e81-104">指定したメタデータ トークンによって参照されるモジュールの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="89e81-104">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e81-105">構文</span><span class="sxs-lookup"><span data-stu-id="89e81-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89e81-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="89e81-106">Parameters</span></span>  

 `mur`  
 <span data-ttu-id="89e81-107">からメタデータ情報を取得するモジュールを参照する ModuleRef メタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="89e81-107">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="89e81-108">入出力モジュール名を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="89e81-108">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="89e81-109">から要求されたサイズ ( `szName` ワイド文字単位)。</span><span class="sxs-lookup"><span data-stu-id="89e81-109">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="89e81-110">入出力返されたのサイズを `szName` ワイド文字数で返します。</span><span class="sxs-lookup"><span data-stu-id="89e81-110">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89e81-111">要件</span><span class="sxs-lookup"><span data-stu-id="89e81-111">Requirements</span></span>  

 <span data-ttu-id="89e81-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89e81-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89e81-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="89e81-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89e81-114">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="89e81-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89e81-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89e81-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89e81-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="89e81-116">See also</span></span>

- [<span data-ttu-id="89e81-117">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="89e81-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="89e81-118">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="89e81-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

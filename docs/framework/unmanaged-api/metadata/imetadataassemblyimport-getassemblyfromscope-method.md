---
description: '詳細について: IMetaDataAssemblyImport:: GetAssemblyFromScope メソッド'
title: IMetaDataAssemblyImport::GetAssemblyFromScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type:
- apiref
ms.openlocfilehash: 78e2862fca80dc06c37436f3d81db4b19c4ec332
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784159"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="a37e1-103">IMetaDataAssemblyImport::GetAssemblyFromScope メソッド</span><span class="sxs-lookup"><span data-stu-id="a37e1-103">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>

<span data-ttu-id="a37e1-104">現在のスコープ内のアセンブリへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="a37e1-104">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a37e1-105">構文</span><span class="sxs-lookup"><span data-stu-id="a37e1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a37e1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a37e1-106">Parameters</span></span>  

 `ptkAssembly`  
 <span data-ttu-id="a37e1-107">入出力アセンブリを識別する、取得されたトークンへのポインター `mdAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="a37e1-107">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a37e1-108">要件</span><span class="sxs-lookup"><span data-stu-id="a37e1-108">Requirements</span></span>  

 <span data-ttu-id="a37e1-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a37e1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a37e1-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="a37e1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a37e1-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="a37e1-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a37e1-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a37e1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a37e1-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a37e1-113">See also</span></span>

- [<span data-ttu-id="a37e1-114">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a37e1-114">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)

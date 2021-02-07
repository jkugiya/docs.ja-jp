---
description: '詳細について: IMetaDataAssemblyImport:: CloseEnum メソッド'
title: IMetaDataAssemblyImport::CloseEnum メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::CloseEnum
helpviewer_keywords:
- CloseEnum method, IMetaDataAssemblyImport interface [.NET Framework metadata]
- IMetaDataAssemblyImport::CloseEnum method [.NET Framework metadata]
ms.assetid: c9df4087-12b3-46d9-b075-9067dd7805df
topic_type:
- apiref
ms.openlocfilehash: 3ff234fac905a058ed832d58a0f996a2c7393ed0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678082"
---
# <a name="imetadataassemblyimportcloseenum-method"></a><span data-ttu-id="a5c05-103">IMetaDataAssemblyImport::CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="a5c05-103">IMetaDataAssemblyImport::CloseEnum Method</span></span>

<span data-ttu-id="a5c05-104">指定した列挙インスタンスへの参照を解放します。</span><span class="sxs-lookup"><span data-stu-id="a5c05-104">Releases a reference to the specified enumeration instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c05-105">構文</span><span class="sxs-lookup"><span data-stu-id="a5c05-105">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
    [in] HCORENUM     hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5c05-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a5c05-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="a5c05-107">から閉じられる列挙体のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="a5c05-107">[in] The enumeration instance to be closed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5c05-108">要件</span><span class="sxs-lookup"><span data-stu-id="a5c05-108">Requirements</span></span>  

 <span data-ttu-id="a5c05-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5c05-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5c05-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="a5c05-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a5c05-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="a5c05-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5c05-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5c05-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c05-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5c05-113">See also</span></span>

- [<span data-ttu-id="a5c05-114">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5c05-114">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)

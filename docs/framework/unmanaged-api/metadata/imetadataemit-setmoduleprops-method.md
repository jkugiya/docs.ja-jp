---
description: '詳細について: IMetaDataEmit:: SetModuleProps メソッド'
title: IMetaDataEmit::SetModuleProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
ms.openlocfilehash: 0fc68a3f40871ddbb70cef885789ae7fe8ae0cba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772025"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="05f4b-103">IMetaDataEmit::SetModuleProps メソッド</span><span class="sxs-lookup"><span data-stu-id="05f4b-103">IMetaDataEmit::SetModuleProps Method</span></span>

<span data-ttu-id="05f4b-104">[IMetaDataEmit::D efinemoduleref](imetadataemit-definemoduleref-method.md)の前の呼び出しで定義されているモジュールへの参照を更新します。</span><span class="sxs-lookup"><span data-stu-id="05f4b-104">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05f4b-105">構文</span><span class="sxs-lookup"><span data-stu-id="05f4b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05f4b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05f4b-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="05f4b-107">からUnicode のモジュール名。</span><span class="sxs-lookup"><span data-stu-id="05f4b-107">[in] The module name in Unicode.</span></span> <span data-ttu-id="05f4b-108">これはファイル名のみで、完全なパス名ではありません。</span><span class="sxs-lookup"><span data-stu-id="05f4b-108">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05f4b-109">要件</span><span class="sxs-lookup"><span data-stu-id="05f4b-109">Requirements</span></span>  

 <span data-ttu-id="05f4b-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05f4b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05f4b-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="05f4b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05f4b-112">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="05f4b-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05f4b-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05f4b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f4b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="05f4b-114">See also</span></span>

- [<span data-ttu-id="05f4b-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05f4b-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="05f4b-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05f4b-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

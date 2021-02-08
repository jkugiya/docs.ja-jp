---
description: '詳細について: IMetaDataEmit:: SetPermissionSetProps メソッド'
title: IMetaDataEmit::SetPermissionSetProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: 1e2786a21a1024f32328e36878a1a2427af54f51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771887"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="e0b64-103">IMetaDataEmit::SetPermissionSetProps メソッド</span><span class="sxs-lookup"><span data-stu-id="e0b64-103">IMetaDataEmit::SetPermissionSetProps Method</span></span>

<span data-ttu-id="e0b64-104">[IMetaDataEmit::D efinepermissionset](imetadataemit-definepermissionset-method.md)の前の呼び出しで定義されたアクセス許可セットのメタデータ署名の機能を設定または更新します。</span><span class="sxs-lookup"><span data-stu-id="e0b64-104">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0b64-105">構文</span><span class="sxs-lookup"><span data-stu-id="e0b64-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0b64-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e0b64-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="e0b64-107">から修飾されるオブジェクトを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="e0b64-107">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="e0b64-108">から使用する宣言セキュリティの種類を指定する [CorDeclSecurity](cordeclsecurity-enumeration.md) 値です。</span><span class="sxs-lookup"><span data-stu-id="e0b64-108">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="e0b64-109">からアクセス許可 BLOB。</span><span class="sxs-lookup"><span data-stu-id="e0b64-109">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="e0b64-110">からのサイズ (バイト単位) `pvPermission` 。</span><span class="sxs-lookup"><span data-stu-id="e0b64-110">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="e0b64-111">入出力 `mdPermission` 更新されたアクセス許可を表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="e0b64-111">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0b64-112">要件</span><span class="sxs-lookup"><span data-stu-id="e0b64-112">Requirements</span></span>  

 <span data-ttu-id="e0b64-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0b64-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0b64-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="e0b64-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0b64-115">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0b64-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0b64-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0b64-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0b64-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0b64-117">See also</span></span>

- [<span data-ttu-id="e0b64-118">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e0b64-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e0b64-119">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e0b64-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

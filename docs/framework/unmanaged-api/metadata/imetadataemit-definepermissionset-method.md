---
description: '詳細について: IMetaDataEmit::D efinePermissionSet メソッド'
title: IMetaDataEmit::DefinePermissionSet メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
ms.openlocfilehash: f5c3f1466217713cb3970c805079d8f65fd429c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784081"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="b878c-103">IMetaDataEmit::DefinePermissionSet メソッド</span><span class="sxs-lookup"><span data-stu-id="b878c-103">IMetaDataEmit::DefinePermissionSet Method</span></span>

<span data-ttu-id="b878c-104">指定したメタデータシグネチャを持つアクセス許可セットの定義を作成し、そのアクセス許可セットの定義に対するトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="b878c-104">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b878c-105">構文</span><span class="sxs-lookup"><span data-stu-id="b878c-105">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b878c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b878c-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="b878c-107">から修飾されるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b878c-107">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="b878c-108">から使用する宣言セキュリティの種類を指定する [CorDeclSecurity](cordeclsecurity-enumeration.md) 値です。</span><span class="sxs-lookup"><span data-stu-id="b878c-108">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="b878c-109">からアクセス許可 BLOB。</span><span class="sxs-lookup"><span data-stu-id="b878c-109">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="b878c-110">からのサイズ (バイト単位) `pvPermission` 。</span><span class="sxs-lookup"><span data-stu-id="b878c-110">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="b878c-111">入出力返されたアクセス許可トークン。</span><span class="sxs-lookup"><span data-stu-id="b878c-111">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b878c-112">要件</span><span class="sxs-lookup"><span data-stu-id="b878c-112">Requirements</span></span>  

 <span data-ttu-id="b878c-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b878c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b878c-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b878c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b878c-115">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b878c-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b878c-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b878c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b878c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b878c-117">See also</span></span>

- [<span data-ttu-id="b878c-118">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b878c-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b878c-119">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b878c-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

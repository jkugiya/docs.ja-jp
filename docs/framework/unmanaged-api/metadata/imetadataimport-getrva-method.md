---
description: '詳細について: IMetaDataImport:: GetRVA メソッド'
title: IMetaDataImport::GetRVA メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 8d6439bcad50a6311e7bb1408f4c86144a5026ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789165"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="f9ccb-103">IMetaDataImport::GetRVA メソッド</span><span class="sxs-lookup"><span data-stu-id="f9ccb-103">IMetaDataImport::GetRVA Method</span></span>

<span data-ttu-id="f9ccb-104">指定したトークンによって表されるメソッドまたはフィールドの相対仮想アドレス (RVA) および実装フラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="f9ccb-104">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9ccb-105">構文</span><span class="sxs-lookup"><span data-stu-id="f9ccb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9ccb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9ccb-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="f9ccb-107">からRVA を返すコードオブジェクトを表す MethodDef または FieldDef のメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="f9ccb-107">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="f9ccb-108">トークンが FieldDef の場合、フィールドはグローバル変数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9ccb-108">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="f9ccb-109">入出力トークンによって表されるコードオブジェクトの相対仮想アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f9ccb-109">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="f9ccb-110">入出力メソッドの実装フラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f9ccb-110">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="f9ccb-111">この値は [Cormethodimpl](cormethodimpl-enumeration.md) 列挙子のビットマスクです。</span><span class="sxs-lookup"><span data-stu-id="f9ccb-111">This value is a bitmask from the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="f9ccb-112">の値は、 `pdwImplFlags` `tk` が MethodDef トークンの場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="f9ccb-112">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9ccb-113">要件</span><span class="sxs-lookup"><span data-stu-id="f9ccb-113">Requirements</span></span>  

 <span data-ttu-id="f9ccb-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9ccb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9ccb-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f9ccb-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9ccb-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f9ccb-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f9ccb-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9ccb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ccb-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9ccb-118">See also</span></span>

- [<span data-ttu-id="f9ccb-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9ccb-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f9ccb-120">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9ccb-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

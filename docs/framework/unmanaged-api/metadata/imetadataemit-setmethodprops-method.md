---
description: '詳細について: IMetaDataEmit:: SetMethodProps メソッド'
title: IMetaDataEmit::SetMethodProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
ms.openlocfilehash: edecdc14abb386f8fa4cd70535f2b8c012bdc59f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772095"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="b72eb-103">IMetaDataEmit::SetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="b72eb-103">IMetaDataEmit::SetMethodProps Method</span></span>

<span data-ttu-id="b72eb-104">[IMetaDataEmit::D efinemethod](imetadataemit-definemethod-method.md)の前の呼び出しで定義されたメソッドの、指定した相対仮想アドレスに格納されている機能を設定または更新します。</span><span class="sxs-lookup"><span data-stu-id="b72eb-104">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b72eb-105">構文</span><span class="sxs-lookup"><span data-stu-id="b72eb-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b72eb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b72eb-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="b72eb-107">から変更するメソッドのトークン。</span><span class="sxs-lookup"><span data-stu-id="b72eb-107">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="b72eb-108">からメンバー属性。</span><span class="sxs-lookup"><span data-stu-id="b72eb-108">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="b72eb-109">からコードのアドレス。</span><span class="sxs-lookup"><span data-stu-id="b72eb-109">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="b72eb-110">からメソッドの実装フラグ。</span><span class="sxs-lookup"><span data-stu-id="b72eb-110">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b72eb-111">要件</span><span class="sxs-lookup"><span data-stu-id="b72eb-111">Requirements</span></span>  

 <span data-ttu-id="b72eb-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b72eb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b72eb-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b72eb-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b72eb-114">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b72eb-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b72eb-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b72eb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b72eb-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b72eb-116">See also</span></span>

- [<span data-ttu-id="b72eb-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b72eb-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b72eb-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b72eb-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

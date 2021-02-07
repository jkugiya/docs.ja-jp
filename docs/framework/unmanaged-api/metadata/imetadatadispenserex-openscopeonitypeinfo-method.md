---
description: '詳細について: IMetaDataDispenserEx:: OpenScopeOnITypeInfo メソッド'
title: IMetaDataDispenserEx::OpenScopeOnITypeInfo メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type:
- apiref
ms.openlocfilehash: bc36bac9e7c63f56f442f1e25fd7a6a93f75924b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753524"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="5bec8-103">IMetaDataDispenserEx::OpenScopeOnITypeInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="5bec8-103">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>

<span data-ttu-id="5bec8-104">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="5bec8-104">This method is not implemented.</span></span> <span data-ttu-id="5bec8-105">呼び出された場合は E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="5bec8-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bec8-106">構文</span><span class="sxs-lookup"><span data-stu-id="5bec8-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bec8-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5bec8-107">Parameters</span></span>  

 `pITI`  
 <span data-ttu-id="5bec8-108">からスコープを開く対象の型情報を提供する [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5bec8-108">[in] Pointer to an [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="5bec8-109">からOpen モードフラグ。</span><span class="sxs-lookup"><span data-stu-id="5bec8-109">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="5bec8-110">から目的のインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="5bec8-110">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="5bec8-111">入出力返されたインターフェイスへのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5bec8-111">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bec8-112">要件</span><span class="sxs-lookup"><span data-stu-id="5bec8-112">Requirements</span></span>  

 <span data-ttu-id="5bec8-113">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bec8-113">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bec8-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="5bec8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5bec8-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="5bec8-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5bec8-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bec8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bec8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bec8-117">See also</span></span>

- [<span data-ttu-id="5bec8-118">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5bec8-118">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="5bec8-119">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5bec8-119">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)

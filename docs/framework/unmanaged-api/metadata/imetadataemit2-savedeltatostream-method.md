---
description: '詳細について: IMetaDataEmit2:: SaveDeltaToStream メソッド'
title: IMetaDataEmit2::SaveDeltaToStream メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
ms.openlocfilehash: ce2e7822a5220a8ab1264a6e18337ba0f7828e3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771705"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="a9e86-103">IMetaDataEmit2::SaveDeltaToStream メソッド</span><span class="sxs-lookup"><span data-stu-id="a9e86-103">IMetaDataEmit2::SaveDeltaToStream Method</span></span>

<span data-ttu-id="a9e86-104">現在のエディットコンティニュセッションから、指定されたストリームに変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="a9e86-104">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9e86-105">構文</span><span class="sxs-lookup"><span data-stu-id="a9e86-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9e86-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a9e86-106">Parameters</span></span>  

 `pIStream`  
 <span data-ttu-id="a9e86-107">から変更を保存する書き込み可能なストリームへのインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="a9e86-107">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="a9e86-108">[in] 予約されています。</span><span class="sxs-lookup"><span data-stu-id="a9e86-108">[in] Reserved.</span></span> <span data-ttu-id="a9e86-109">必ずゼロを指定します。</span><span class="sxs-lookup"><span data-stu-id="a9e86-109">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9e86-110">要件</span><span class="sxs-lookup"><span data-stu-id="a9e86-110">Requirements</span></span>  

 <span data-ttu-id="a9e86-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9e86-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9e86-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="a9e86-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9e86-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="a9e86-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9e86-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9e86-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9e86-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9e86-115">See also</span></span>

- [<span data-ttu-id="a9e86-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9e86-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="a9e86-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9e86-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)

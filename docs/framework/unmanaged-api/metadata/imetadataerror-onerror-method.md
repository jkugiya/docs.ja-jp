---
description: '詳細について: IMetaDataError:: OnError メソッド'
title: IMetaDataError::OnError メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
ms.openlocfilehash: 9556f1bd7758755d9160e3a2e91a1fe5786aa562
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670971"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="b98e9-103">IMetaDataError::OnError メソッド</span><span class="sxs-lookup"><span data-stu-id="b98e9-103">IMetaDataError::OnError Method</span></span>

<span data-ttu-id="b98e9-104">メタデータのマージ中に発生したエラーの通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="b98e9-104">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b98e9-105">構文</span><span class="sxs-lookup"><span data-stu-id="b98e9-105">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b98e9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b98e9-106">Parameters</span></span>  

 `hrError`  
 <span data-ttu-id="b98e9-107">から呼び出し元のメソッドに返される HRESULT エラー値。</span><span class="sxs-lookup"><span data-stu-id="b98e9-107">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="b98e9-108">からエラーが発生したときにマージされていたコードオブジェクトのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="b98e9-108">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b98e9-109">要件</span><span class="sxs-lookup"><span data-stu-id="b98e9-109">Requirements</span></span>  

 <span data-ttu-id="b98e9-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b98e9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b98e9-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b98e9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b98e9-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b98e9-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b98e9-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b98e9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b98e9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b98e9-114">See also</span></span>

- [<span data-ttu-id="b98e9-115">IMetaDataError インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b98e9-115">IMetaDataError Interface</span></span>](imetadataerror-interface.md)

---
description: '詳細について: IMetaDataEmit2:: SaveDelta メソッド'
title: IMetaDataEmit2::SaveDelta メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
ms.openlocfilehash: 6e7a7527125869fea041f407da056db3eea88cbe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771770"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="53ee2-103">IMetaDataEmit2::SaveDelta メソッド</span><span class="sxs-lookup"><span data-stu-id="53ee2-103">IMetaDataEmit2::SaveDelta Method</span></span>

<span data-ttu-id="53ee2-104">現在のエディットコンティニュセッションから、指定したファイルへの変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="53ee2-104">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53ee2-105">構文</span><span class="sxs-lookup"><span data-stu-id="53ee2-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53ee2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="53ee2-106">Parameters</span></span>  

 `szFile`  
 <span data-ttu-id="53ee2-107">から変更を保存するファイル名。</span><span class="sxs-lookup"><span data-stu-id="53ee2-107">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="53ee2-108">[in] 予約されています。</span><span class="sxs-lookup"><span data-stu-id="53ee2-108">[in] Reserved.</span></span> <span data-ttu-id="53ee2-109">ゼロを指定してください。</span><span class="sxs-lookup"><span data-stu-id="53ee2-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53ee2-110">要件</span><span class="sxs-lookup"><span data-stu-id="53ee2-110">Requirements</span></span>  

 <span data-ttu-id="53ee2-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53ee2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53ee2-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="53ee2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53ee2-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="53ee2-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53ee2-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53ee2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53ee2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="53ee2-115">See also</span></span>

- [<span data-ttu-id="53ee2-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="53ee2-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="53ee2-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="53ee2-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)

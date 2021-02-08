---
description: '詳細について: IMetaDataTables2:: GetMetaDataStreamInfo メソッド'
title: IMetaDataTables2::GetMetaDataStreamInfo メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
ms.openlocfilehash: 323c31931cc97f18ff09df83c57153a3629d0a10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799246"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="18261-103">IMetaDataTables2::GetMetaDataStreamInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="18261-103">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>

<span data-ttu-id="18261-104">指定したインデックス位置にあるメタデータストリームの名前、サイズ、および内容を取得します。</span><span class="sxs-lookup"><span data-stu-id="18261-104">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18261-105">構文</span><span class="sxs-lookup"><span data-stu-id="18261-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18261-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="18261-106">Parameters</span></span>  

 `ix`  
 <span data-ttu-id="18261-107">から要求されたメタデータストリームのインデックス。</span><span class="sxs-lookup"><span data-stu-id="18261-107">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="18261-108">入出力ストリームの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="18261-108">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="18261-109">入出力メタデータストリームへのポインター。</span><span class="sxs-lookup"><span data-stu-id="18261-109">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="18261-110">入出力のサイズ (バイト単位) `ppv` 。</span><span class="sxs-lookup"><span data-stu-id="18261-110">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18261-111">要件</span><span class="sxs-lookup"><span data-stu-id="18261-111">Requirements</span></span>  

 <span data-ttu-id="18261-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18261-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18261-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="18261-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18261-114">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="18261-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18261-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18261-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18261-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="18261-116">See also</span></span>

- [<span data-ttu-id="18261-117">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="18261-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="18261-118">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="18261-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)

---
description: '詳細について: IMetaDataTables2:: GetMetaDataStorage メソッド'
title: IMetaDataTables2::GetMetaDataStorage メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
ms.openlocfilehash: df6bbc69be05986dc6d4f143cec7ec09a2d78ee5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799249"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="5ffa0-103">IMetaDataTables2::GetMetaDataStorage メソッド</span><span class="sxs-lookup"><span data-stu-id="5ffa0-103">IMetaDataTables2::GetMetaDataStorage Method</span></span>

<span data-ttu-id="5ffa0-104">指定したセクションに格納されているメタデータのサイズと内容を取得します。</span><span class="sxs-lookup"><span data-stu-id="5ffa0-104">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ffa0-105">構文</span><span class="sxs-lookup"><span data-stu-id="5ffa0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ffa0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ffa0-106">Parameters</span></span>  

 `ppvMd`  
 <span data-ttu-id="5ffa0-107">[入力、出力]メタデータセクションへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5ffa0-107">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="5ffa0-108">入出力メタデータストリームのサイズ。</span><span class="sxs-lookup"><span data-stu-id="5ffa0-108">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ffa0-109">要件</span><span class="sxs-lookup"><span data-stu-id="5ffa0-109">Requirements</span></span>  

 <span data-ttu-id="5ffa0-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ffa0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ffa0-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="5ffa0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ffa0-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ffa0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5ffa0-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ffa0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ffa0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ffa0-114">See also</span></span>

- [<span data-ttu-id="5ffa0-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ffa0-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="5ffa0-116">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ffa0-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)

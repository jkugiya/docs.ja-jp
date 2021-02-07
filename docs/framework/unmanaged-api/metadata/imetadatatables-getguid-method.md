---
description: '詳細については、次を参照してください: IMetaDataTables 許容:: GetGuid メソッド'
title: IMetaDataTables::GetGuid メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 9c3b8b11bb2f6a1abc3c55d953e1cbfbd7ee8622
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688170"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="ef714-103">IMetaDataTables::GetGuid メソッド</span><span class="sxs-lookup"><span data-stu-id="ef714-103">IMetaDataTables::GetGuid Method</span></span>

<span data-ttu-id="ef714-104">指定したインデックス位置にある行から GUID を取得します。</span><span class="sxs-lookup"><span data-stu-id="ef714-104">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef714-105">構文</span><span class="sxs-lookup"><span data-stu-id="ef714-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef714-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ef714-106">Parameters</span></span>  

 `ixGuid`  
 <span data-ttu-id="ef714-107">からGUID の取得元となる行のインデックス。</span><span class="sxs-lookup"><span data-stu-id="ef714-107">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="ef714-108">入出力GUID へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ef714-108">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef714-109">解説</span><span class="sxs-lookup"><span data-stu-id="ef714-109">Remarks</span></span>  

  <span data-ttu-id="ef714-110">このメソッドは、一貫性のある結果を返さないため、使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ef714-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="ef714-111">GUID テーブルの詳細については、共通言語基盤 (CLI) のドキュメント (特に「パーティション II: メタデータの定義とセマンティクス」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef714-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="ef714-112">ドキュメントはオンラインで入手できます。「 [Ecma C# および共通言語基盤の標準](../../../standard/components.md#applicable-standards) と [標準 ecma-335-共通言語基盤 (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef714-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef714-113">要件</span><span class="sxs-lookup"><span data-stu-id="ef714-113">Requirements</span></span>  

 <span data-ttu-id="ef714-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef714-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef714-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="ef714-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef714-116">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="ef714-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ef714-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef714-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef714-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef714-118">See also</span></span>

- [<span data-ttu-id="ef714-119">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef714-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="ef714-120">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef714-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

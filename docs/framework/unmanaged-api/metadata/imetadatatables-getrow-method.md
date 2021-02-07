---
description: '詳細については、「IMetaDataTables:: メソッド」を参照してください。'
title: IMetaDataTables::GetRow メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: f3888bbb53339dc60eb0c2d36f2d7383e5f8c228
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687819"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="a2bd8-103">IMetaDataTables::GetRow メソッド</span><span class="sxs-lookup"><span data-stu-id="a2bd8-103">IMetaDataTables::GetRow Method</span></span>

<span data-ttu-id="a2bd8-104">指定したテーブルインデックスにあるテーブル内の指定した行インデックスにある行を取得します。</span><span class="sxs-lookup"><span data-stu-id="a2bd8-104">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2bd8-105">構文</span><span class="sxs-lookup"><span data-stu-id="a2bd8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2bd8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a2bd8-106">Parameters</span></span>  

 `ixTbl`  
 <span data-ttu-id="a2bd8-107">から行の取得元となるテーブルのインデックス。</span><span class="sxs-lookup"><span data-stu-id="a2bd8-107">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="a2bd8-108">から取得する行のインデックス。</span><span class="sxs-lookup"><span data-stu-id="a2bd8-108">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="a2bd8-109">入出力行へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a2bd8-109">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2bd8-110">解説</span><span class="sxs-lookup"><span data-stu-id="a2bd8-110">Remarks</span></span>  

  <span data-ttu-id="a2bd8-111">このメソッドは、一貫性のある結果を返さないため、使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a2bd8-111">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="a2bd8-112">GUID テーブルの詳細については、共通言語基盤 (CLI) のドキュメント (特に「パーティション II: メタデータの定義とセマンティクス」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2bd8-112">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="a2bd8-113">ドキュメントはオンラインで入手できます。「 [Ecma C# および共通言語基盤の標準](../../../standard/components.md#applicable-standards) と [標準 ecma-335-共通言語基盤 (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2bd8-113">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2bd8-114">要件</span><span class="sxs-lookup"><span data-stu-id="a2bd8-114">Requirements</span></span>  

 <span data-ttu-id="a2bd8-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2bd8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2bd8-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="a2bd8-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2bd8-117">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="a2bd8-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2bd8-118">**.NET Framework のバージョン**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2bd8-118">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2bd8-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2bd8-119">See also</span></span>

- [<span data-ttu-id="a2bd8-120">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2bd8-120">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="a2bd8-121">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2bd8-121">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

---
description: '詳細について: IMetaDataImport:: CloseEnum メソッド'
title: IMetaDataImport::CloseEnum メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
ms.openlocfilehash: b18b484cab0d9f4c0ecea21da78535c9a872bb1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677744"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="df1d8-103">IMetaDataImport::CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="df1d8-103">IMetaDataImport::CloseEnum Method</span></span>

<span data-ttu-id="df1d8-104">指定したハンドルによって識別される列挙子を閉じます。</span><span class="sxs-lookup"><span data-stu-id="df1d8-104">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df1d8-105">構文</span><span class="sxs-lookup"><span data-stu-id="df1d8-105">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df1d8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="df1d8-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="df1d8-107">から閉じる列挙子のハンドル。</span><span class="sxs-lookup"><span data-stu-id="df1d8-107">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df1d8-108">解説</span><span class="sxs-lookup"><span data-stu-id="df1d8-108">Remarks</span></span>  

 <span data-ttu-id="df1d8-109">によって指定されたハンドル `hEnum` は、前 `Enum` の *名前* の呼び出し (たとえば、 [IMetaDataImport:: enumtypedefs](imetadataimport-enumtypedefs-method.md)) から取得されます。</span><span class="sxs-lookup"><span data-stu-id="df1d8-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df1d8-110">要件</span><span class="sxs-lookup"><span data-stu-id="df1d8-110">Requirements</span></span>  

 <span data-ttu-id="df1d8-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df1d8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df1d8-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="df1d8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df1d8-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="df1d8-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df1d8-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df1d8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df1d8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="df1d8-115">See also</span></span>

- [<span data-ttu-id="df1d8-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df1d8-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="df1d8-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df1d8-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

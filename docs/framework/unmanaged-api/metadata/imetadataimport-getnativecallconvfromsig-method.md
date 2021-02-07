---
description: '詳細について: IMetaDataImport:: GetNativeCallConvFromSig メソッド'
title: IMetaDataImport::GetNativeCallConvFromSig メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNativeCallConvFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type:
- apiref
ms.openlocfilehash: 2fb5c347098f860f9ad32eab20c8b5bd6278f838
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677575"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="35ac3-103">IMetaDataImport::GetNativeCallConvFromSig メソッド</span><span class="sxs-lookup"><span data-stu-id="35ac3-103">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>

<span data-ttu-id="35ac3-104">指定したシグネチャ ポインターで表されるメソッドのネイティブな呼び出し規約を取得します。</span><span class="sxs-lookup"><span data-stu-id="35ac3-104">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35ac3-105">構文</span><span class="sxs-lookup"><span data-stu-id="35ac3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35ac3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="35ac3-106">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="35ac3-107">から呼び出し規約を返すメソッドのメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="35ac3-107">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="35ac3-108">からのサイズ (バイト単位) `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="35ac3-108">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="35ac3-109">入出力ネイティブ呼び出し規約へのポインター。</span><span class="sxs-lookup"><span data-stu-id="35ac3-109">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35ac3-110">要件</span><span class="sxs-lookup"><span data-stu-id="35ac3-110">Requirements</span></span>  

 <span data-ttu-id="35ac3-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35ac3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35ac3-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="35ac3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="35ac3-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="35ac3-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="35ac3-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35ac3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35ac3-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="35ac3-115">See also</span></span>

- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="35ac3-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35ac3-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="35ac3-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35ac3-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

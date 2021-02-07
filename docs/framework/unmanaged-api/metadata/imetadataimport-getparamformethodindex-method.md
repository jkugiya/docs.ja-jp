---
description: '詳細について: IMetaDataImport:: GetParamForMethodIndex メソッド'
title: IMetaDataImport::GetParamForMethodIndex メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
ms.openlocfilehash: d84b26f1239e548b6cf96d1e6b38791eb6ecddff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728146"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="62d50-103">IMetaDataImport::GetParamForMethodIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="62d50-103">IMetaDataImport::GetParamForMethodIndex Method</span></span>

<span data-ttu-id="62d50-104">指定した MethodDef トークンによって表されるメソッドの、指定したパラメーターを表すトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="62d50-104">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62d50-105">構文</span><span class="sxs-lookup"><span data-stu-id="62d50-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62d50-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="62d50-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="62d50-107">からパラメータートークンを返すメソッドを表すトークン。</span><span class="sxs-lookup"><span data-stu-id="62d50-107">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="62d50-108">から要求されたパラメーターが発生するパラメーターリスト内の序数位置。</span><span class="sxs-lookup"><span data-stu-id="62d50-108">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="62d50-109">パラメーターには1から始まる番号が付けられ、メソッドの戻り値は0の位置にあります。</span><span class="sxs-lookup"><span data-stu-id="62d50-109">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="62d50-110">入出力要求されたパラメーターを表す ParamDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="62d50-110">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62d50-111">要件</span><span class="sxs-lookup"><span data-stu-id="62d50-111">Requirements</span></span>  

 <span data-ttu-id="62d50-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62d50-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62d50-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="62d50-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="62d50-114">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="62d50-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="62d50-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62d50-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d50-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="62d50-116">See also</span></span>

- [<span data-ttu-id="62d50-117">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62d50-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="62d50-118">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62d50-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

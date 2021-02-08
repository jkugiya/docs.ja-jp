---
description: '詳細について: IMetaDataImport:: GetMemberRefProps メソッド'
title: IMetaDataImport::GetMemberRefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
ms.openlocfilehash: b441f39d95c9af1e18d34a1a4d86d6cea33508c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783880"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="6b742-103">IMetaDataImport::GetMemberRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="6b742-103">IMetaDataImport::GetMemberRefProps Method</span></span>

<span data-ttu-id="6b742-104">指定したトークンによって参照されるメンバーに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="6b742-104">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b742-105">構文</span><span class="sxs-lookup"><span data-stu-id="6b742-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,
   [out] mdToken           *ptk,
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b742-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6b742-106">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="6b742-107">から関連付けられたメタデータを返す MemberRef トークン。</span><span class="sxs-lookup"><span data-stu-id="6b742-107">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="6b742-108">入出力メンバーを宣言するクラスを表す TypeDef または TypeRef または TypeSpec トークン、またはメンバーを宣言するモジュールクラスを表す ModuleRef トークン、またはメンバーを表す MethodDef。</span><span class="sxs-lookup"><span data-stu-id="6b742-108">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="6b742-109">入出力メンバーの名前の文字列バッファー。</span><span class="sxs-lookup"><span data-stu-id="6b742-109">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="6b742-110">からのワイド文字で要求されたサイズ `szMember` 。</span><span class="sxs-lookup"><span data-stu-id="6b742-110">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="6b742-111">入出力のワイド文字で返されたサイズ `szMember` 。</span><span class="sxs-lookup"><span data-stu-id="6b742-111">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="6b742-112">入出力メンバーのバイナリメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b742-112">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="6b742-113">入出力のサイズ (バイト単位) `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="6b742-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b742-114">要件</span><span class="sxs-lookup"><span data-stu-id="6b742-114">Requirements</span></span>  

 <span data-ttu-id="6b742-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b742-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b742-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="6b742-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b742-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6b742-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b742-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b742-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b742-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b742-119">See also</span></span>

- [<span data-ttu-id="6b742-120">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b742-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6b742-121">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b742-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

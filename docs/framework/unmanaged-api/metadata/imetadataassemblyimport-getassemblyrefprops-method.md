---
description: '詳細について: IMetaDataAssemblyImport:: GetAssemblyRefProps メソッド'
title: IMetaDataAssemblyImport::GetAssemblyRefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
ms.openlocfilehash: f7011806920ba37ca84b1a48f12da3a5557fa464
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784133"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="b422c-103">IMetaDataAssemblyImport::GetAssemblyRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="b422c-103">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>

<span data-ttu-id="b422c-104">指定されたメタデータシグネチャを持つアセンブリ参照のプロパティのセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="b422c-104">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b422c-105">構文</span><span class="sxs-lookup"><span data-stu-id="b422c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,
    [out] const void          **ppbPublicKeyOrToken,
    [out] ULONG                *pcbPublicKeyOrToken,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] ASSEMBLYMETADATA     *pMetaData,
    [out] const void           **ppbHashValue,
    [out] ULONG                *pcbHashValue,
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b422c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b422c-106">Parameters</span></span>  

 `mdar`  
 <span data-ttu-id="b422c-107">から `mdAssemblyRef` プロパティを取得する対象のアセンブリ参照を表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="b422c-107">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="b422c-108">入出力公開キーまたはメタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b422c-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="b422c-109">入出力返される公開キーまたはトークン内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="b422c-109">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="b422c-110">入出力アセンブリの簡易名。</span><span class="sxs-lookup"><span data-stu-id="b422c-110">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b422c-111">からのサイズ (ワイド文字数) `szName` 。</span><span class="sxs-lookup"><span data-stu-id="b422c-111">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b422c-112">入出力実際にで返されるワイド文字数へのポインター `szName` 。</span><span class="sxs-lookup"><span data-stu-id="b422c-112">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="b422c-113">入出力アセンブリメタデータを格納している ASSEMBLYMETADATA 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b422c-113">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="b422c-114">入出力ハッシュ値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b422c-114">[out] A pointer to the hash value.</span></span> <span data-ttu-id="b422c-115">これは、参照されるアセンブリのプロパティの SHA-1 アルゴリズムを使用するハッシュです `PublicKey` 。 [Assemblyrefflags](assemblyrefflags-enumeration.md) の列挙の arfFullOriginator フラグが設定されている場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="b422c-115">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="b422c-116">入出力返されたハッシュ値のワイド文字の数。</span><span class="sxs-lookup"><span data-stu-id="b422c-116">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="b422c-117">入出力アセンブリに適用されるメタデータを記述するフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b422c-117">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="b422c-118">Flags 値は、1つまたは複数の [Corassemblyflags](corassemblyflags-enumeration.md) 値を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="b422c-118">The flags value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b422c-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="b422c-119">Return Value</span></span>  

 <span data-ttu-id="b422c-120">成功した場合、このメソッドは S_OK を返します。それ以外の場合は、Winerror.h ヘッダーファイルで定義されているエラーコードの1つを返します。</span><span class="sxs-lookup"><span data-stu-id="b422c-120">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b422c-121">要件</span><span class="sxs-lookup"><span data-stu-id="b422c-121">Requirements</span></span>  

 <span data-ttu-id="b422c-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b422c-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b422c-123">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b422c-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b422c-124">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b422c-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b422c-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b422c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b422c-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="b422c-126">See also</span></span>

- [<span data-ttu-id="b422c-127">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b422c-127">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)

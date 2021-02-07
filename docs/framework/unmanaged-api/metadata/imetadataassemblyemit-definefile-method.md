---
description: '詳細については、次を参照してください: IMetaDataAssemblyEmit::D efineFile メソッド'
title: IMetaDataAssemblyEmit::DefineFile メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: 825ef44c2b0a5f312b4c5f9c851d62e75709c7ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671050"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="f1de5-103">IMetaDataAssemblyEmit::DefineFile メソッド</span><span class="sxs-lookup"><span data-stu-id="f1de5-103">IMetaDataAssemblyEmit::DefineFile Method</span></span>

<span data-ttu-id="f1de5-104">このアセンブリが参照するアセンブリのメタデータを含む `File` メタデータ構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="f1de5-104">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1de5-105">構文</span><span class="sxs-lookup"><span data-stu-id="f1de5-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1de5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f1de5-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="f1de5-107">から使用するファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="f1de5-107">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f1de5-108">からアセンブリに関連付けられているハッシュデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f1de5-108">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f1de5-109">からのサイズ (バイト単位) `pbHashValue` 。</span><span class="sxs-lookup"><span data-stu-id="f1de5-109">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="f1de5-110">から `FileFlags` プロパティ設定を指定する値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="f1de5-110">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="f1de5-111">入出力返されたトークンへのポインター `File` 。</span><span class="sxs-lookup"><span data-stu-id="f1de5-111">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1de5-112">解説</span><span class="sxs-lookup"><span data-stu-id="f1de5-112">Remarks</span></span>  

 <span data-ttu-id="f1de5-113">このアセンブリがビルドされた時点 `File` で、このアセンブリに含まれていたファイルごとに1つのメタデータ構造を定義する必要があります。メタデータを含むファイルは除きます。</span><span class="sxs-lookup"><span data-stu-id="f1de5-113">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1de5-114">要件</span><span class="sxs-lookup"><span data-stu-id="f1de5-114">Requirements</span></span>  

 <span data-ttu-id="f1de5-115">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1de5-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1de5-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f1de5-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1de5-117">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f1de5-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1de5-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1de5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1de5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1de5-119">See also</span></span>

- [<span data-ttu-id="f1de5-120">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1de5-120">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)

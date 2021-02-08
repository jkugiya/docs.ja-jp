---
description: '詳細について: IMetaDataAssemblyEmit:: SetFileProps メソッド'
title: IMetaDataAssemblyEmit::SetFileProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
ms.openlocfilehash: 482aa11b85eaf05d126c4fcc0d5a1aced85002d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789308"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="2b310-103">IMetaDataAssemblyEmit::SetFileProps メソッド</span><span class="sxs-lookup"><span data-stu-id="2b310-103">IMetaDataAssemblyEmit::SetFileProps Method</span></span>

<span data-ttu-id="2b310-104">指定された `File` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="2b310-104">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b310-105">構文</span><span class="sxs-lookup"><span data-stu-id="2b310-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b310-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2b310-106">Parameters</span></span>  

 `file`  
 <span data-ttu-id="2b310-107">から変更するメタデータ構造を指定するメタデータトークン `File` 。</span><span class="sxs-lookup"><span data-stu-id="2b310-107">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="2b310-108">からファイルに関連付けられているハッシュデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2b310-108">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="2b310-109">からのサイズ (バイト単位) `pbHashValue` 。</span><span class="sxs-lookup"><span data-stu-id="2b310-109">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="2b310-110">からファイルのさまざまな属性を指定する [Corfileflags](corfileflags-enumeration.md) 値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="2b310-110">[in] A bitwise combination of [CorFileFlags](corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b310-111">解説</span><span class="sxs-lookup"><span data-stu-id="2b310-111">Remarks</span></span>  

 <span data-ttu-id="2b310-112">メタデータ構造を作成するには `File` 、 [IMetaDataAssemblyEmit::D efineFile](imetadataassemblyemit-definefile-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2b310-112">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b310-113">要件</span><span class="sxs-lookup"><span data-stu-id="2b310-113">Requirements</span></span>  

 <span data-ttu-id="2b310-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b310-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b310-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="2b310-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b310-116">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="2b310-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b310-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b310-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b310-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b310-118">See also</span></span>

- [<span data-ttu-id="2b310-119">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b310-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)

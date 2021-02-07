---
description: '詳細について: IMetaDataAssemblyEmit::D efineAssembly メソッド'
title: IMetaDataAssemblyEmit::DefineAssembly メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: cd53a4398f49ca96072fc5f5b6dcac35a94bdc59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706748"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="200ee-103">IMetaDataAssemblyEmit::DefineAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="200ee-103">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>

<span data-ttu-id="200ee-104">`Assembly`指定したアセンブリのメタデータを格納している構造体を作成し、関連付けられているメタデータトークンを返します。</span><span class="sxs-lookup"><span data-stu-id="200ee-104">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="200ee-105">構文</span><span class="sxs-lookup"><span data-stu-id="200ee-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="200ee-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="200ee-106">Parameters</span></span>  

 `pbPublicKey`  
 <span data-ttu-id="200ee-107">からアセンブリの発行元を識別する公開キー。アセンブリに厳密な名前が付けられていない場合は NULL。</span><span class="sxs-lookup"><span data-stu-id="200ee-107">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="200ee-108">からのサイズ (バイト単位) `pbPublicKey` 。</span><span class="sxs-lookup"><span data-stu-id="200ee-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="200ee-109">からアセンブリ内のファイルを暗号化するために使用するハッシュアルゴリズムの識別子。または、SHA-1 アルゴリズムを指定する場合は NULL。</span><span class="sxs-lookup"><span data-stu-id="200ee-109">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="200ee-110">からユーザーが判読できる、アセンブリのテキスト名。</span><span class="sxs-lookup"><span data-stu-id="200ee-110">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="200ee-111">この値は、1024文字を超えないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="200ee-111">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="200ee-112">からアセンブリのバージョン、プラットフォーム、およびロケール情報を格納している ASSEMBLYMETADATA インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="200ee-112">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="200ee-113">からアセンブリの機能を記述する [Corassemblyflags](corassemblyflags-enumeration.md) 値の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="200ee-113">[in] A combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="200ee-114">入出力メタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="200ee-114">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="200ee-115">解説</span><span class="sxs-lookup"><span data-stu-id="200ee-115">Remarks</span></span>  

 <span data-ttu-id="200ee-116">`Assembly`マニフェスト内で定義できるメタデータ構造は1つだけです。</span><span class="sxs-lookup"><span data-stu-id="200ee-116">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="200ee-117">要件</span><span class="sxs-lookup"><span data-stu-id="200ee-117">Requirements</span></span>  

 <span data-ttu-id="200ee-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="200ee-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="200ee-119">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="200ee-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="200ee-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="200ee-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="200ee-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="200ee-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="200ee-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="200ee-122">See also</span></span>

- [<span data-ttu-id="200ee-123">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="200ee-123">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)

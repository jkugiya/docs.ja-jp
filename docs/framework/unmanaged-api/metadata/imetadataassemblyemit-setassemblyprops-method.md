---
description: '詳細について: IMetaDataAssemblyEmit:: SetAssemblyProps メソッド'
title: IMetaDataAssemblyEmit::SetAssemblyProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
ms.openlocfilehash: d5dfb5fa472bb83863c8e4909998deeb2b9fc53b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678199"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="4402f-103">IMetaDataAssemblyEmit::SetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="4402f-103">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>

<span data-ttu-id="4402f-104">指定された `Assembly` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="4402f-104">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4402f-105">構文</span><span class="sxs-lookup"><span data-stu-id="4402f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4402f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4402f-106">Parameters</span></span>  

 `pma`  
 <span data-ttu-id="4402f-107">から変更するメタデータ構造を指定するメタデータトークン `Assembly` 。</span><span class="sxs-lookup"><span data-stu-id="4402f-107">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="4402f-108">からアセンブリの発行者の公開キーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4402f-108">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="4402f-109">からのサイズ (バイト単位) `pbPublicKey` 。</span><span class="sxs-lookup"><span data-stu-id="4402f-109">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="4402f-110">からアセンブリファイルのハッシュに使用されるハッシュアルゴリズムの識別子。</span><span class="sxs-lookup"><span data-stu-id="4402f-110">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="4402f-111">からユーザーが判読できる、アセンブリのテキスト名。</span><span class="sxs-lookup"><span data-stu-id="4402f-111">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="4402f-112">からアセンブリのバージョン、プラットフォーム、およびロケール情報を格納している ASSEMBLYMETADATA へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4402f-112">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="4402f-113">からアセンブリのさまざまな属性を指定する [Assemblyflags](assemblyflags-enumeration.md) 値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="4402f-113">[in] A bitwise combination of [AssemblyFlags](assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4402f-114">解説</span><span class="sxs-lookup"><span data-stu-id="4402f-114">Remarks</span></span>  

 <span data-ttu-id="4402f-115">メタデータ構造を作成するには `Assembly` 、 [IMetaDataAssemblyEmit::D efineAssembly](imetadataassemblyemit-defineassembly-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4402f-115">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4402f-116">要件</span><span class="sxs-lookup"><span data-stu-id="4402f-116">Requirements</span></span>  

 <span data-ttu-id="4402f-117">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4402f-117">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4402f-118">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4402f-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4402f-119">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="4402f-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4402f-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4402f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4402f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="4402f-121">See also</span></span>

- [<span data-ttu-id="4402f-122">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4402f-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)

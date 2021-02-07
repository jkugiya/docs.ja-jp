---
description: '詳細について: IMetaDataAssemblyEmit::D efineAssemblyRef メソッド'
title: IMetaDataAssemblyEmit::DefineAssemblyRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
ms.openlocfilehash: e3c3acce77e6b0cb2943d66f3477898c90ea6251
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706709"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="dc270-103">IMetaDataAssemblyEmit::DefineAssemblyRef メソッド</span><span class="sxs-lookup"><span data-stu-id="dc270-103">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>

<span data-ttu-id="dc270-104">このアセンブリが参照するアセンブリのメタデータを含む `AssemblyRef` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="dc270-104">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc270-105">構文</span><span class="sxs-lookup"><span data-stu-id="dc270-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc270-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dc270-106">Parameters</span></span>  

 `pbPublicKeyOrToken`  
 <span data-ttu-id="dc270-107">から参照アセンブリの発行元の公開キー。</span><span class="sxs-lookup"><span data-stu-id="dc270-107">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="dc270-108">ヘルパー関数 [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) を使用して、このパラメーターとして渡す公開キーのハッシュを取得できます。</span><span class="sxs-lookup"><span data-stu-id="dc270-108">The helper function [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="dc270-109">からのサイズ (バイト単位) `pbPublicKeyOrToken` 。</span><span class="sxs-lookup"><span data-stu-id="dc270-109">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="dc270-110">からユーザーが判読できる、アセンブリのテキスト名。</span><span class="sxs-lookup"><span data-stu-id="dc270-110">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="dc270-111">この値は、1024文字を超えないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc270-111">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="dc270-112">から参照されたアセンブリのバージョン、プラットフォーム、およびロケール情報を格納している ASSEMBLYMETADATA インスタンス。</span><span class="sxs-lookup"><span data-stu-id="dc270-112">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="dc270-113">から参照アセンブリに関連付けられているハッシュデータ。</span><span class="sxs-lookup"><span data-stu-id="dc270-113">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="dc270-114">任意。</span><span class="sxs-lookup"><span data-stu-id="dc270-114">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="dc270-115">からのサイズ (バイト単位) `pbHashValue` 。</span><span class="sxs-lookup"><span data-stu-id="dc270-115">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="dc270-116">から実行エンジンの動作に影響を与える [Corassemblyflags](corassemblyflags-enumeration.md) 値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="dc270-116">[in] A bitwise combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="dc270-117">入出力返された `AssemblyRef` メタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dc270-117">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc270-118">解説</span><span class="sxs-lookup"><span data-stu-id="dc270-118">Remarks</span></span>  

 <span data-ttu-id="dc270-119">`AssemblyRef`このアセンブリが参照するアセンブリごとに1つのメタデータ構造を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc270-119">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="dc270-120">実行時には、参照されたアセンブリの詳細がアセンブリリゾルバーに渡され、"ビルド済み" の情報を表すことが示されます。</span><span class="sxs-lookup"><span data-stu-id="dc270-120">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="dc270-121">次に、アセンブリリゾルバーがポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="dc270-121">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc270-122">要件</span><span class="sxs-lookup"><span data-stu-id="dc270-122">Requirements</span></span>  

 <span data-ttu-id="dc270-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc270-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc270-124">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="dc270-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc270-125">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="dc270-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc270-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc270-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc270-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc270-127">See also</span></span>

- [<span data-ttu-id="dc270-128">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc270-128">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)

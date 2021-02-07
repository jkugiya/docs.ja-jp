---
description: 詳細については、「IMetaDataImport2 インターフェイス」を参照してください。
title: IMetaDataImport2 インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
ms.openlocfilehash: de1b190ae174c6028e4f116d7f6fc0b9af0aac6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688547"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="8b082-103">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b082-103">IMetaDataImport2 Interface</span></span>

<span data-ttu-id="8b082-104">[IMetaDataImport](imetadataimport-interface.md)インターフェイスを拡張して、ジェネリック型を処理する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="8b082-104">Extends the [IMetaDataImport](imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b082-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8b082-105">Methods</span></span>  
  
|<span data-ttu-id="8b082-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8b082-106">Method</span></span>|<span data-ttu-id="8b082-107">説明</span><span class="sxs-lookup"><span data-stu-id="8b082-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b082-108">EnumGenericParamConstraints メソッド</span><span class="sxs-lookup"><span data-stu-id="8b082-108">EnumGenericParamConstraints Method</span></span>](imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="8b082-109">指定したトークンによって表されるジェネリックパラメーターに関連付けられているジェネリックパラメーター制約の配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8b082-109">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="8b082-110">EnumGenericParams メソッド</span><span class="sxs-lookup"><span data-stu-id="8b082-110">EnumGenericParams Method</span></span>](imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="8b082-111">指定した TypeDef または MethodDef トークンに関連付けられているジェネリックパラメータートークンの配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8b082-111">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="8b082-112">EnumMethodSpecs メソッド</span><span class="sxs-lookup"><span data-stu-id="8b082-112">EnumMethodSpecs Method</span></span>](imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="8b082-113">指定した MethodDef または MemberRef トークンに関連付けられている MethodSpec トークンの配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8b082-113">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="8b082-114">GetGenericParamConstraintProps メソッド</span><span class="sxs-lookup"><span data-stu-id="8b082-114">GetGenericParamConstraintProps Method</span></span>](imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="8b082-115">指定された制約トークンによって表されるジェネリックパラメーター制約に関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="8b082-115">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="8b082-116">GetGenericParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="8b082-116">GetGenericParamProps Method</span></span>](imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="8b082-117">指定したトークンによって表されるジェネリックパラメーターに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="8b082-117">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="8b082-118">GetMethodSpecProps メソッド</span><span class="sxs-lookup"><span data-stu-id="8b082-118">GetMethodSpecProps Method</span></span>](imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="8b082-119">指定した MethodSpec トークンによって参照されるメソッドのメタデータシグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="8b082-119">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="8b082-120">GetPEKind メソッド</span><span class="sxs-lookup"><span data-stu-id="8b082-120">GetPEKind Method</span></span>](imetadataimport2-getpekind-method.md)|<span data-ttu-id="8b082-121">移植可能な実行可能 (PE) ファイルのコードの性質を示す値を取得します。通常は、現在のメタデータスコープで定義されている DLL または EXE ファイルです。</span><span class="sxs-lookup"><span data-stu-id="8b082-121">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="8b082-122">GetVersionString メソッド</span><span class="sxs-lookup"><span data-stu-id="8b082-122">GetVersionString Method</span></span>](imetadataimport2-getversionstring-method.md)|<span data-ttu-id="8b082-123">アセンブリのビルドに使用されたランタイムのバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="8b082-123">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b082-124">要件</span><span class="sxs-lookup"><span data-stu-id="8b082-124">Requirements</span></span>  

 <span data-ttu-id="8b082-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b082-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b082-126">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8b082-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b082-127">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="8b082-127">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b082-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b082-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b082-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b082-129">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="8b082-130">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b082-130">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="8b082-131">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b082-131">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)

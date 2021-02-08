---
description: 詳細については、「IMetaDataConverter インターフェイス」を参照してください。
title: IMetaDataConverter インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
ms.openlocfilehash: 6ed84083bad924e760c576afe485bd7ccad012cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789256"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="cf5b0-103">IMetaDataConverter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf5b0-103">IMetaDataConverter Interface</span></span>

<span data-ttu-id="cf5b0-104">タイプ ライブラリをそれぞれのメタデータ署名にマップして、一方から他方に変換するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="cf5b0-104">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf5b0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cf5b0-105">Methods</span></span>  
  
|<span data-ttu-id="cf5b0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="cf5b0-106">Method</span></span>|<span data-ttu-id="cf5b0-107">説明</span><span class="sxs-lookup"><span data-stu-id="cf5b0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf5b0-108">GetMetaDataFromTypeInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="cf5b0-108">GetMetaDataFromTypeInfo Method</span></span>](imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="cf5b0-109">指定したインスタンスによって参照されるタイプライブラリのメタデータシグネチャを表す [IMetaDataImport](imetadataimport-interface.md) インスタンスへのポインターを取得し `ITypeInfo` ます。</span><span class="sxs-lookup"><span data-stu-id="cf5b0-109">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="cf5b0-110">GetMetaDataFromTypeLib メソッド</span><span class="sxs-lookup"><span data-stu-id="cf5b0-110">GetMetaDataFromTypeLib Method</span></span>](imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="cf5b0-111">`IMetaDataImport`指定したインスタンスによって表されるタイプライブラリのメタデータ署名を表すインスタンスへのポインターを取得し `ITypeLib` ます。</span><span class="sxs-lookup"><span data-stu-id="cf5b0-111">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="cf5b0-112">GetTypeLibFromMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="cf5b0-112">GetTypeLibFromMetaData Method</span></span>](imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="cf5b0-113">指定した `ITypeLib` モジュール名およびライブラリ名を持つタイプライブラリを表すインスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="cf5b0-113">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf5b0-114">要件</span><span class="sxs-lookup"><span data-stu-id="cf5b0-114">Requirements</span></span>  

 <span data-ttu-id="cf5b0-115">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf5b0-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf5b0-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="cf5b0-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf5b0-117">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="cf5b0-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf5b0-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf5b0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf5b0-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf5b0-119">See also</span></span>

- [<span data-ttu-id="cf5b0-120">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf5b0-120">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="cf5b0-121">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf5b0-121">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)

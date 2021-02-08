---
description: '詳細については、次を参照してください: CorGenericParamAttr 列挙型'
title: CorGenericParamAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
ms.openlocfilehash: 8fe8cb20834ecbc5477bbe8b01bf77d6b1af0eea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784458"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="8c000-103">CorGenericParamAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="8c000-103">CorGenericParamAttr Enumeration</span></span>

<span data-ttu-id="8c000-104"><xref:System.Type> [IMetaDataEmit2::D efineGenericParam](imetadataemit2-definegenericparam-method.md)の呼び出しで使用される、ジェネリック型のパラメーターを記述する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="8c000-104">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c000-105">構文</span><span class="sxs-lookup"><span data-stu-id="8c000-105">Syntax</span></span>  
  
```cpp  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="8c000-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="8c000-106">Members</span></span>  
  
|<span data-ttu-id="8c000-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="8c000-107">Member</span></span>|<span data-ttu-id="8c000-108">説明</span><span class="sxs-lookup"><span data-stu-id="8c000-108">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="8c000-109">パラメーターの分散は、インターフェイスとデリゲートのジェネリックパラメーターにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8c000-109">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="8c000-110">分散が存在しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="8c000-110">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="8c000-111">共変性を示します。</span><span class="sxs-lookup"><span data-stu-id="8c000-111">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="8c000-112">反変性を示します。</span><span class="sxs-lookup"><span data-stu-id="8c000-112">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="8c000-113">特殊な制約は、任意のパラメーターに適用でき <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="8c000-113">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="8c000-114">パラメーターに制約が適用されないことを示し <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="8c000-114">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="8c000-115">パラメーターが参照型である必要があることを示し <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="8c000-115">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="8c000-116"><xref:System.Type>パラメーターが null 値にできない値型である必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="8c000-116">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="8c000-117">パラメーターを受け取らない既定のパブリックコンストラクターがパラメーターに必要であることを示し <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="8c000-117">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c000-118">要件</span><span class="sxs-lookup"><span data-stu-id="8c000-118">Requirements</span></span>  

 <span data-ttu-id="8c000-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c000-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c000-120">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="8c000-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8c000-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c000-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c000-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c000-122">See also</span></span>

- [<span data-ttu-id="8c000-123">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="8c000-123">Metadata Enumerations</span></span>](metadata-enumerations.md)

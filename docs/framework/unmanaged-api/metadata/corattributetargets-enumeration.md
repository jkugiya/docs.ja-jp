---
description: '詳細については、次を参照してください: CorAttributeTargets 列挙型'
title: CorAttributeTargets 列挙型
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: 6f80df31b9da8591fac3d979ede1e9bf0f8ecfc4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678498"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="32bd1-103">CorAttributeTargets 列挙型</span><span class="sxs-lookup"><span data-stu-id="32bd1-103">CorAttributeTargets Enumeration</span></span>

<span data-ttu-id="32bd1-104">属性を適用できるアプリケーション要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="32bd1-104">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32bd1-105">構文</span><span class="sxs-lookup"><span data-stu-id="32bd1-105">Syntax</span></span>  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =
        catAssembly | catModule | catClass | catStruct |
        catEnum | catConstructor | catMethod | catProperty |
        catField | catEvent | catInterface | catParameter |
        catDelegate | catGenericParameter,  
  
    catClassMembers        =
        catClass | catStruct | catEnum | catConstructor |
        catMethod | catProperty | catField | catEvent |
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a><span data-ttu-id="32bd1-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="32bd1-106">Members</span></span>  
  
|<span data-ttu-id="32bd1-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="32bd1-107">Member</span></span>|<span data-ttu-id="32bd1-108">説明</span><span class="sxs-lookup"><span data-stu-id="32bd1-108">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="32bd1-109">アセンブリに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-109">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="32bd1-110">属性は、移植可能な実行可能ファイル (.dll または .exe) モジュールに適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-110">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="32bd1-111">クラスに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-111">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="32bd1-112">構造体、つまり、値型に属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-112">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="32bd1-113">列挙体に属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-113">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="32bd1-114">コンストラクターに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-114">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="32bd1-115">メソッドに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-115">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="32bd1-116">プロパティに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-116">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="32bd1-117">フィールドに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-117">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="32bd1-118">イベントに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-118">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="32bd1-119">インターフェイスに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-119">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="32bd1-120">パラメーターに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-120">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="32bd1-121">デリゲートに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-121">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="32bd1-122">ジェネリック パラメーターに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-122">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="32bd1-123">任意のアプリケーション要素に属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-123">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="32bd1-124">属性は、クラスのメンバーに適用できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-124">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32bd1-125">解説</span><span class="sxs-lookup"><span data-stu-id="32bd1-125">Remarks</span></span>  

 <span data-ttu-id="32bd1-126">`CorAttributeTargets`列挙値をビットごとの or 演算と組み合わせて、適切な組み合わせを取得できます。</span><span class="sxs-lookup"><span data-stu-id="32bd1-126">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="32bd1-127">は、 `CorAttributeTargets` マネージ列挙に似て <xref:System.AttributeTargets?displayProperty=nameWithType> います。</span><span class="sxs-lookup"><span data-stu-id="32bd1-127">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32bd1-128">要件</span><span class="sxs-lookup"><span data-stu-id="32bd1-128">Requirements</span></span>  

 <span data-ttu-id="32bd1-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32bd1-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32bd1-130">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="32bd1-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="32bd1-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32bd1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32bd1-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="32bd1-132">See also</span></span>

- [<span data-ttu-id="32bd1-133">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="32bd1-133">Metadata Enumerations</span></span>](metadata-enumerations.md)

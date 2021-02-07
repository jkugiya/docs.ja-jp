---
description: 詳細については、「CorSerializationType 列挙型」を参照してください。
title: CorSerializationType 列挙型
ms.date: 03/30/2017
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
ms.openlocfilehash: 86df23bf03037d329a3138798725058f1d24a450
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707385"
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="73d51-103">CorSerializationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="73d51-103">CorSerializationType Enumeration</span></span>

<span data-ttu-id="73d51-104">共通言語ランタイムによってオブジェクトをシリアル化する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="73d51-104">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73d51-105">構文</span><span class="sxs-lookup"><span data-stu-id="73d51-105">Syntax</span></span>  
  
```cpp  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a><span data-ttu-id="73d51-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="73d51-106">Members</span></span>  
  
|<span data-ttu-id="73d51-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="73d51-107">Member</span></span>|<span data-ttu-id="73d51-108">説明</span><span class="sxs-lookup"><span data-stu-id="73d51-108">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="73d51-109">オブジェクトのシリアル化が定義されていません。</span><span class="sxs-lookup"><span data-stu-id="73d51-109">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="73d51-110">オブジェクトはブール型としてシリアル化されます</span><span class="sxs-lookup"><span data-stu-id="73d51-110">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="73d51-111">オブジェクトは文字型としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-111">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="73d51-112">オブジェクトは符号付き1バイト整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-112">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="73d51-113">オブジェクトは、符号なし1バイト整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-113">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="73d51-114">オブジェクトは、符号付き2バイト整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-114">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="73d51-115">オブジェクトは、符号なし2バイト整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-115">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="73d51-116">オブジェクトは、符号付き4バイト整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-116">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="73d51-117">オブジェクトは、4バイトの符号なし整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-117">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="73d51-118">オブジェクトは、符号付き8バイト整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-118">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="73d51-119">オブジェクトは、8バイトの符号なし整数としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-119">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="73d51-120">オブジェクトは、4バイトの浮動小数点としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-120">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="73d51-121">オブジェクトは8バイト浮動小数点としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-121">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="73d51-122">オブジェクトは System.string 型としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-122">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="73d51-123">オブジェクトは、1次元の下限の配列としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-123">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="73d51-124">オブジェクトは、ジェネリック型としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-124">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="73d51-125">オブジェクトはタグ付きオブジェクトとしてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-125">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="73d51-126">オブジェクトはフィールドとしてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-126">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="73d51-127">オブジェクトはプロパティとしてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-127">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="73d51-128">オブジェクトは列挙体としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="73d51-128">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73d51-129">要件</span><span class="sxs-lookup"><span data-stu-id="73d51-129">Requirements</span></span>  

 <span data-ttu-id="73d51-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73d51-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73d51-131">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="73d51-131">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="73d51-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73d51-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73d51-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="73d51-133">See also</span></span>

- [<span data-ttu-id="73d51-134">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="73d51-134">Metadata Enumerations</span></span>](metadata-enumerations.md)

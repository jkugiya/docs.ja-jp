---
description: 詳細については、「CorTypeAttr 列挙型」を参照してください。
title: CorTypeAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
ms.openlocfilehash: d4f7d25ce8ead945790defae800b7a45dc88bc38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721166"
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="e4f10-103">CorTypeAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="e4f10-103">CorTypeAttr Enumeration</span></span>

<span data-ttu-id="e4f10-104">メタデータ型を示す値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="e4f10-104">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4f10-105">構文</span><span class="sxs-lookup"><span data-stu-id="e4f10-105">Syntax</span></span>  
  
```cpp  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="e4f10-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e4f10-106">Members</span></span>  
  
|<span data-ttu-id="e4f10-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="e4f10-107">Member</span></span>|<span data-ttu-id="e4f10-108">説明</span><span class="sxs-lookup"><span data-stu-id="e4f10-108">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="e4f10-109">型の可視性情報に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e4f10-109">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="e4f10-110">型がパブリックスコープ内にないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-110">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="e4f10-111">型がパブリックスコープ内にあることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-111">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="e4f10-112">型がパブリックの可視性で入れ子になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-112">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="e4f10-113">型がプライベート可視性で入れ子になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-113">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="e4f10-114">型がファミリの可視性で入れ子になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-114">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="e4f10-115">型がアセンブリの可視性で入れ子になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-115">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="e4f10-116">型がファミリおよびアセンブリの可視性で入れ子になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-116">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="e4f10-117">型が、ファミリまたはアセンブリの参照可能範囲に入れ子になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-117">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="e4f10-118">型のレイアウト情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-118">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="e4f10-119">この型のフィールドが自動的にレイアウトされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-119">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="e4f10-120">この型のフィールドを順番に配置することを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-120">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="e4f10-121">フィールドレイアウトが明示的に指定されていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-121">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="e4f10-122">型に関するセマンティック情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-122">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="e4f10-123">型がクラスであることを示します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-123">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="e4f10-124">型がインターフェイスであることを示します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-124">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="e4f10-125">型が抽象的であることを示します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-125">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="e4f10-126">型を拡張できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-126">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="e4f10-127">クラス名が特別であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-127">Specifies that the class name is special.</span></span> <span data-ttu-id="e4f10-128">その名前は、方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-128">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="e4f10-129">型がインポートされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-129">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="e4f10-130">型がシリアル化可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-130">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="e4f10-131">この型が Windows ランタイム型であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-131">Specifies that this type is a Windows Runtime type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="e4f10-132">文字列をエンコードおよび書式設定する方法に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-132">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="e4f10-133">この型が LPTSTR を ANSI と解釈することを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-133">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="e4f10-134">この型が LPTSTR を Unicode として解釈することを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-134">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="e4f10-135">この型が LPTSTR を自動的に解釈することを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-135">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="e4f10-136">によって指定された標準以外のエンコーディングを型が持つことを指定し `CustomFormatMask` ます。</span><span class="sxs-lookup"><span data-stu-id="e4f10-136">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="e4f10-137">ネイティブ相互運用機能の非標準のエンコード情報を取得するには、このマスクを使用します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-137">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="e4f10-138">これら2つのビットの値の意味は、指定されていません。</span><span class="sxs-lookup"><span data-stu-id="e4f10-138">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="e4f10-139">静的フィールドに最初にアクセスしようとする前に型を初期化する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-139">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="e4f10-140">型がエクスポートされ、型フォワーダーが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-140">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="e4f10-141">このフラグと以下のフラグは、共通言語ランタイムによって内部的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e4f10-141">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="e4f10-142">共通言語ランタイムが名前のエンコーディングを確認する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-142">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="e4f10-143">型にセキュリティが関連付けられていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4f10-143">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4f10-144">要件</span><span class="sxs-lookup"><span data-stu-id="e4f10-144">Requirements</span></span>  

 <span data-ttu-id="e4f10-145">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4f10-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4f10-146">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="e4f10-146">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e4f10-147">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4f10-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f10-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4f10-148">See also</span></span>

- [<span data-ttu-id="e4f10-149">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="e4f10-149">Metadata Enumerations</span></span>](metadata-enumerations.md)

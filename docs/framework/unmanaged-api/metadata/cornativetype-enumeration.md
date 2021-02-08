---
description: '詳細については、次を参照してください: CorNativeType 列挙型'
title: CorNativeType 列挙型
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
ms.openlocfilehash: d2313eef124f3308c4792b47da8b7c8bba984597
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784328"
---
# <a name="cornativetype-enumeration"></a><span data-ttu-id="61a29-103">CorNativeType 列挙型</span><span class="sxs-lookup"><span data-stu-id="61a29-103">CorNativeType Enumeration</span></span>

<span data-ttu-id="61a29-104">ネイティブのアンマネージ型を記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="61a29-104">Contains values that describe native unmanaged types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61a29-105">構文</span><span class="sxs-lookup"><span data-stu-id="61a29-105">Syntax</span></span>  
  
```cpp  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a><span data-ttu-id="61a29-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="61a29-106">Members</span></span>  
  
|<span data-ttu-id="61a29-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="61a29-107">Member</span></span>|<span data-ttu-id="61a29-108">説明</span><span class="sxs-lookup"><span data-stu-id="61a29-108">Description</span></span>|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|<span data-ttu-id="61a29-109">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="61a29-109">Obsolete.</span></span>|  
|`NATIVE_TYPE_VOID`|<span data-ttu-id="61a29-110">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="61a29-110">Obsolete.</span></span>|  
|`NATIVE_TYPE_BOOLEAN`|<span data-ttu-id="61a29-111">4バイトのブール値。 TRUE は0以外で、FALSE は0です。</span><span class="sxs-lookup"><span data-stu-id="61a29-111">A 4-byte Boolean value, where TRUE is non-zero and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_I1`|<span data-ttu-id="61a29-112">符号付き8ビット整数値。</span><span class="sxs-lookup"><span data-stu-id="61a29-112">A signed 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_U1`|<span data-ttu-id="61a29-113">8ビットの符号なし整数値。</span><span class="sxs-lookup"><span data-stu-id="61a29-113">An unsigned 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_I2`|<span data-ttu-id="61a29-114">符号付き16ビット整数値。</span><span class="sxs-lookup"><span data-stu-id="61a29-114">A signed 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_U2`|<span data-ttu-id="61a29-115">符号なし16ビット整数値です。</span><span class="sxs-lookup"><span data-stu-id="61a29-115">An unsigned 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_I4`|<span data-ttu-id="61a29-116">符号付き 32 ビット整数値。</span><span class="sxs-lookup"><span data-stu-id="61a29-116">A signed 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_U4`|<span data-ttu-id="61a29-117">32 ビットの符号なし整数値。</span><span class="sxs-lookup"><span data-stu-id="61a29-117">An unsigned 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_I8`|<span data-ttu-id="61a29-118">64ビットの符号付き整数値。</span><span class="sxs-lookup"><span data-stu-id="61a29-118">A signed 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_U8`|<span data-ttu-id="61a29-119">64ビットの符号なし整数値。</span><span class="sxs-lookup"><span data-stu-id="61a29-119">An unsigned 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_R4`|<span data-ttu-id="61a29-120">4バイト浮動小数点数値。</span><span class="sxs-lookup"><span data-stu-id="61a29-120">A 4-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_R8`|<span data-ttu-id="61a29-121">8バイト浮動小数点数値。</span><span class="sxs-lookup"><span data-stu-id="61a29-121">An 8-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_SYSCHAR`|<span data-ttu-id="61a29-122">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="61a29-122">Obsolete.</span></span>|  
|`NATIVE_TYPE_VARIANT`|<span data-ttu-id="61a29-123">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="61a29-123">Obsolete.</span></span>|  
|`NATIVE_TYPE_CURRENCY`|<span data-ttu-id="61a29-124">マネージ型に対応する数値 COM 型 <xref:System.Decimal> 。</span><span class="sxs-lookup"><span data-stu-id="61a29-124">A numeric COM type that corresponds to the managed <xref:System.Decimal> type.</span></span>|  
|`NATIVE_TYPE_PTR`|<span data-ttu-id="61a29-125">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="61a29-125">Obsolete.</span></span>|  
|`NATIVE_TYPE_DECIMAL`|<span data-ttu-id="61a29-126">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="61a29-126">Obsolete.</span></span>|  
|`NATIVE_TYPE_DATE`|<span data-ttu-id="61a29-127">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="61a29-127">Obsolete.</span></span>|  
|`NATIVE_TYPE_BSTR`|<span data-ttu-id="61a29-128">「COM 相互運用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61a29-128">COM Interop.</span></span>|  
|`NATIVE_TYPE_LPSTR`|<span data-ttu-id="61a29-129">LPSTR 文字列値。</span><span class="sxs-lookup"><span data-stu-id="61a29-129">An LPSTR string value.</span></span>|  
|`NATIVE_TYPE_LPWSTR`|<span data-ttu-id="61a29-130">LPWSTR 文字列値。</span><span class="sxs-lookup"><span data-stu-id="61a29-130">An LPWSTR string value.</span></span>|  
|`NATIVE_TYPE_LPTSTR`|<span data-ttu-id="61a29-131">LPTSTR 文字列値。</span><span class="sxs-lookup"><span data-stu-id="61a29-131">An LPTSTR string value.</span></span>|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|<span data-ttu-id="61a29-132">システム定義の固定文字列値。</span><span class="sxs-lookup"><span data-stu-id="61a29-132">A fixed, system-defined string value.</span></span>|  
|`NATIVE_TYPE_OBJECTREF`|<span data-ttu-id="61a29-133">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="61a29-133">Obsolete.</span></span>|  
|`NATIVE_TYPE_IUNKNOWN`|<span data-ttu-id="61a29-134">「COM 相互運用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61a29-134">COM Interop.</span></span>|  
|`NATIVE_TYPE_IDISPATCH`|<span data-ttu-id="61a29-135">「COM 相互運用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61a29-135">COM Interop.</span></span>|  
|`NATIVE_TYPE_STRUCT`|<span data-ttu-id="61a29-136">ネイティブ構造体の値。</span><span class="sxs-lookup"><span data-stu-id="61a29-136">A native structure value.</span></span>|  
|`NATIVE_TYPE_INTF`|<span data-ttu-id="61a29-137">「COM 相互運用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61a29-137">COM Interop.</span></span>|  
|`NATIVE_TYPE_SAFEARRAY`|<span data-ttu-id="61a29-138">「COM 相互運用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61a29-138">COM Interop.</span></span>|  
|`NATIVE_TYPE_FIXEDARRAY`|<span data-ttu-id="61a29-139">固定長配列値。</span><span class="sxs-lookup"><span data-stu-id="61a29-139">A fixed-length array value.</span></span>|  
|`NATIVE_TYPE_INT`|<span data-ttu-id="61a29-140">ネイティブ16ビット符号付き整数値。</span><span class="sxs-lookup"><span data-stu-id="61a29-140">A native 16-bit signed integer value.</span></span>|  
|`NATIVE_TYPE_UINT`|<span data-ttu-id="61a29-141">ネイティブ16ビット符号なし整数値。</span><span class="sxs-lookup"><span data-stu-id="61a29-141">A native 16-bit unsigned integer value.</span></span>|  
|`NATIVE_TYPE_NESTEDSTRUCT`|<span data-ttu-id="61a29-142">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="61a29-142">Obsolete.</span></span><br /><br /> <span data-ttu-id="61a29-143">NATIVE_TYPE_STRUCT を使用します。</span><span class="sxs-lookup"><span data-stu-id="61a29-143">Use NATIVE_TYPE_STRUCT.</span></span>|  
|`NATIVE_TYPE_BYVALSTR`|<span data-ttu-id="61a29-144">「COM 相互運用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61a29-144">COM Interop.</span></span>|  
|`NATIVE_TYPE_ANSIBSTR`|<span data-ttu-id="61a29-145">「COM 相互運用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61a29-145">COM Interop.</span></span>|  
|`NATIVE_TYPE_TBSTR`|<span data-ttu-id="61a29-146">「COM 相互運用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61a29-146">COM Interop.</span></span><br /><br /> <span data-ttu-id="61a29-147">プラットフォームに応じて、BSTR または ANSIBSTR を選択します。</span><span class="sxs-lookup"><span data-stu-id="61a29-147">Select BSTR or ANSIBSTR depending on the platform.</span></span>|  
|`NATIVE_TYPE_VARIANTBOOL`|<span data-ttu-id="61a29-148">2バイトのブール値。 TRUE は-1、FALSE は0です。</span><span class="sxs-lookup"><span data-stu-id="61a29-148">A 2-byte Boolean value, where TRUE is -1 and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_FUNC`|<span data-ttu-id="61a29-149">関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="61a29-149">A function pointer.</span></span>|  
|`NATIVE_TYPE_ASANY`|<span data-ttu-id="61a29-150">任意のネイティブ型への参照。</span><span class="sxs-lookup"><span data-stu-id="61a29-150">A reference to any native type.</span></span>|  
|`NATIVE_TYPE_ARRAY`|<span data-ttu-id="61a29-151">指定されていない型のメンバーを持つ配列への参照。</span><span class="sxs-lookup"><span data-stu-id="61a29-151">A reference to an array with members of an unspecified type.</span></span>|  
|`NATIVE_TYPE_LPSTRUCT`|<span data-ttu-id="61a29-152">構造体への32ビット整数ポインター。</span><span class="sxs-lookup"><span data-stu-id="61a29-152">A 32-bit integer pointer to a structure.</span></span>|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|<span data-ttu-id="61a29-153">カスタムマーシャラーネイティブ型。</span><span class="sxs-lookup"><span data-stu-id="61a29-153">A custom marshaler native type.</span></span><br /><br /> <span data-ttu-id="61a29-154">この後には、"ネイティブ型名/0Custom marshaler 型名/0Custom cookie/0" または "{ネイティブ型 GUID}/0Custom marshaler 型名/0Custom cookie/0" という形式の文字列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61a29-154">This must be followed by a string of the following format: "Native type name/0Custom marshaler type name/0Optional cookie/0" or "{Native type GUID}/0Custom marshaler type name/0Optional cookie/0"</span></span>|  
|`NATIVE_TYPE_ERROR`|<span data-ttu-id="61a29-155">「COM 相互運用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61a29-155">COM Interop.</span></span><br /><br /> <span data-ttu-id="61a29-156">ELEMENT_TYPE_I4 この型は VT_HRESULT にマップされます。</span><span class="sxs-lookup"><span data-stu-id="61a29-156">With ELEMENT_TYPE_I4 this type maps to VT_HRESULT.</span></span>|  
|`NATIVE_TYPE_IINSPECTABLE`|<span data-ttu-id="61a29-157">ネイティブ `IInspectable` 型。</span><span class="sxs-lookup"><span data-stu-id="61a29-157">A native `IInspectable` type.</span></span>|  
|`NATIVE_TYPE_HSTRING`|<span data-ttu-id="61a29-158">ネイティブ `HString` 。</span><span class="sxs-lookup"><span data-stu-id="61a29-158">A native `HString`.</span></span>|  
|`NATIVE_TYPE_MAX`|<span data-ttu-id="61a29-159">無効な値。</span><span class="sxs-lookup"><span data-stu-id="61a29-159">An invalid value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61a29-160">要件</span><span class="sxs-lookup"><span data-stu-id="61a29-160">Requirements</span></span>  

 <span data-ttu-id="61a29-161">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61a29-161">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61a29-162">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="61a29-162">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="61a29-163">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61a29-163">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a29-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="61a29-164">See also</span></span>

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [<span data-ttu-id="61a29-165">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="61a29-165">Metadata Enumerations</span></span>](metadata-enumerations.md)

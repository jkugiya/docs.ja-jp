---
description: '詳細については、次を参照してください: CorElementType 列挙型'
title: CorElementType 列挙型
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
ms.openlocfilehash: 3eaf75a6d2094ec875ab1861aac49e4382e65801
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784536"
---
# <a name="corelementtype-enumeration"></a><span data-ttu-id="c72a5-103">CorElementType 列挙型</span><span class="sxs-lookup"><span data-stu-id="c72a5-103">CorElementType Enumeration</span></span>

<span data-ttu-id="c72a5-104">共通言語ランタイム <xref:System.Type> 、型修飾子、またはメタデータ型シグネチャの型に関する情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="c72a5-104">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>

## <a name="syntax"></a><span data-ttu-id="c72a5-105">構文</span><span class="sxs-lookup"><span data-stu-id="c72a5-105">Syntax</span></span>

```cpp
typedef enum CorElementType {
    ELEMENT_TYPE_END            = 0x0,
    ELEMENT_TYPE_VOID           = 0x1,
    ELEMENT_TYPE_BOOLEAN        = 0x2,
    ELEMENT_TYPE_CHAR           = 0x3,
    ELEMENT_TYPE_I1             = 0x4,
    ELEMENT_TYPE_U1             = 0x5,
    ELEMENT_TYPE_I2             = 0x6,
    ELEMENT_TYPE_U2             = 0x7,
    ELEMENT_TYPE_I4             = 0x8,
    ELEMENT_TYPE_U4             = 0x9,
    ELEMENT_TYPE_I8             = 0xa,
    ELEMENT_TYPE_U8             = 0xb,
    ELEMENT_TYPE_R4             = 0xc,
    ELEMENT_TYPE_R8             = 0xd,
    ELEMENT_TYPE_STRING         = 0xe,

    ELEMENT_TYPE_PTR            = 0xf,
    ELEMENT_TYPE_BYREF          = 0x10,

    ELEMENT_TYPE_VALUETYPE      = 0x11,
    ELEMENT_TYPE_CLASS          = 0x12,
    ELEMENT_TYPE_VAR            = 0x13,
    ELEMENT_TYPE_ARRAY          = 0x14,
    ELEMENT_TYPE_GENERICINST    = 0x15,
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,

    ELEMENT_TYPE_I              = 0x18,
    ELEMENT_TYPE_U              = 0x19,
    ELEMENT_TYPE_FNPTR          = 0x1B,
    ELEMENT_TYPE_OBJECT         = 0x1C,
    ELEMENT_TYPE_SZARRAY        = 0x1D,
    ELEMENT_TYPE_MVAR           = 0x1e,

    ELEMENT_TYPE_CMOD_REQD      = 0x1F,
    ELEMENT_TYPE_CMOD_OPT       = 0x20,

    ELEMENT_TYPE_INTERNAL       = 0x21,
    ELEMENT_TYPE_MAX            = 0x22,

    ELEMENT_TYPE_MODIFIER       = 0x40,
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER

} CorElementType;
```

## <a name="members"></a><span data-ttu-id="c72a5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c72a5-106">Members</span></span>

|<span data-ttu-id="c72a5-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="c72a5-107">Member</span></span>|<span data-ttu-id="c72a5-108">説明</span><span class="sxs-lookup"><span data-stu-id="c72a5-108">Description</span></span>|
|------------|-----------------|
|`ELEMENT_TYPE_END`|<span data-ttu-id="c72a5-109">内部使用。</span><span class="sxs-lookup"><span data-stu-id="c72a5-109">Used internally.</span></span>|
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="c72a5-110">Void 型。</span><span class="sxs-lookup"><span data-stu-id="c72a5-110">A void type.</span></span>|
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="c72a5-111">ブール型</span><span class="sxs-lookup"><span data-stu-id="c72a5-111">A Boolean type</span></span>|
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="c72a5-112">文字型。</span><span class="sxs-lookup"><span data-stu-id="c72a5-112">A character type.</span></span>|
|`ELEMENT_TYPE_I1`|<span data-ttu-id="c72a5-113">符号付き1バイト整数。</span><span class="sxs-lookup"><span data-stu-id="c72a5-113">A signed 1-byte integer.</span></span>|
|`ELEMENT_TYPE_U1`|<span data-ttu-id="c72a5-114">1 バイトの符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="c72a5-114">An unsigned 1-byte integer.</span></span>|
|`ELEMENT_TYPE_I2`|<span data-ttu-id="c72a5-115">符号付き2バイト整数。</span><span class="sxs-lookup"><span data-stu-id="c72a5-115">A signed 2-byte integer.</span></span>|
|`ELEMENT_TYPE_U2`|<span data-ttu-id="c72a5-116">符号なし2バイト整数。</span><span class="sxs-lookup"><span data-stu-id="c72a5-116">An unsigned 2-byte integer.</span></span>|
|`ELEMENT_TYPE_I4`|<span data-ttu-id="c72a5-117">4バイトの符号付き整数。</span><span class="sxs-lookup"><span data-stu-id="c72a5-117">A signed 4-byte integer.</span></span>|
|`ELEMENT_TYPE_U4`|<span data-ttu-id="c72a5-118">4バイトの符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="c72a5-118">An unsigned 4-byte integer.</span></span>|
|`ELEMENT_TYPE_I8`|<span data-ttu-id="c72a5-119">8バイトの符号付き整数。</span><span class="sxs-lookup"><span data-stu-id="c72a5-119">A signed 8-byte integer.</span></span>|
|`ELEMENT_TYPE_U8`|<span data-ttu-id="c72a5-120">8バイトの符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="c72a5-120">An unsigned 8-byte integer.</span></span>|
|`ELEMENT_TYPE_R4`|<span data-ttu-id="c72a5-121">4バイト浮動小数点。</span><span class="sxs-lookup"><span data-stu-id="c72a5-121">A 4-byte floating point.</span></span>|
|`ELEMENT_TYPE_R8`|<span data-ttu-id="c72a5-122">8バイト浮動小数点。</span><span class="sxs-lookup"><span data-stu-id="c72a5-122">An 8-byte floating point.</span></span>|
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="c72a5-123">System.string 型。</span><span class="sxs-lookup"><span data-stu-id="c72a5-123">A System.String type.</span></span>|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="c72a5-124">ポインター型修飾子。</span><span class="sxs-lookup"><span data-stu-id="c72a5-124">A pointer type modifier.</span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="c72a5-125">参照型修飾子。</span><span class="sxs-lookup"><span data-stu-id="c72a5-125">A reference type modifier.</span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="c72a5-126">値型修飾子。</span><span class="sxs-lookup"><span data-stu-id="c72a5-126">A value type modifier.</span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="c72a5-127">クラス型修飾子。</span><span class="sxs-lookup"><span data-stu-id="c72a5-127">A class type modifier.</span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="c72a5-128">クラス変数の型修飾子。</span><span class="sxs-lookup"><span data-stu-id="c72a5-128">A class variable type modifier.</span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="c72a5-129">多次元配列型修飾子。</span><span class="sxs-lookup"><span data-stu-id="c72a5-129">A multi-dimensional array type modifier.</span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="c72a5-130">ジェネリック型の型修飾子。</span><span class="sxs-lookup"><span data-stu-id="c72a5-130">A type modifier for generic types.</span></span>|
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="c72a5-131">型指定された参照。</span><span class="sxs-lookup"><span data-stu-id="c72a5-131">A typed reference.</span></span>|
|`ELEMENT_TYPE_I`|<span data-ttu-id="c72a5-132">ネイティブ整数のサイズ。</span><span class="sxs-lookup"><span data-stu-id="c72a5-132">Size of a native integer.</span></span>|
|`ELEMENT_TYPE_U`|<span data-ttu-id="c72a5-133">符号なしネイティブ整数のサイズ。</span><span class="sxs-lookup"><span data-stu-id="c72a5-133">Size of an unsigned native integer.</span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="c72a5-134">関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c72a5-134">A pointer to a function.</span></span>|
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="c72a5-135">System.object 型。</span><span class="sxs-lookup"><span data-stu-id="c72a5-135">A System.Object type.</span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="c72a5-136">1次元の下限の配列型修飾子。</span><span class="sxs-lookup"><span data-stu-id="c72a5-136">A single-dimensional, zero lower-bound array type modifier.</span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="c72a5-137">メソッド変数の型修飾子。</span><span class="sxs-lookup"><span data-stu-id="c72a5-137">A method variable type modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="c72a5-138">C 言語で必要な修飾子。</span><span class="sxs-lookup"><span data-stu-id="c72a5-138">A C language required modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="c72a5-139">C 言語の省略可能な修飾子。</span><span class="sxs-lookup"><span data-stu-id="c72a5-139">A C language optional modifier.</span></span>|
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="c72a5-140">内部使用。</span><span class="sxs-lookup"><span data-stu-id="c72a5-140">Used internally.</span></span>|
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="c72a5-141">無効な型。</span><span class="sxs-lookup"><span data-stu-id="c72a5-141">An invalid type.</span></span>|
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="c72a5-142">内部使用。</span><span class="sxs-lookup"><span data-stu-id="c72a5-142">Used internally.</span></span>|
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="c72a5-143">可変個のパラメーターのリストの sentinel である型修飾子。</span><span class="sxs-lookup"><span data-stu-id="c72a5-143">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="c72a5-144">内部使用。</span><span class="sxs-lookup"><span data-stu-id="c72a5-144">Used internally.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c72a5-145">解説</span><span class="sxs-lookup"><span data-stu-id="c72a5-145">Remarks</span></span>

<span data-ttu-id="c72a5-146">型修飾子は、より複雑な型を表すための基礎となります。</span><span class="sxs-lookup"><span data-stu-id="c72a5-146">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="c72a5-147">型 `CorElementType` 修飾子の値は、型シグネチャの直後に続く値に適用されます。</span><span class="sxs-lookup"><span data-stu-id="c72a5-147">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="c72a5-148">型修飾子の値の後に続く値には、 `CorElementType` `CorElementType` 次の表に示すように、単純型の値、メタデータトークン、またはその他の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c72a5-148">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>

> [!NOTE]
> <span data-ttu-id="c72a5-149">すべての数値 (*数値*、 *引数の数*、 *メタデータトークン*、 *順位*、 *カウント*、および *バインド*) は、圧縮された整数として格納されます。</span><span class="sxs-lookup"><span data-stu-id="c72a5-149">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="c72a5-150">詳細については、ECMA Web サイトの「 [STANDARD ECMA-335-共通言語基盤 (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c72a5-150">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) on the ECMA Web site for details.</span></span>

|<span data-ttu-id="c72a5-151">型修飾子</span><span class="sxs-lookup"><span data-stu-id="c72a5-151">Type modifier</span></span>|<span data-ttu-id="c72a5-152">フォーマット</span><span class="sxs-lookup"><span data-stu-id="c72a5-152">Format</span></span>|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="c72a5-153">ELEMENT_TYPE_PTR \<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="c72a5-153">ELEMENT_TYPE_PTR \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="c72a5-154">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="c72a5-154">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="c72a5-155">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="c72a5-155">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="c72a5-156">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="c72a5-156">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="c72a5-157">ELEMENT_TYPE_VAR \<number></span><span class="sxs-lookup"><span data-stu-id="c72a5-157">ELEMENT_TYPE_VAR \<number></span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="c72a5-158">ELEMENT_TYPE_ARRAY.. \<a `CorElementType` value> \<rank> \<count1> \<bound1> . \<countN>\<boundN></span><span class="sxs-lookup"><span data-stu-id="c72a5-158">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="c72a5-159">ELEMENT_TYPE_GENERICINST.. \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> . \<argN></span><span class="sxs-lookup"><span data-stu-id="c72a5-159">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="c72a5-160">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span><span class="sxs-lookup"><span data-stu-id="c72a5-160">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="c72a5-161">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="c72a5-161">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="c72a5-162">ELEMENT_TYPE_MVAR \<number></span><span class="sxs-lookup"><span data-stu-id="c72a5-162">ELEMENT_TYPE_MVAR \<number></span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="c72a5-163">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="c72a5-163">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="c72a5-164">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="c72a5-164">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|

## <a name="requirements"></a><span data-ttu-id="c72a5-165">要件</span><span class="sxs-lookup"><span data-stu-id="c72a5-165">Requirements</span></span>

<span data-ttu-id="c72a5-166">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c72a5-166">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="c72a5-167">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="c72a5-167">**Header:** CorHdr.h</span></span>

<span data-ttu-id="c72a5-168">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c72a5-168">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c72a5-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="c72a5-169">See also</span></span>

- [<span data-ttu-id="c72a5-170">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="c72a5-170">Metadata Enumerations</span></span>](metadata-enumerations.md)

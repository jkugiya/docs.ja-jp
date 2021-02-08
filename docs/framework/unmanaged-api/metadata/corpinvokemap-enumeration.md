---
description: '詳細については、次を参照してください: CorPinvokeMap 列挙型'
title: CorPinvokeMap 列挙型
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: 8285632725096b4e6afc85fe54a89f12fc899dd1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784263"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="796cd-103">CorPinvokeMap 列挙型</span><span class="sxs-lookup"><span data-stu-id="796cd-103">CorPinvokeMap Enumeration</span></span>

<span data-ttu-id="796cd-104">PInvoke 呼び出しのオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="796cd-104">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="796cd-105">構文</span><span class="sxs-lookup"><span data-stu-id="796cd-105">Syntax</span></span>  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a><span data-ttu-id="796cd-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="796cd-106">Members</span></span>  
  
|<span data-ttu-id="796cd-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="796cd-107">Member</span></span>|<span data-ttu-id="796cd-108">説明</span><span class="sxs-lookup"><span data-stu-id="796cd-108">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="796cd-109">各メンバー名は、指定されたとおりに使用します。</span><span class="sxs-lookup"><span data-stu-id="796cd-109">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="796cd-110">予約済み。</span><span class="sxs-lookup"><span data-stu-id="796cd-110">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="796cd-111">予約済み。</span><span class="sxs-lookup"><span data-stu-id="796cd-111">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="796cd-112">マルチバイト文字として文字列をマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="796cd-112">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="796cd-113">Unicode 2 バイト文字として文字列をマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="796cd-113">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="796cd-114">対象オペレーティング システムに適するように、自動的に文字列をマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="796cd-114">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="796cd-115">既定値は、Windows NT、Windows 2000、Windows XP、および Windows Server 2003 ファミリの Unicode です。Windows 98 および Windows Me では、既定値は ANSI です。</span><span class="sxs-lookup"><span data-stu-id="796cd-115">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="796cd-116">予約済み。</span><span class="sxs-lookup"><span data-stu-id="796cd-116">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="796cd-117">ANSI 文字セットと完全に一致しない Unicode 文字の最適マッピングを実行します。</span><span class="sxs-lookup"><span data-stu-id="796cd-117">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="796cd-118">Unicode 文字の最適マッピングを実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="796cd-118">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="796cd-119">この場合、マップされていないすべての文字は、'? ' に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="796cd-119">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="796cd-120">予約済み。</span><span class="sxs-lookup"><span data-stu-id="796cd-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="796cd-121">予約済み。</span><span class="sxs-lookup"><span data-stu-id="796cd-121">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="796cd-122">相互運用マーシャラーがマップされていない文字を検出したときに、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="796cd-122">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="796cd-123">相互運用マーシャラーがマップ不可能な文字を検出した場合は、例外をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="796cd-123">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="796cd-124">予約済み</span><span class="sxs-lookup"><span data-stu-id="796cd-124">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="796cd-125">`SetLastError`属性付きメソッドから戻る前に、呼び出し先が Win32 関数を呼び出すことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="796cd-125">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="796cd-126">予約済み</span><span class="sxs-lookup"><span data-stu-id="796cd-126">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="796cd-127">既定のプラットフォーム呼び出し規約を使用します。</span><span class="sxs-lookup"><span data-stu-id="796cd-127">Use the default platform calling convention.</span></span> <span data-ttu-id="796cd-128">たとえば、Windows では、既定値はで `StdCall` あり、Windows CE .net ではです `Cdecl` 。</span><span class="sxs-lookup"><span data-stu-id="796cd-128">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="796cd-129">呼び出し規約を使用し `Cdecl` ます。</span><span class="sxs-lookup"><span data-stu-id="796cd-129">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="796cd-130">この場合、呼び出し元はスタックを消去します。</span><span class="sxs-lookup"><span data-stu-id="796cd-130">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="796cd-131">これにより `varargs` 、(つまり、可変個のパラメーターを受け取る関数) を使用して関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="796cd-131">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="796cd-132">呼び出し規約を使用し `StdCall` ます。</span><span class="sxs-lookup"><span data-stu-id="796cd-132">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="796cd-133">この場合、呼び出し先がスタックを消去します。</span><span class="sxs-lookup"><span data-stu-id="796cd-133">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="796cd-134">これは、プラットフォーム呼び出しでアンマネージ関数を呼び出すための既定の規約です。</span><span class="sxs-lookup"><span data-stu-id="796cd-134">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="796cd-135">呼び出し規約を使用し `ThisCall` ます。</span><span class="sxs-lookup"><span data-stu-id="796cd-135">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="796cd-136">この場合、最初のパラメーターはポインターであり、 `this` レジスタ ECX に格納されます。</span><span class="sxs-lookup"><span data-stu-id="796cd-136">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="796cd-137">その他のパラメーターは、スタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="796cd-137">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="796cd-138">`ThisCall`呼び出し規約は、アンマネージ DLL からエクスポートされたクラスのメソッドを呼び出すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="796cd-138">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="796cd-139">予約済み。</span><span class="sxs-lookup"><span data-stu-id="796cd-139">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="796cd-140">予約済み。</span><span class="sxs-lookup"><span data-stu-id="796cd-140">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="796cd-141">要件</span><span class="sxs-lookup"><span data-stu-id="796cd-141">Requirements</span></span>  

 <span data-ttu-id="796cd-142">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="796cd-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="796cd-143">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="796cd-143">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="796cd-144">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="796cd-144">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796cd-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="796cd-145">See also</span></span>

- [<span data-ttu-id="796cd-146">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="796cd-146">Metadata Enumerations</span></span>](metadata-enumerations.md)

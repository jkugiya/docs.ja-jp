---
description: '詳細については、次を参照してください: CeeSectionRelocType 列挙型'
title: CeeSectionRelocType 列挙型
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
ms.openlocfilehash: 49f7b39b3cc4c2e71dd3e4e426d0ca787e9ac0b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678836"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="56f09-103">CeeSectionRelocType 列挙型</span><span class="sxs-lookup"><span data-stu-id="56f09-103">CeeSectionRelocType Enumeration</span></span>

<span data-ttu-id="56f09-104">`reloc` [ICeeGen:: AddSectionReloc](iceegen-addsectionreloc-method.md)の呼び出しで生成された命令の種類に影響する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="56f09-104">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f09-105">構文</span><span class="sxs-lookup"><span data-stu-id="56f09-105">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a><span data-ttu-id="56f09-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="56f09-106">Members</span></span>  
  
|<span data-ttu-id="56f09-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="56f09-107">Member</span></span>|<span data-ttu-id="56f09-108">説明</span><span class="sxs-lookup"><span data-stu-id="56f09-108">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="56f09-109">は、セクションに対して相対的なを生成し `reloc` 、reloc セクションには何も送信しません。</span><span class="sxs-lookup"><span data-stu-id="56f09-109">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="56f09-110">`reloc`ポインターサイズの位置のを生成します。</span><span class="sxs-lookup"><span data-stu-id="56f09-110">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="56f09-111">これは、プラットフォームに応じて BASED_HIGHLOW または BASED_DIR64 に変換されます。</span><span class="sxs-lookup"><span data-stu-id="56f09-111">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="56f09-112">は、 `reloc` 32 ビットの数値の上位16ビットに対してを生成します。下位16ビットは、reloc テーブルの次の単語に含まれます。</span><span class="sxs-lookup"><span data-stu-id="56f09-112">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="56f09-113">トークンマップの再配置を生成し、reloc セクションに何も送信しません。</span><span class="sxs-lookup"><span data-stu-id="56f09-113">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="56f09-114">値が相対アドレスの修正であることを示します。</span><span class="sxs-lookup"><span data-stu-id="56f09-114">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="56f09-115">は、セクションに対して相対的なを生成し `reloc` 、reloc セクションには何も送信しません。</span><span class="sxs-lookup"><span data-stu-id="56f09-115">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="56f09-116">これは、セクションの `reloc` 仮想アドレスではなく、セクションのファイル位置に対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="56f09-116">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="56f09-117">コード相対アドレスのフィックスアップを指定します。</span><span class="sxs-lookup"><span data-stu-id="56f09-117">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="56f09-118">`reloc`Ia64 命令で64ビットアドレスのを生成 `movl` します。</span><span class="sxs-lookup"><span data-stu-id="56f09-118">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="56f09-119">`reloc`64 ビットアドレスのを生成します。</span><span class="sxs-lookup"><span data-stu-id="56f09-119">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="56f09-120">`reloc`Ia64 命令で25ビット PC 相対アドレスのを生成 `br.call` します。</span><span class="sxs-lookup"><span data-stu-id="56f09-120">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="56f09-121">`reloc`Ia64 命令で64ビット PC 相対アドレスのを生成 `brl.call` します。</span><span class="sxs-lookup"><span data-stu-id="56f09-121">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="56f09-122">`reloc`タグ付きポインター値に使用される、30ビットのセクション相対を生成します。</span><span class="sxs-lookup"><span data-stu-id="56f09-122">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="56f09-123">この列挙型への追加が内部名配列に反映されるようにするための sentinel 値 `reloc` 。</span><span class="sxs-lookup"><span data-stu-id="56f09-123">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="56f09-124">ベースを生成しないことを指定し `reloc` ます。</span><span class="sxs-lookup"><span data-stu-id="56f09-124">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="56f09-125">メモリの事前修正の内容が、セクションオフセットではなくポインターであることを示す値。</span><span class="sxs-lookup"><span data-stu-id="56f09-125">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56f09-126">要件</span><span class="sxs-lookup"><span data-stu-id="56f09-126">Requirements</span></span>  

 <span data-ttu-id="56f09-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56f09-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56f09-128">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="56f09-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56f09-129">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="56f09-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56f09-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56f09-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f09-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="56f09-131">See also</span></span>

- [<span data-ttu-id="56f09-132">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="56f09-132">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="56f09-133">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56f09-133">ICeeGen Interface</span></span>](iceegen-interface.md)
- [<span data-ttu-id="56f09-134">AddSectionReloc メソッド</span><span class="sxs-lookup"><span data-stu-id="56f09-134">AddSectionReloc Method</span></span>](iceegen-addsectionreloc-method.md)

---
description: 詳細については、「CorAssemblyFlags 列挙型」を参照してください。
title: CorAssemblyFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
ms.openlocfilehash: bd74534b1f607eea15f1d8615f66723428ddae3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678489"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="b3a14-103">CorAssemblyFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="b3a14-103">CorAssemblyFlags Enumeration</span></span>

<span data-ttu-id="b3a14-104">アセンブリ コンパイルに適用されるメタデータを記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="b3a14-104">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3a14-105">構文</span><span class="sxs-lookup"><span data-stu-id="b3a14-105">Syntax</span></span>  
  
```cpp  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b3a14-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b3a14-106">Members</span></span>  
  
|<span data-ttu-id="b3a14-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b3a14-107">Member</span></span>|<span data-ttu-id="b3a14-108">説明</span><span class="sxs-lookup"><span data-stu-id="b3a14-108">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="b3a14-109">アセンブリ参照が完全なハッシュされていない公開キーを保持していることを示します。</span><span class="sxs-lookup"><span data-stu-id="b3a14-109">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="b3a14-110">プロセッサアーキテクチャが指定されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="b3a14-110">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="b3a14-111">プロセッサアーキテクチャがニュートラル (PE32) であることを示します。</span><span class="sxs-lookup"><span data-stu-id="b3a14-111">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="b3a14-112">プロセッサアーキテクチャが x86 (PE32) であることを示します。</span><span class="sxs-lookup"><span data-stu-id="b3a14-112">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="b3a14-113">プロセッサアーキテクチャが Itanium (PE32 +) であることを示します。</span><span class="sxs-lookup"><span data-stu-id="b3a14-113">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="b3a14-114">プロセッサアーキテクチャが AMD X64 (PE32 +) であることを示します。</span><span class="sxs-lookup"><span data-stu-id="b3a14-114">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="b3a14-115">プロセッサアーキテクチャが ARM (PE32) であることを示します。</span><span class="sxs-lookup"><span data-stu-id="b3a14-115">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="b3a14-116">アセンブリが参照アセンブリであることを示します。つまり、アーキテクチャには適用されますが、どのアーキテクチャでも実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="b3a14-116">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="b3a14-117">したがって、フラグはと同じ `afPA_Mask` です。</span><span class="sxs-lookup"><span data-stu-id="b3a14-117">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="b3a14-118">プロセッサアーキテクチャフラグをレコードに反映する必要があることを示し `AssemblyRef` ます。</span><span class="sxs-lookup"><span data-stu-id="b3a14-118">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="b3a14-119">プロセッサアーキテクチャを記述するマスク。</span><span class="sxs-lookup"><span data-stu-id="b3a14-119">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="b3a14-120">プロセッサアーキテクチャの説明を含めることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b3a14-120">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="b3a14-121">プロセッサアーキテクチャフラグのインデックスとの間のシフト数を示します。</span><span class="sxs-lookup"><span data-stu-id="b3a14-121">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="b3a14-122">のからの対応する値を示し <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="b3a14-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="b3a14-123">のからの対応する値を示し <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="b3a14-123">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="b3a14-124">アセンブリを実行時に別のパブリッシャーからのアセンブリに再ターゲットできることを示します。</span><span class="sxs-lookup"><span data-stu-id="b3a14-124">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="b3a14-125">コンテンツの種類を説明するマスク。</span><span class="sxs-lookup"><span data-stu-id="b3a14-125">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="b3a14-126">既定のコンテンツタイプを示します。</span><span class="sxs-lookup"><span data-stu-id="b3a14-126">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="b3a14-127">Windows ランタイムコンテンツの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="b3a14-127">Indicates the Windows Runtime content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b3a14-128">要件</span><span class="sxs-lookup"><span data-stu-id="b3a14-128">Requirements</span></span>  

 <span data-ttu-id="b3a14-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3a14-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3a14-130">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b3a14-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b3a14-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3a14-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a14-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3a14-132">See also</span></span>

- [<span data-ttu-id="b3a14-133">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="b3a14-133">Metadata Enumerations</span></span>](metadata-enumerations.md)

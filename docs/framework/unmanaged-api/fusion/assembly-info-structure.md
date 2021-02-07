---
description: '詳細情報: ASSEMBLY_INFO 構造'
title: ASSEMBLY_INFO 構造体
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
ms.openlocfilehash: c28d9abf13769197b62705d51bbcf4f099616bbc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761286"
---
# <a name="assembly_info-structure"></a><span data-ttu-id="1d18b-103">ASSEMBLY_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="1d18b-103">ASSEMBLY_INFO Structure</span></span>

<span data-ttu-id="1d18b-104">グローバルアセンブリキャッシュに登録されているアセンブリに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="1d18b-104">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d18b-105">構文</span><span class="sxs-lookup"><span data-stu-id="1d18b-105">Syntax</span></span>  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="1d18b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1d18b-106">Members</span></span>  
  
|<span data-ttu-id="1d18b-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="1d18b-107">Member</span></span>|<span data-ttu-id="1d18b-108">説明</span><span class="sxs-lookup"><span data-stu-id="1d18b-108">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="1d18b-109">構造体のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="1d18b-109">The size, in bytes, of the structure.</span></span> <span data-ttu-id="1d18b-110">このフィールドは、将来の拡張のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="1d18b-110">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="1d18b-111">アセンブリに関するインストールの詳細を示すフラグ。</span><span class="sxs-lookup"><span data-stu-id="1d18b-111">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="1d18b-112">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d18b-112">The following values are supported:</span></span><br /><br /> <span data-ttu-id="1d18b-113">-アセンブリがインストールされていることを示す ASSEMBLYINFO_FLAG_INSTALLED 値。</span><span class="sxs-lookup"><span data-stu-id="1d18b-113">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="1d18b-114">.NET Framework の現在のバージョンは、常に `dwAssemblyFlags` この値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1d18b-114">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="1d18b-115">-アセンブリがペイロード常駐であることを示す ASSEMBLYINFO_FLAG_PAYLOADRESIDENT 値。</span><span class="sxs-lookup"><span data-stu-id="1d18b-115">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="1d18b-116">.NET Framework の現在のバージョンでは、この値には設定されません `dwAssemblyFlags` 。</span><span class="sxs-lookup"><span data-stu-id="1d18b-116">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="1d18b-117">アセンブリに格納されているファイルの合計サイズ (kb 単位)。</span><span class="sxs-lookup"><span data-stu-id="1d18b-117">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="1d18b-118">マニフェストファイルへの現在のパスを保持する文字列バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1d18b-118">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="1d18b-119">パスの末尾は null 文字である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d18b-119">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="1d18b-120">を格納している、null 終端文字を含むワイド文字の数 `pszCurrentAssemblyPathBuf` 。</span><span class="sxs-lookup"><span data-stu-id="1d18b-120">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1d18b-121">要件</span><span class="sxs-lookup"><span data-stu-id="1d18b-121">Requirements</span></span>  

 <span data-ttu-id="1d18b-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d18b-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d18b-123">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="1d18b-123">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1d18b-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d18b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d18b-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d18b-125">See also</span></span>

- [<span data-ttu-id="1d18b-126">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="1d18b-126">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="1d18b-127">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="1d18b-127">Global Assembly Cache</span></span>](../../app-domains/gac.md)

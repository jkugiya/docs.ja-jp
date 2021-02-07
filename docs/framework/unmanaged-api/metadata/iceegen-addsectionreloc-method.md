---
description: '詳細について: ICeeGen:: AddSectionReloc メソッド'
title: ICeeGen::AddSectionReloc メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
ms.openlocfilehash: 715c506f0bdcb3fcef33b3e9165d1f9ae47c6073
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707177"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="b52b6-103">ICeeGen::AddSectionReloc メソッド</span><span class="sxs-lookup"><span data-stu-id="b52b6-103">ICeeGen::AddSectionReloc Method</span></span>

<span data-ttu-id="b52b6-104">コードベースに reloc 命令を追加します。</span><span class="sxs-lookup"><span data-stu-id="b52b6-104">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="b52b6-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b52b6-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b52b6-106">構文</span><span class="sxs-lookup"><span data-stu-id="b52b6-106">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b52b6-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b52b6-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="b52b6-108">からReloc 命令を追加するメモリ内コードのセクション。</span><span class="sxs-lookup"><span data-stu-id="b52b6-108">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="b52b6-109">からセクションのオフセット。</span><span class="sxs-lookup"><span data-stu-id="b52b6-109">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="b52b6-110">からが参照するセクション `offset` 。</span><span class="sxs-lookup"><span data-stu-id="b52b6-110">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="b52b6-111">から [CeeSectionRelocType](ceesectionreloctype-enumeration.md) 値の1つ。追加する reloc 命令の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="b52b6-111">[in] One of the [CeeSectionRelocType](ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b52b6-112">要件</span><span class="sxs-lookup"><span data-stu-id="b52b6-112">Requirements</span></span>  

 <span data-ttu-id="b52b6-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b52b6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b52b6-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b52b6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b52b6-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b52b6-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b52b6-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b52b6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b52b6-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b52b6-117">See also</span></span>

- [<span data-ttu-id="b52b6-118">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b52b6-118">ICeeGen Interface</span></span>](iceegen-interface.md)

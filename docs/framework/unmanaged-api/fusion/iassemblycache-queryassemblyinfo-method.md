---
description: '詳細については、「IAssemblyCache:: QueryAssemblyInfo メソッド」を参照してください。'
title: IAssemblyCache::QueryAssemblyInfo メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCache.QueryAssemblyInfo
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type:
- apiref
ms.openlocfilehash: b3aa0064e24b22cf0af8b4e8d23a8b92d2f1ac34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760915"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="79fcf-103">IAssemblyCache::QueryAssemblyInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="79fcf-103">IAssemblyCache::QueryAssemblyInfo Method</span></span>

<span data-ttu-id="79fcf-104">指定したアセンブリに関する要求されたデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="79fcf-104">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79fcf-105">構文</span><span class="sxs-lookup"><span data-stu-id="79fcf-105">Syntax</span></span>  
  
```cpp  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79fcf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="79fcf-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="79fcf-107">からFusion に定義されているフラグ。</span><span class="sxs-lookup"><span data-stu-id="79fcf-107">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="79fcf-108">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="79fcf-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="79fcf-109">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="79fcf-109">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
- <span data-ttu-id="79fcf-110">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="79fcf-110">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="79fcf-111">からデータの取得対象となるアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="79fcf-111">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="79fcf-112">[入力、出力]アセンブリに関するデータを格納する [ASSEMBLY_INFO](assembly-info-structure.md) 構造体。</span><span class="sxs-lookup"><span data-stu-id="79fcf-112">[in, out] An [ASSEMBLY_INFO](assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79fcf-113">要件</span><span class="sxs-lookup"><span data-stu-id="79fcf-113">Requirements</span></span>  

 <span data-ttu-id="79fcf-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79fcf-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79fcf-115">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="79fcf-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="79fcf-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79fcf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79fcf-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="79fcf-117">See also</span></span>

- [<span data-ttu-id="79fcf-118">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79fcf-118">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)

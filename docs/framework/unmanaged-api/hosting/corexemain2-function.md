---
description: '詳細情報: _CorExeMain2 関数'
title: _CorExeMain2 関数
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
ms.openlocfilehash: 4629ea2f6c2ba13351c409bc382077eea926b507
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717096"
---
# <a name="_corexemain2-function"></a><span data-ttu-id="0d68c-103">_CorExeMain2 関数</span><span class="sxs-lookup"><span data-stu-id="0d68c-103">_CorExeMain2 Function</span></span>

<span data-ttu-id="0d68c-104">指定されたメモリ マップト コードのエントリ ポイントを実行します。</span><span class="sxs-lookup"><span data-stu-id="0d68c-104">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="0d68c-105">この関数は、オペレーティング システム ローダーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0d68c-105">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d68c-106">構文</span><span class="sxs-lookup"><span data-stu-id="0d68c-106">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d68c-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d68c-107">Parameters</span></span>  

 `pUnmappedPE`  
 <span data-ttu-id="0d68c-108">からメモリマップトコードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0d68c-108">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="0d68c-109">から保持できる要素の数 `pUnmappedPE` 。</span><span class="sxs-lookup"><span data-stu-id="0d68c-109">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="0d68c-110">から実行可能イメージの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0d68c-110">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="0d68c-111">からローダーファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="0d68c-111">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="0d68c-112">からコマンドラインパラメーター (存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="0d68c-112">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d68c-113">要件</span><span class="sxs-lookup"><span data-stu-id="0d68c-113">Requirements</span></span>  

 <span data-ttu-id="0d68c-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d68c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d68c-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0d68c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d68c-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0d68c-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d68c-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d68c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d68c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d68c-118">See also</span></span>

- [<span data-ttu-id="0d68c-119">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="0d68c-119">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)

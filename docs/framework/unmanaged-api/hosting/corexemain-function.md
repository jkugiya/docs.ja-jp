---
description: '詳細情報: _CorExeMain 関数'
title: _CorExeMain 関数
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
ms.openlocfilehash: f94197598d01255c35712aa682f83ca9be1fb377
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717135"
---
# <a name="_corexemain-function"></a><span data-ttu-id="6173b-103">_CorExeMain 関数</span><span class="sxs-lookup"><span data-stu-id="6173b-103">_CorExeMain Function</span></span>

<span data-ttu-id="6173b-104">共通言語ランタイム (CLR) を初期化し、実行可能アセンブリの CLR ヘッダーでマネージエントリポイントを検索して、実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="6173b-104">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6173b-105">構文</span><span class="sxs-lookup"><span data-stu-id="6173b-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6173b-106">解説</span><span class="sxs-lookup"><span data-stu-id="6173b-106">Remarks</span></span>  

 <span data-ttu-id="6173b-107">この関数は、マネージ実行可能アセンブリから作成されたプロセスでローダーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6173b-107">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="6173b-108">DLL アセンブリの場合、ローダーは代わりに [_CorDllMain](cordllmain-function.md) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6173b-108">For DLL assemblies, the loader calls the [_CorDllMain](cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="6173b-109">オペレーティングシステムローダーは、イメージファイルで指定されたエントリポイントに関係なく、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6173b-109">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="6173b-110">Windows 98、Windows ME、Windows NT、および Windows 2000 では、 `_CorExeMain` 関数はオペレーティングシステムローダーの修正によって間接的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6173b-110">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="6173b-111">それ以外のすべてのバージョンの Windows では、オペレーティングシステムローダーによって直接呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6173b-111">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="6173b-112">詳細については、「 [_CorValidateImage](corvalidateimage-function.md) 」トピックの「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6173b-112">For additional information, see the Remarks section in the [_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6173b-113">要件</span><span class="sxs-lookup"><span data-stu-id="6173b-113">Requirements</span></span>  

 <span data-ttu-id="6173b-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6173b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6173b-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="6173b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6173b-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6173b-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6173b-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6173b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6173b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6173b-118">See also</span></span>

- [<span data-ttu-id="6173b-119">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="6173b-119">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)

---
description: '詳細情報: _CorDllMain 関数'
title: _CorDllMain 関数
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
ms.openlocfilehash: 442afae3a627eb684a86c02fbc6e546aa804b7a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717149"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="336db-103">\_CorDllMain 関数</span><span class="sxs-lookup"><span data-stu-id="336db-103">\_CorDllMain Function</span></span>

<span data-ttu-id="336db-104">共通言語ランタイム (CLR) を初期化し、DLL アセンブリの CLR ヘッダー内のマネージエントリポイントを検索して、実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="336db-104">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="336db-105">構文</span><span class="sxs-lookup"><span data-stu-id="336db-105">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="336db-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="336db-106">Parameters</span></span>  

 `hInst`  
 <span data-ttu-id="336db-107">から読み込まれたモジュールのインスタンスハンドル。</span><span class="sxs-lookup"><span data-stu-id="336db-107">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="336db-108">からDLL のエントリポイント関数が呼び出される理由を示します。</span><span class="sxs-lookup"><span data-stu-id="336db-108">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="336db-109">このパラメーターには、DLL \_ PROCESS_ATTACH、dll \_ スレッド \_ のアタッチ、dll \_ スレッドの \_ アタッチ、または dll プロセスの \_ \_ デタッチのいずれかの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="336db-109">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="336db-110">これらの値の詳細については、Platform SDK のドキュメントを参照してください `DllMain` 。</span><span class="sxs-lookup"><span data-stu-id="336db-110">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="336db-111">から未使用.</span><span class="sxs-lookup"><span data-stu-id="336db-111">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="336db-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="336db-112">Return Value</span></span>  

 <span data-ttu-id="336db-113">このメソッドは `true` 、成功し `false` た場合はを返し、エラーが発生した場合はを返します。</span><span class="sxs-lookup"><span data-stu-id="336db-113">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="336db-114">解説</span><span class="sxs-lookup"><span data-stu-id="336db-114">Remarks</span></span>  

 <span data-ttu-id="336db-115">この関数は、DLL アセンブリのオペレーティングシステムローダーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="336db-115">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="336db-116">実行可能アセンブリの場合、ローダーは代わりに[ \_ CorExeMain](corexemain-function.md)関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="336db-116">For executable assemblies, the loader calls the [\_CorExeMain](corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="336db-117">オペレーティングシステムローダーは、DLL ファイルで指定されたエントリポイントに関係なく、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="336db-117">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="336db-118">`_CorDllMain`関数は、オペレーティングシステムローダーによって直接呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="336db-118">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="336db-119">詳細については、 [ \_ corvalidateimage](corvalidateimage-function.md)トピックの「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="336db-119">For additional information, see the Remarks section in the [\_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="336db-120">要件</span><span class="sxs-lookup"><span data-stu-id="336db-120">Requirements</span></span>  

 <span data-ttu-id="336db-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="336db-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="336db-122">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="336db-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="336db-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="336db-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="336db-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="336db-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="336db-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="336db-125">See also</span></span>

- [<span data-ttu-id="336db-126">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="336db-126">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)

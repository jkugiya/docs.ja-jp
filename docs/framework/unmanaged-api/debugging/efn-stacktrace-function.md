---
description: '詳細情報: _EFN_StackTrace 関数'
title: _EFN_StackTrace 関数
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
ms.openlocfilehash: 6092d0793967cc422e30342783ab4dfd70b33de9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738287"
---
# <a name="_efn_stacktrace-function"></a><span data-ttu-id="43a5e-103">\_EFN \_ StackTrace 関数</span><span class="sxs-lookup"><span data-stu-id="43a5e-103">\_EFN\_StackTrace Function</span></span>

<span data-ttu-id="43a5e-104">マネージド スタック トレースのテキスト表現および `CONTEXT` レコードの配列 (アンマネージド コードとマネージド コードの間の各移行につき 1 つ) を提供します。</span><span class="sxs-lookup"><span data-stu-id="43a5e-104">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43a5e-105">構文</span><span class="sxs-lookup"><span data-stu-id="43a5e-105">Syntax</span></span>  
  
```cpp  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43a5e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="43a5e-106">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="43a5e-107">からデバッグ中のクライアント。</span><span class="sxs-lookup"><span data-stu-id="43a5e-107">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="43a5e-108">入出力スタックトレースのテキスト表現。</span><span class="sxs-lookup"><span data-stu-id="43a5e-108">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="43a5e-109">入出力内の文字数へのポインター `wszTextOut` 。</span><span class="sxs-lookup"><span data-stu-id="43a5e-109">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="43a5e-110">入出力遷移コンテキストの配列。</span><span class="sxs-lookup"><span data-stu-id="43a5e-110">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="43a5e-111">入出力配列内の遷移コンテキストの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="43a5e-111">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="43a5e-112">からコンテキスト構造のサイズ。</span><span class="sxs-lookup"><span data-stu-id="43a5e-112">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="43a5e-113">からを0または SOS_STACKTRACE_SHOWADDRESSES (0x01) のいずれかに設定すると、EBP レジスタと、各行の前に入力スタックポインター (ESP) が表示され `module!functionname` ます。</span><span class="sxs-lookup"><span data-stu-id="43a5e-113">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43a5e-114">解説</span><span class="sxs-lookup"><span data-stu-id="43a5e-114">Remarks</span></span>  

 <span data-ttu-id="43a5e-115">この `_EFN_StackTrace` 構造体は、WinDbg プログラムインターフェイスから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="43a5e-115">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="43a5e-116">パラメーターは次のように使用されます。</span><span class="sxs-lookup"><span data-stu-id="43a5e-116">Parameters are used as follows:</span></span>  
  
- <span data-ttu-id="43a5e-117">`wszTextOut`が null で、 `puiTextLength` が null でない場合、関数はの文字列長を返し `puiTextLength` ます。</span><span class="sxs-lookup"><span data-stu-id="43a5e-117">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
- <span data-ttu-id="43a5e-118">`wszTextOut`が null でない場合、関数はに `wszTextOut` よって示される場所までテキストを格納し `puiTextLength` ます。</span><span class="sxs-lookup"><span data-stu-id="43a5e-118">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="43a5e-119">バッファーに十分な空き領域がある場合は、正常に返されます。バッファーの長さが十分でない場合は E_OUTOFMEMORY を返します。</span><span class="sxs-lookup"><span data-stu-id="43a5e-119">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
- <span data-ttu-id="43a5e-120">とが両方とも null の場合、関数の移行部分は無視され `pTransitionContexts` `puiTransitionContextCount` ます。</span><span class="sxs-lookup"><span data-stu-id="43a5e-120">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="43a5e-121">この場合、関数は呼び出し元に関数名のみのテキスト出力を提供します。</span><span class="sxs-lookup"><span data-stu-id="43a5e-121">In this case, the function provides callers with text output of only the function names.</span></span>  
  
- <span data-ttu-id="43a5e-122">`pTransitionContexts`が null で、 `puiTransitionContextCount` が null でない場合、関数はで必要なコンテキストエントリの数を返し `puiTransitionContextCount` ます。</span><span class="sxs-lookup"><span data-stu-id="43a5e-122">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
- <span data-ttu-id="43a5e-123">`pTransitionContexts`が null でない場合、関数はそれを長さの構造体の配列として扱い `puiTransitionContextCount` ます。</span><span class="sxs-lookup"><span data-stu-id="43a5e-123">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="43a5e-124">構造体のサイズはによって指定され、 `uiSizeOfContext` [simplecontext](stacktrace-simplecontext-structure.md) またはアーキテクチャのサイズである必要があり `CONTEXT` ます。</span><span class="sxs-lookup"><span data-stu-id="43a5e-124">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
- <span data-ttu-id="43a5e-125">`wszTextOut` は、次の形式で記述されます。</span><span class="sxs-lookup"><span data-stu-id="43a5e-125">`wszTextOut` is written in the following format:</span></span>  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- <span data-ttu-id="43a5e-126">16進数のオフセットが0x0 の場合、オフセットは書き込まれません。</span><span class="sxs-lookup"><span data-stu-id="43a5e-126">If the offset in hex is 0x0, no offset is written.</span></span>  
  
- <span data-ttu-id="43a5e-127">現在コンテキスト内にあるスレッドにマネージコードがない場合、関数は SOS_E_NOMANAGEDCODE を返します。</span><span class="sxs-lookup"><span data-stu-id="43a5e-127">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
- <span data-ttu-id="43a5e-128">パラメーターは、 `Flags` 各行の前に EBP と ESP を表示する場合は0または SOS_STACKTRACE_SHOWADDRESSES になり `module!functionname` ます。</span><span class="sxs-lookup"><span data-stu-id="43a5e-128">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="43a5e-129">既定値は0です。</span><span class="sxs-lookup"><span data-stu-id="43a5e-129">By default, it is 0.</span></span>  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="43a5e-130">要件</span><span class="sxs-lookup"><span data-stu-id="43a5e-130">Requirements</span></span>  

 <span data-ttu-id="43a5e-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43a5e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43a5e-132">**ヘッダー:** SOS_Stacktrace</span><span class="sxs-lookup"><span data-stu-id="43a5e-132">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="43a5e-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43a5e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43a5e-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="43a5e-134">See also</span></span>

- [<span data-ttu-id="43a5e-135">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="43a5e-135">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

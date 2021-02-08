---
description: '詳細について: ICLRDataTarget:: GetThreadContext メソッド'
title: ICLRDataTarget::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
ms.openlocfilehash: 210f4294aed31307557db419a0fb567cc71d4354
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785691"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="677b7-103">ICLRDataTarget::GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="677b7-103">ICLRDataTarget::GetThreadContext Method</span></span>

<span data-ttu-id="677b7-104">ターゲットプロセス内の指定されたスレッドの現在の実行コンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="677b7-104">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="677b7-105">このメソッドは、共通言語ランタイムのデータアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="677b7-105">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="677b7-106">構文</span><span class="sxs-lookup"><span data-stu-id="677b7-106">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="677b7-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="677b7-107">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="677b7-108">からターゲットプロセス内のスレッドのオペレーティングシステム識別子。</span><span class="sxs-lookup"><span data-stu-id="677b7-108">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="677b7-109">からコンテキストのどの部分を返すかを指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="677b7-109">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="677b7-110">実装は、少なくともこれらのコンテキストの部分を返します。</span><span class="sxs-lookup"><span data-stu-id="677b7-110">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="677b7-111">からコンテキストのサイズ。</span><span class="sxs-lookup"><span data-stu-id="677b7-111">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="677b7-112">入出力コンテキストを配置するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="677b7-112">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="677b7-113">バッファー内のデータは、 `context` Win32 構造体の形式である必要があり `CONTEXT` ます。</span><span class="sxs-lookup"><span data-stu-id="677b7-113">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="677b7-114">コンテキストはプロセッサ固有のレジスタデータを指定するため、Win32 構造体の定義は `CONTEXT` プロセッサのアーキテクチャによって異なります。</span><span class="sxs-lookup"><span data-stu-id="677b7-114">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="677b7-115">Win32 構造体の定義については、Winnt.h ヘッダーファイルを参照してください `CONTEXT` 。</span><span class="sxs-lookup"><span data-stu-id="677b7-115">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="677b7-116">解説</span><span class="sxs-lookup"><span data-stu-id="677b7-116">Remarks</span></span>  

 <span data-ttu-id="677b7-117">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="677b7-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="677b7-118">要件</span><span class="sxs-lookup"><span data-stu-id="677b7-118">Requirements</span></span>  

 <span data-ttu-id="677b7-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="677b7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="677b7-120">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="677b7-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="677b7-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="677b7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="677b7-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="677b7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="677b7-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="677b7-123">See also</span></span>

- [<span data-ttu-id="677b7-124">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="677b7-124">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)

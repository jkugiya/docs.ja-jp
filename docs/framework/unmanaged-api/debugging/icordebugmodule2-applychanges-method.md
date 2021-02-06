---
description: '詳細情報: ICorDebugModule2:: ApplyChanges メソッド'
title: ICorDebugModule2::ApplyChanges メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
ms.openlocfilehash: 09cbc395c8d656d1dc27de86305432b26308c885
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660077"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="82b7a-103">ICorDebugModule2::ApplyChanges メソッド</span><span class="sxs-lookup"><span data-stu-id="82b7a-103">ICorDebugModule2::ApplyChanges Method</span></span>

<span data-ttu-id="82b7a-104">メタデータの変更と、Microsoft 中間言語 (MSIL) コードの変更を実行中のプロセスに適用します。</span><span class="sxs-lookup"><span data-stu-id="82b7a-104">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82b7a-105">構文</span><span class="sxs-lookup"><span data-stu-id="82b7a-105">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82b7a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82b7a-106">Parameters</span></span>  

 `cbMetadata`  
 <span data-ttu-id="82b7a-107">からデルタメタデータのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="82b7a-107">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="82b7a-108">からデルタメタデータを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="82b7a-108">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="82b7a-109">バッファーのアドレスは、 [IMetaDataEmit2:: SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) メソッドから返されます。</span><span class="sxs-lookup"><span data-stu-id="82b7a-109">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="82b7a-110">メタデータ内の相対仮想アドレス (RVAs) は、MSIL コードの先頭に対して相対的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="82b7a-110">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="82b7a-111">からデルタ MSIL コードのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="82b7a-111">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="82b7a-112">から更新された MSIL コードを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="82b7a-112">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82b7a-113">解説</span><span class="sxs-lookup"><span data-stu-id="82b7a-113">Remarks</span></span>  

 <span data-ttu-id="82b7a-114">パラメーターは、 `pbMetadata` ( [IMetaDataEmit2:: SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)によって出力される) 特別なデルタメタデータ形式です。</span><span class="sxs-lookup"><span data-stu-id="82b7a-114">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="82b7a-115">`pbMetadata` 以前のメタデータをベースとして受け取り、そのベースに適用する個々の変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="82b7a-115">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="82b7a-116">これに対し、のパラメーターには、 `pbIL[` 更新されたメソッドの新しい msil が含まれています。これは、そのメソッドの前の msil を完全に置き換えることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="82b7a-116">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="82b7a-117">デルタ MSIL とメタデータがデバッガーのメモリ内に作成されると、デバッガーはを呼び出して、 `ApplyChanges` 変更を共通言語ランタイム (CLR) に送信します。</span><span class="sxs-lookup"><span data-stu-id="82b7a-117">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="82b7a-118">ランタイムはそのメタデータテーブルを更新し、新しい MSIL をプロセスに配置して、新しい MSIL の just-in-time (JIT) コンパイルを設定します。</span><span class="sxs-lookup"><span data-stu-id="82b7a-118">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="82b7a-119">変更が適用されると、デバッガーは [IMetaDataEmit2:: ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) を呼び出して、次の編集セッションの準備を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="82b7a-119">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="82b7a-120">デバッガーはプロセスを続行できます。</span><span class="sxs-lookup"><span data-stu-id="82b7a-120">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="82b7a-121">デバッガーは、 `ApplyChanges` デルタメタデータを持つモジュールでを呼び出すたびに、変更を出力するために使用されるコピーを除き、そのモジュールのメタデータのすべてのコピーで同じデルタメタデータを使用して [IMetaDataEmit:: ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="82b7a-121">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="82b7a-122">メタデータのコピーが実際のメタデータと同期しなくなる場合、デバッガーは常にそのコピーを破棄して新しいコピーを取得できます。</span><span class="sxs-lookup"><span data-stu-id="82b7a-122">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="82b7a-123">メソッドが失敗した場合 `ApplyChanges` 、デバッグセッションは無効な状態にあり、再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="82b7a-123">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82b7a-124">要件</span><span class="sxs-lookup"><span data-stu-id="82b7a-124">Requirements</span></span>  

 <span data-ttu-id="82b7a-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82b7a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82b7a-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82b7a-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82b7a-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82b7a-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82b7a-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82b7a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

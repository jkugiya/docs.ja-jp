---
description: '詳細について: ICorDebugProcess2:: SetDesiredNGENCompilerFlags メソッド'
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
ms.openlocfilehash: 3a4749ad26e88d1a602876f28a52754323093fce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650087"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="8601a-103">ICorDebugProcess2::SetDesiredNGENCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="8601a-103">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>

<span data-ttu-id="8601a-104">ランタイムがそのイメージを現在のプロセスに読み込むために、プリコンパイル済みイメージに埋め込む必要があるフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="8601a-104">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8601a-105">構文</span><span class="sxs-lookup"><span data-stu-id="8601a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8601a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8601a-106">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="8601a-107">から適切なプリコンパイル済みイメージを選択するために使用されるコンパイラフラグを指定する [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="8601a-107">[in] A value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8601a-108">解説</span><span class="sxs-lookup"><span data-stu-id="8601a-108">Remarks</span></span>  

 <span data-ttu-id="8601a-109">メソッドは、 `SetDesiredNGENCompilerFlags` プリコンパイル済みイメージに埋め込まれる必要があるフラグを指定します。これにより、ランタイムはそのイメージをこのプロセスに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="8601a-109">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="8601a-110">このメソッドによって設定されるフラグは、正しいプリコンパイル済みイメージを選択するためにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="8601a-110">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="8601a-111">そのようなイメージが存在しない場合、ランタイムは Microsoft 中間言語 (MSIL) イメージと just-in-time (JIT) コンパイラを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="8601a-111">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="8601a-112">その場合でも、デバッガーは [ICorDebugModule2:: SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) メソッドを使用して、JIT コンパイルに必要なフラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8601a-112">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="8601a-113">イメージが読み込まれるときに、そのイメージに対して一部の JIT コンパイルを実行する必要がある場合 (イメージにジェネリックが含まれている場合)、メソッドによって指定されたコンパイラフラグ `SetDesiredNGENCompilerFlags` が追加の jit コンパイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8601a-113">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="8601a-114">このメソッドは、の `SetDesiredNGENCompilerFlags` メソッドを[](icordebugmanagedcallback-createprocess-method.md)呼び出さなければなりません。</span><span class="sxs-lookup"><span data-stu-id="8601a-114">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="8601a-115">その後、メソッドを呼び出そうとすると `SetDesiredNGENCompilerFlags` 失敗します。</span><span class="sxs-lookup"><span data-stu-id="8601a-115">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="8601a-116">また、列挙型で定義されていないフラグや、指定されたプロセスに対して有効ではないフラグを設定しようとすると `CorDebugJITCompilerFlags` 失敗します。</span><span class="sxs-lookup"><span data-stu-id="8601a-116">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8601a-117">要件</span><span class="sxs-lookup"><span data-stu-id="8601a-117">Requirements</span></span>  

 <span data-ttu-id="8601a-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8601a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8601a-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8601a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8601a-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8601a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8601a-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8601a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8601a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="8601a-122">See also</span></span>

- [<span data-ttu-id="8601a-123">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8601a-123">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="8601a-124">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8601a-124">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

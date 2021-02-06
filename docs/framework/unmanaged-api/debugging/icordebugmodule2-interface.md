---
description: 詳細については、「ICorDebugModule2 インターフェイス」を参照してください。
title: ICorDebugModule2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
ms.openlocfilehash: 28de1f0d3411218ac92991d4fceda0612c8199bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659934"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="59483-103">ICorDebugModule2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="59483-103">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="59483-104">モジュールインターフェイスの論理拡張機能として機能します。</span><span class="sxs-lookup"><span data-stu-id="59483-104">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59483-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="59483-105">Methods</span></span>  
  
|<span data-ttu-id="59483-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="59483-106">Method</span></span>|<span data-ttu-id="59483-107">説明</span><span class="sxs-lookup"><span data-stu-id="59483-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59483-108">ApplyChanges メソッド</span><span class="sxs-lookup"><span data-stu-id="59483-108">ApplyChanges Method</span></span>](icordebugmodule2-applychanges-method.md)|<span data-ttu-id="59483-109">メタデータの変更と、Microsoft 中間言語 (MSIL) コードの変更を実行中のプロセスに適用します。</span><span class="sxs-lookup"><span data-stu-id="59483-109">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="59483-110">GetJITCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="59483-110">GetJITCompilerFlags Method</span></span>](icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="59483-111">このの just-in-time (JIT) コンパイルを制御するフラグを取得し `ICorDebugModule2` ます。</span><span class="sxs-lookup"><span data-stu-id="59483-111">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="59483-112">ResolveAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="59483-112">ResolveAssembly Method</span></span>](icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="59483-113">指定したメタデータトークンによって参照されるアセンブリを解決します。</span><span class="sxs-lookup"><span data-stu-id="59483-113">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="59483-114">SetJITCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="59483-114">SetJITCompilerFlags Method</span></span>](icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="59483-115">このの JIT コンパイルを制御するフラグを設定 `ICorDebugModule2` します。</span><span class="sxs-lookup"><span data-stu-id="59483-115">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="59483-116">SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="59483-116">SetJMCStatus Method</span></span>](icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="59483-117">こののすべてのクラスのすべてのメソッドのマイコードのみ (JMC) の状態を、 `ICorDebugModule2` 指定した値に設定し `pTokens` ます。ただし、逆の値に設定されている配列内のすべてのメソッドを除きます。</span><span class="sxs-lookup"><span data-stu-id="59483-117">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59483-118">解説</span><span class="sxs-lookup"><span data-stu-id="59483-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59483-119">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="59483-119">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59483-120">要件</span><span class="sxs-lookup"><span data-stu-id="59483-120">Requirements</span></span>  

 <span data-ttu-id="59483-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59483-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59483-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59483-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59483-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59483-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59483-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59483-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59483-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="59483-125">See also</span></span>

- [<span data-ttu-id="59483-126">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="59483-126">Debugging Interfaces</span></span>](debugging-interfaces.md)

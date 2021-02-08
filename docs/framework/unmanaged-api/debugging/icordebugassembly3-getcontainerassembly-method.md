---
description: '詳細について: ICorDebugAssembly3:: GetContainerAssembly メソッド'
title: ICorDebugAssembly3::GetContainerAssembly メソッド
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 5a6bc6dfb1c8403137a9444ff1cc4f64e75da65d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791518"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="0d412-103">ICorDebugAssembly3::GetContainerAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="0d412-103">ICorDebugAssembly3::GetContainerAssembly Method</span></span>

<span data-ttu-id="0d412-104">この `ICorDebugAssembly3` オブジェクトのコンテナー アセンブリを返します。</span><span class="sxs-lookup"><span data-stu-id="0d412-104">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d412-105">構文</span><span class="sxs-lookup"><span data-stu-id="0d412-105">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d412-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d412-106">Parameters</span></span>  

 `ppAssembly`  
 <span data-ttu-id="0d412-107">コンテナーアセンブリを表す、オブジェクトのアドレスへのポインター。メソッドの呼び出しが失敗した場合は **null** 。</span><span class="sxs-lookup"><span data-stu-id="0d412-107">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d412-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0d412-108">Return Value</span></span>  

 <span data-ttu-id="0d412-109">`S_OK` メソッドの呼び出しが成功した場合は。それ以外の場合、 `S_FALSE` 、、および `ppAssembly` は **null** になります。</span><span class="sxs-lookup"><span data-stu-id="0d412-109">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d412-110">解説</span><span class="sxs-lookup"><span data-stu-id="0d412-110">Remarks</span></span>  

 <span data-ttu-id="0d412-111">このアセンブリが 1 つのコンテナー アセンブリ内の他のアセンブリとマージされている場合、このメソッドはコンテナー アセンブリを返します。</span><span class="sxs-lookup"><span data-stu-id="0d412-111">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="0d412-112">詳細と用語については、「 [ICorDebugProcess6:: EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d412-112">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d412-113">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d412-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d412-114">要件</span><span class="sxs-lookup"><span data-stu-id="0d412-114">Requirements</span></span>  

 <span data-ttu-id="0d412-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d412-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d412-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d412-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d412-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d412-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d412-118">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d412-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d412-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d412-119">See also</span></span>

- [<span data-ttu-id="0d412-120">ICorDebugAssembly3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d412-120">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="0d412-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d412-121">Debugging Interfaces</span></span>](debugging-interfaces.md)

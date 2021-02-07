---
description: '詳細について: ICorDebugAssembly3:: EnumerateContainedAssemblies メソッド'
title: ICorDebugAssembly3::EnumerateContainedAssemblies メソッド
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 8933500713661ef785eb3ce5abc574e512580b6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754083"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="d582d-103">ICorDebugAssembly3::EnumerateContainedAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="d582d-103">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>

<span data-ttu-id="d582d-104">このアセンブリに含まれているアセンブリの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="d582d-104">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d582d-105">構文</span><span class="sxs-lookup"><span data-stu-id="d582d-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d582d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d582d-106">Parameters</span></span>  

 `ppAssemblies`  
 <span data-ttu-id="d582d-107">[出力] 列挙子である ICorDebugAssemblyEnum インターフェイス オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d582d-107">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d582d-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="d582d-108">Return Value</span></span>  

 <span data-ttu-id="d582d-109">この `S_OK` オブジェクトがコンテナーの場合は、`ICorDebugAssembly3`。それ以外の場合は、`S_FALSE` で、列挙子は空です。</span><span class="sxs-lookup"><span data-stu-id="d582d-109">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d582d-110">解説</span><span class="sxs-lookup"><span data-stu-id="d582d-110">Remarks</span></span>  

 <span data-ttu-id="d582d-111">含まれているアセンブリを列挙するためにシンボルが必要です。</span><span class="sxs-lookup"><span data-stu-id="d582d-111">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="d582d-112">シンボルがない場合、メソッドは `S_FALSE` を返し、有効な列挙子は提供されません。</span><span class="sxs-lookup"><span data-stu-id="d582d-112">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d582d-113">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d582d-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d582d-114">要件</span><span class="sxs-lookup"><span data-stu-id="d582d-114">Requirements</span></span>  

 <span data-ttu-id="d582d-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d582d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d582d-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d582d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d582d-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d582d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d582d-118">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d582d-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d582d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d582d-119">See also</span></span>

- [<span data-ttu-id="d582d-120">ICorDebugAssembly3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d582d-120">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="d582d-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d582d-121">Debugging Interfaces</span></span>](debugging-interfaces.md)

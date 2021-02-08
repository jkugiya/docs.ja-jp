---
description: 詳細については、「ICorDebugAssembly3 インターフェイス」を参照してください。
title: ICorDebugAssembly3 インターフェイス
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 3a8cabf41dffa75d82c2b6fde53dff2ede4838e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791505"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="2d6ae-103">ICorDebugAssembly3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2d6ae-103">ICorDebugAssembly3 Interface</span></span>

<span data-ttu-id="2d6ae-104">コンテナーのアセンブリとそれらに含まれるアセンブリのサポートを提供するために、ICorDebugAssembly インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="2d6ae-104">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d6ae-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2d6ae-105">Methods</span></span>  
  
|<span data-ttu-id="2d6ae-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="2d6ae-106">Method</span></span>|<span data-ttu-id="2d6ae-107">説明</span><span class="sxs-lookup"><span data-stu-id="2d6ae-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d6ae-108">EnumerateContainedAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="2d6ae-108">EnumerateContainedAssemblies Method</span></span>](icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="2d6ae-109">このアセンブリに含まれているアセンブリの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="2d6ae-109">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="2d6ae-110">GetContainerAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="2d6ae-110">GetContainerAssembly Method</span></span>](icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="2d6ae-111">この `ICorDebugAssembly3` オブジェクトのコンテナー アセンブリを返します。</span><span class="sxs-lookup"><span data-stu-id="2d6ae-111">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d6ae-112">解説</span><span class="sxs-lookup"><span data-stu-id="2d6ae-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d6ae-113">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="2d6ae-113">The interface is available with .NET Native only.</span></span> <span data-ttu-id="2d6ae-114">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="2d6ae-114">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d6ae-115">要件</span><span class="sxs-lookup"><span data-stu-id="2d6ae-115">Requirements</span></span>  

 <span data-ttu-id="2d6ae-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d6ae-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d6ae-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d6ae-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d6ae-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d6ae-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d6ae-119">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d6ae-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d6ae-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d6ae-120">See also</span></span>

- [<span data-ttu-id="2d6ae-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2d6ae-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2d6ae-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="2d6ae-122">Debugging</span></span>](index.md)

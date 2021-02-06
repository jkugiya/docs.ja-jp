---
description: '詳細については、次を参照してください: いいね Provider インターフェイス'
title: ICorDebugSymbolProvider インターフェイス
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: bd47f294092ee87fc1f34bc68fe744b447e21f20
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659583"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="c75de-103">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c75de-103">ICorDebugSymbolProvider Interface</span></span>

<span data-ttu-id="c75de-104">デバッグ シンボル情報を取得するために使用できるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c75de-104">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c75de-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c75de-105">Methods</span></span>  
  
|<span data-ttu-id="c75de-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="c75de-106">Method</span></span>|<span data-ttu-id="c75de-107">説明</span><span class="sxs-lookup"><span data-stu-id="c75de-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c75de-108">GetAssemblyImageBytes メソッド</span><span class="sxs-lookup"><span data-stu-id="c75de-108">GetAssemblyImageBytes Method</span></span>](icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="c75de-109">マージされたアセンブリ内の指定の相対仮想アドレス (RVA: relative virtual address) で、マージされたアセンブリのデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="c75de-109">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="c75de-110">GetAssemblyImageMetadata メソッド</span><span class="sxs-lookup"><span data-stu-id="c75de-110">GetAssemblyImageMetadata Method</span></span>](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="c75de-111">マージされたアセンブリのメタデータを返します。</span><span class="sxs-lookup"><span data-stu-id="c75de-111">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="c75de-112">GetCodeRange メソッド</span><span class="sxs-lookup"><span data-stu-id="c75de-112">GetCodeRange Method</span></span>](icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="c75de-113">メソッド内の指定の相対仮想アドレス (RVA: relative virtual address) で、メソッド開始アドレスとサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="c75de-113">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="c75de-114">GetInstanceFieldSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="c75de-114">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="c75de-115">typespec シグネチャに対応するインスタンス フィールド シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="c75de-115">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="c75de-116">GetMergedAssemblyRecords メソッド</span><span class="sxs-lookup"><span data-stu-id="c75de-116">GetMergedAssemblyRecords Method</span></span>](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="c75de-117">すべてのマージされたアセンブリのシンボル レコードを取得します。</span><span class="sxs-lookup"><span data-stu-id="c75de-117">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="c75de-118">GetMethodLocalSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="c75de-118">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="c75de-119">メソッドの指定の相対仮想アドレス (RVA) で、そのメソッドのローカル シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="c75de-119">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="c75de-120">GetMethodParameterSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="c75de-120">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="c75de-121">メソッドの指定の相対仮想アドレス (RVA: relative virtual address ) で、そのメソッドのパラメーター シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="c75de-121">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="c75de-122">GetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="c75de-122">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="c75de-123">メソッドの指定の相対仮想アドレス (RVA) で、そのメソッドのプロパティに関する情報 (メソッドのメタデータ トークンなど) と、そのジェネリック パラメーターに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="c75de-123">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="c75de-124">GetObjectSize メソッド</span><span class="sxs-lookup"><span data-stu-id="c75de-124">GetObjectSize Method</span></span>](icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="c75de-125">typespec シグネチャに基づいてオブジェクトのオブジェクト サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="c75de-125">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="c75de-126">GetStaticFieldSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="c75de-126">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="c75de-127">typespec シグネチャに対応する静的フィールド シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="c75de-127">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="c75de-128">GetTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="c75de-128">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="c75de-129">Vtable の指定の相対仮想アドレス (RVA) における、ジェネリック パラメーターのシグネチャの数などの型のプロパティに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="c75de-129">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c75de-130">解説</span><span class="sxs-lookup"><span data-stu-id="c75de-130">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c75de-131">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="c75de-131">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c75de-132">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="c75de-132">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c75de-133">要件</span><span class="sxs-lookup"><span data-stu-id="c75de-133">Requirements</span></span>  

 <span data-ttu-id="c75de-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c75de-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c75de-135">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c75de-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c75de-136">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c75de-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c75de-137">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c75de-137">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75de-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="c75de-138">See also</span></span>

- [<span data-ttu-id="c75de-139">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c75de-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c75de-140">デバッグ</span><span class="sxs-lookup"><span data-stu-id="c75de-140">Debugging</span></span>](index.md)

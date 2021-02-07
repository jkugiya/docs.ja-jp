---
description: 詳細については、「ICorDebugProcess6 インターフェイス」を参照してください。
title: ICorDebugProcess6 インターフェイス
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: f303670d0667a80507bc623f9af037759fdde463
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691459"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="bcdfb-103">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bcdfb-103">ICorDebugProcess6 Interface</span></span>

<span data-ttu-id="bcdfb-104">ICorDebugProcess インターフェイスを論理的に拡張し、ネイティブ例外デバッグ イベントにエンコードされたマネージド デバッグ イベントのデコードや仮想モジュール分割などの機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="bcdfb-104">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bcdfb-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="bcdfb-105">Methods</span></span>  
  
|<span data-ttu-id="bcdfb-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="bcdfb-106">Method</span></span>|<span data-ttu-id="bcdfb-107">説明</span><span class="sxs-lookup"><span data-stu-id="bcdfb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bcdfb-108">DecodeEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="bcdfb-108">DecodeEvent Method</span></span>](icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="bcdfb-109">特別に作成されたネイティブ例外デバッグ イベントのペイロードにカプセル化されたマネージド デバッグ イベントをデコードします。</span><span class="sxs-lookup"><span data-stu-id="bcdfb-109">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="bcdfb-110">EnableVirtualModuleSplitting メソッド</span><span class="sxs-lookup"><span data-stu-id="bcdfb-110">EnableVirtualModuleSplitting Method</span></span>](icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="bcdfb-111">仮想モジュール分割を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="bcdfb-111">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="bcdfb-112">GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="bcdfb-112">GetCode Method</span></span>](icordebugprocess6-getcode-method.md)|<span data-ttu-id="bcdfb-113">特定のコード アドレスで、マネージド コードに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="bcdfb-113">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="bcdfb-114">GetExportStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="bcdfb-114">GetExportStepInfo Method</span></span>](icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="bcdfb-115">マネージド コードのステップ実行に役立つランタイム エクスポート関数の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="bcdfb-115">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="bcdfb-116">MarkDebuggerAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="bcdfb-116">MarkDebuggerAttached Method</span></span>](icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="bcdfb-117">.NET Framework クラス ライブラリの <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> メソッドが `true` を返すように、デバッグ対象の内部状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="bcdfb-117">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="bcdfb-118">ProcessStateChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="bcdfb-118">ProcessStateChanged Method</span></span>](icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="bcdfb-119">プロセスが実行されていることを [ICorDebug](icordebug-interface.md) に通知します。</span><span class="sxs-lookup"><span data-stu-id="bcdfb-119">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcdfb-120">解説</span><span class="sxs-lookup"><span data-stu-id="bcdfb-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcdfb-121">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="bcdfb-121">The interface is available with .NET Native only.</span></span> <span data-ttu-id="bcdfb-122">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="bcdfb-122">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcdfb-123">要件</span><span class="sxs-lookup"><span data-stu-id="bcdfb-123">Requirements</span></span>  

 <span data-ttu-id="bcdfb-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcdfb-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcdfb-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcdfb-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcdfb-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcdfb-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcdfb-127">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcdfb-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcdfb-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcdfb-128">See also</span></span>

- [<span data-ttu-id="bcdfb-129">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="bcdfb-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bcdfb-130">デバッグ</span><span class="sxs-lookup"><span data-stu-id="bcdfb-130">Debugging</span></span>](index.md)

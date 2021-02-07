---
description: 詳細については、「デバッグインターフェイス」を参照してください。
title: デバッグのインターフェイス
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 6e6cc07e200b9ecf6bf4039f4fd5fd69e27b6fda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717967"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="19511-103">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="19511-103">Debugging Interfaces</span></span>

<span data-ttu-id="19511-104">ここでは、共通言語ランタイム (CLR: Common Language Runtime) で実行するプログラムのデバッグを処理するアンマネージ インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="19511-104">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19511-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="19511-105">In This Section</span></span>  

 <span data-ttu-id="19511-106">[ICLRDataEnumMemoryRegions インターフェイス](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-106">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="19511-107">呼び出し元が指定したメモリ範囲を列挙するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-107">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="19511-108">[ICLRDataEnumMemoryRegionsCallback インターフェイス](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-108">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="19511-109">メモリの指定された領域を列挙した結果の `EnumMemoryRegions` をデバッガーにレポートするコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-109">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="19511-110">[ICLRDataTarget インターフェイス](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-110">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="19511-111">対象の CLR プロセスと対話するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-111">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="19511-112">[ICLRDataTarget2 インターフェイス](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-112">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="19511-113">データ アクセス サービス層で使用して対象プロセスの仮想メモリ領域を操作する、`ICLRDataTarget` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="19511-113">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="19511-114">[ICLRDataTarget3 インターフェイス](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-114">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="19511-115">例外情報へのアクセスを提供する [ICLRDataTarget2](iclrdatatarget2-interface.md) のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="19511-115">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="19511-116">[ICLRDebugging インターフェイス](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-116">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="19511-117">デバッグ用にモジュールの読み込みとアンロードを処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-117">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="19511-118">[ICLRDebuggingLibraryProvider インターフェイス](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-118">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="19511-119">には、提供 [ライブラリのメソッド](iclrdebugginglibraryprovider-providelibrary-method.md) メソッドが含まれています。このメソッドは、共通言語ランタイムのバージョン固有のデバッグライブラリをオンデマンドで検索して読み込むことができるようにする、ライブラリプロバイダーのコールバックインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="19511-119">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="19511-120">[ICLRMetadataLocator インターフェイス](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-120">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="19511-121">データ アクセス サービス層で使用して、対象プロセス内のアセンブリのメタデータを見つけるためのインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="19511-121">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="19511-122">[ICorDebug インターフェイス](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-122">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="19511-123">開発者が CLR 環境でアプリケーションをデバッグできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-123">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="19511-124">[の Appdomain インターフェイス](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-124">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="19511-125">アプリケーション ドメインをデバッグするためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-125">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="19511-126">[ICorDebugAppDomain2 インターフェイス](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-126">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="19511-127">配列、ポインター、関数ポインター、および ByRef 型を使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-127">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="19511-128">これは、`ICorDebugAppDomain` インターフェイスの機能を拡張するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="19511-128">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="19511-129">[ICorDebugAppDomain3 インターフェイス](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-129">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="19511-130">アプリケーションドメインの Windows ランタイム型を操作するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-130">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="19511-131">このインターフェイスは、`ICorDebugAppDomain` インターフェイスと `ICorDebugAppDomain2` インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-131">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="19511-132">[ICorDebugAppDomain4 インターフェイス](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-132">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="19511-133">コードを論理的に拡張して、COM 呼び出し可能ラッパーからマネージオブジェクトを [取得します](icordebugappdomain-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="19511-133">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="19511-134">[ICorDebugAppDomainEnum インターフェイス](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-134">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="19511-135">列挙体の次の位置から、指定した数の `ICorDebugAppDomain` の値を返すメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-135">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="19511-136">[ICorDebugArrayValue インターフェイス](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-136">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="19511-137">1 次元または多次元の配列を表す `ICorDebugHeapValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="19511-137">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="19511-138">[のアセンブリインターフェイス](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-138">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="19511-139">アセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-139">Represents an assembly.</span></span>  
  
 <span data-ttu-id="19511-140">[ICorDebugAssembly2 インターフェイス](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-140">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="19511-141">アセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-141">Represents an assembly.</span></span> <span data-ttu-id="19511-142">これは、`ICorDebugAssembly` インターフェイスの機能を拡張するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="19511-142">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="19511-143">[ICorDebugAssembly3 インターフェイス](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-143">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="19511-144">は、この [アセンブリ](icordebugassembly-interface.md) インターフェイスを論理的に拡張して、コンテナーアセンブリとそれに含まれるアセンブリのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-144">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="19511-145">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-145">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-146">[いいね。インターフェイス](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-146">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="19511-147">`ICorDebugEnum` メソッドを実装し、`ICorDebugAssembly` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="19511-147">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="19511-148">[ICorDebugBlockingObjectEnum インターフェイス](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-148">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="19511-149">[CorDebugBlockingObject](cordebugblockingobject-structure.md)構造体のリストの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-149">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="19511-150">[の値のインターフェイス](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-150">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="19511-151">ボックス化された値クラスのオブジェクトを表す `ICorDebugHeapValue` のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="19511-151">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="19511-152">[ICorDebugBreakpoint インターフェイス](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-152">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="19511-153">関数のブレークポイント、または値のウォッチ ポイントを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-153">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="19511-154">[いいね Pointenum インターフェイス](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-154">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="19511-155">`ICorDebugEnum` メソッドを実装し、`ICorDebugBreakpoint` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="19511-155">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="19511-156">[というチェーンインターフェイス](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-156">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="19511-157">物理呼び出し履歴または論理呼び出し履歴のセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-157">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="19511-158">[ICorDebugChainEnum インターフェイス](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-158">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="19511-159">`ICorDebugEnum` メソッドを実装し、`ICorDebugChain` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="19511-159">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="19511-160">[のクラスインターフェイス](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-160">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="19511-161">基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。</span><span class="sxs-lookup"><span data-stu-id="19511-161">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="19511-162">型がジェネリックの場合、`ICorDebugClass` はインスタンス化されないジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="19511-162">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="19511-163">[ICorDebugClass2 インターフェイス](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-163">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="19511-164">ジェネリック、または <xref:System.Type> 型のメソッド パラメーターを持つクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-164">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="19511-165">このインターフェイスは、`ICorDebugClass` の機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-165">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="19511-166">[のコードインターフェイス](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="19511-166">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="19511-167">Microsoft Intermediate Language (MSIL) コードまたはネイティブ コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-167">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="19511-168">[ICorDebugCode2 インターフェイス](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-168">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="19511-169">`ICorDebugCode` の機能を拡張するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-169">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="19511-170">[ICorDebugCode3 インターフェイス](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-170">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="19511-171">[コード](icordebugcode-interface1.md)と[ICorDebugCode2](icordebugcode2-interface.md)を拡張して、マネージ戻り値に関する情報を提供するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-171">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="19511-172">[ICorDebugCode4 インターフェイス](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-172">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="19511-173">デバッガーが関数のローカル変数と引数を列挙できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-173">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="19511-174">[のコードの列挙型インターフェイス](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-174">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="19511-175">`ICorDebugEnum` メソッドを実装し、`ICorDebugCode` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="19511-175">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="19511-176">[「いいね! 値インターフェイス」](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-176">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="19511-177">キャッシュされたインターフェイス オブジェクトを取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-177">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="19511-178">[テキストコンテキストインターフェイス](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-178">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="19511-179">コンテキストのオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-179">Represents a context object.</span></span> <span data-ttu-id="19511-180">このインターフェイスはまだ実装されていません。</span><span class="sxs-lookup"><span data-stu-id="19511-180">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="19511-181">[のコントロールインターフェイス](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-181">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="19511-182">コードの実行コンテキストを制御できる <xref:System.Diagnostics.Process> または <xref:System.AppDomain> のスコープを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-182">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="19511-183">[の場合は、このインターフェイス](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-183">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="19511-184">特定のターゲット プロセスにアクセスするためのコールバック インターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="19511-184">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="19511-185">[ICorDebugDataTarget2 インターフェイス](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-185">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="19511-186">によって、"の" を論理的に [拡張します](icordebugdatatarget-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="19511-186">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="19511-187">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-187">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-188">[ICorDebugDataTarget3 インターフェイス](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-188">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="19511-189">提供され [たモジュール](icordebugdatatarget-interface.md) に関する情報を提供するために、によって、参照インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-189">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="19511-190">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-190">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-191">[のイベントインターフェイス](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-191">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="19511-192">すべての `ICorDebug` デバッグ イベントを派生させる基本インターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="19511-192">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="19511-193">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-193">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-194">[ICorDebugEditAndContinueErrorInfo インターフェイス](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-194">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="19511-195">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="19511-195">Obsolete.</span></span> <span data-ttu-id="19511-196">このインターフェイスは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="19511-196">Do not use this interface.</span></span>  
  
 <span data-ttu-id="19511-197">[ICorDebugEditAndContinueSnapshot インターフェイス](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-197">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="19511-198">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="19511-198">Obsolete.</span></span> <span data-ttu-id="19511-199">このインターフェイスは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="19511-199">Do not use this interface.</span></span>  
  
 <span data-ttu-id="19511-200">[ICorDebugEnum インターフェイス](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="19511-200">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="19511-201">デバッグ中の列挙子の抽象基底インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="19511-201">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="19511-202">[いいね Infoenum インターフェイス](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-202">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="19511-203">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="19511-203">Obsolete.</span></span> <span data-ttu-id="19511-204">このインターフェイスは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="19511-204">Do not use this interface.</span></span>  
  
 <span data-ttu-id="19511-205">[の場合は、インターフェイス](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-205">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="19511-206">デバッガーが、デバッグ中のコードのコンテキスト内でコードを実行できるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-206">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="19511-207">[ICorDebugEval2 インターフェイス](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-207">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="19511-208">ジェネリック型をサポートできるように `ICorDebugEval` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-208">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="19511-209">[は、の例外のイベントインターフェイス](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-209">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="19511-210">は、例外イベントをサポートするために、の [イベント](icordebugdebugevent-interface.md) インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-210">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="19511-211">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-211">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-212">[いい Exceptionobjectcallstackenum インターフェイス](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-212">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="19511-213">例外オブジェクトに埋め込まれているコール スタックの情報の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-213">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="19511-214">[の値インターフェイス](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-214">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="19511-215">によっ [て、](icordebugobjectvalue-interface.md) のマネージ例外オブジェクトからスタックトレース情報を提供するように、の機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-215">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="19511-216">[テキストフレームインターフェイス](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-216">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="19511-217">現在のスタックのフレームを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-217">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="19511-218">[の場合は、インターフェイスの列挙体](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-218">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="19511-219">`ICorDebugEnum` メソッドを実装し、`ICorDebugFrame` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="19511-219">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="19511-220">[の関数インターフェイス](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="19511-220">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="19511-221">マネージド関数またはマネージド メソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-221">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="19511-222">[ICorDebugFunction2 インターフェイス](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-222">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="19511-223">`ICorDebugFunction` を論理的に拡張して、"マイ コードのみ" ステップ実行によるデバッグをサポートします。</span><span class="sxs-lookup"><span data-stu-id="19511-223">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="19511-224">[ICorDebugFunction3 インターフェイス](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-224">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="19511-225">により、再 Jit 要求からコードへのアクセスを提供するために、の [関数](icordebugfunction-interface1.md) インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-225">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="19511-226">[いいね! ブレークポイントインターフェイス](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-226">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="19511-227">関数内のブレークポイントをサポートするように `ICorDebugBreakpoint` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-227">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="19511-228">["いいね!" インターフェイスの列挙](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-228">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="19511-229">ガベージ コレクトされるオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-229">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="19511-230">[の値インターフェイス](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-230">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="19511-231">すべての値に適用する `ICorDebugValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="19511-231">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="19511-232">このインターフェイスは、値に対して Get メソッドと Set メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-232">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="19511-233">[は、"いいね" インターフェイス](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-233">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="19511-234">GUID およびその対応する `ICorDebugType` オブジェクトをマップするオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-234">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="19511-235">[の値インターフェイス](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-235">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="19511-236">デバッガーが作成したガベージ コレクションのハンドルへの参照値を表す `ICorDebugReferenceValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="19511-236">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="19511-237">[このインターフェイスは、このインターフェイスによって](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-237">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="19511-238">マネージド ヒープのオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-238">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="19511-239">[ICorDebugHeapSegmentEnum インターフェイス](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-239">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="19511-240">マネージド ヒープのメモリ領域の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-240">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="19511-241">["いいね!" インターフェイス](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-241">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="19511-242">CLR ガベージ コレクターによって収集されたオブジェクトを表す `ICorDebugValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="19511-242">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="19511-243">[ICorDebugHeapValue2 インターフェイス](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="19511-243">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="19511-244">ランタイム ハンドルのサポートを提供する `ICorDebugHeapValue` の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="19511-244">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="19511-245">[ICorDebugHeapValue3 インターフェイス](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-245">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="19511-246">オブジェクトのモニター ロック プロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="19511-246">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="19511-247">[のコードインターフェイス](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-247">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="19511-248">中間言語 (IL) コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-248">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="19511-249">[ICorDebugILCode2 インターフェイス](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-249">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="19511-250">では、この [コード](icordebugilcode-interface.md) インターフェイスを論理的に拡張して、関数のローカル変数シグネチャのトークンを返すメソッドを提供し、プロファイラーのインストルメント化された中間言語 (il) オフセットを元のメソッドの il オフセットにマップします。</span><span class="sxs-lookup"><span data-stu-id="19511-250">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="19511-251">[いいね! のインターフェイス](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-251">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="19511-252">MSIL コードのスタック フレームを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-252">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="19511-253">[ICorDebugILFrame2 インターフェイス](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-253">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="19511-254">`ICorDebugILFrame` の論理拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="19511-254">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="19511-255">[ICorDebugILFrame3 インターフェイス](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-255">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="19511-256">関数の戻り値をカプセル化するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-256">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="19511-257">[ICorDebugILFrame4 インターフェイス](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-257">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="19511-258">ローカル変数にアクセスできるようにするメソッドおよび中間言語 (IL) コードのスタック フレームのコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-258">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="19511-259">パラメーターは、プロファイラーの ReJIT インストルメンテーションに追加される変数およびコードへデバッガーがアクセスできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="19511-259">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="19511-260">[のコードインターフェイス](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-260">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="19511-261">インスタンス フィールドのデバッグ シンボル情報を表します。</span><span class="sxs-lookup"><span data-stu-id="19511-261">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="19511-262">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-262">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-263">[のテキストフレームインターフェイス](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-263">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="19511-264">デバッガーのフレーム種類を識別します。</span><span class="sxs-lookup"><span data-stu-id="19511-264">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="19511-265">[ICorDebugInternalFrame2 インターフェイス](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-265">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="19511-266">スタックアドレスや、 [テキストフレーム](icordebugframe-interface.md) オブジェクトに対する位置など、内部フレームに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-266">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="19511-267">[ICorDebugLoadedModule インターフェイス](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-267">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="19511-268">読み込まれたモジュールについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-268">Provides information about a loaded module.</span></span> <span data-ttu-id="19511-269">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-269">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-270">[の Managedmanagedcallback インターフェイス](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-270">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="19511-271">デバッガーのコールバックを処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-271">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="19511-272">[ICorDebugManagedCallback2 インターフェイス](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-272">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="19511-273">デバッガーの例外処理およびマネージド デバッグ アシスタント (MDA: Managed Debugging Assistants) をサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-273">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="19511-274">`ICorDebugManagedCallback2` は、`ICorDebugManagedCallback` の論理拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="19511-274">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="19511-275">[ICorDebugManagedCallback3 インターフェイス](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-275">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="19511-276">有効なカスタムのデバッガー通知が発生したことを示すコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-276">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="19511-277">[は、のインターフェイス](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-277">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="19511-278">マネージド デバッグ アシスタント (MDA) メッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-278">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="19511-279">[のの Memorybuffer インターフェイス](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-279">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="19511-280">メモリ内のバッファーを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-280">Represents an in-memory buffer.</span></span> <span data-ttu-id="19511-281">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-281">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-282">[ICorDebugMergedAssemblyRecord インターフェイス](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-282">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="19511-283">マージされたアセンブリに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-283">Provides information about a merged assembly.</span></span> <span data-ttu-id="19511-284">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-284">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-285">[ICorDebugMetaDataLocator インターフェイス](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-285">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="19511-286">デバッガーにメタデータ情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-286">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="19511-287">[のモジュールインターフェイス](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-287">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="19511-288">実行可能ファイルまたはダイナミック リンク ライブラリ (DLL: Dynamic-Link Library) のいずれかの CLR モジュールを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-288">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="19511-289">[ICorDebugModule2 インターフェイス](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-289">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="19511-290">`ICorDebugModule` の論理的な拡張機能として動作します。</span><span class="sxs-lookup"><span data-stu-id="19511-290">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="19511-291">[ICorDebugModule3 インターフェイス](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-291">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="19511-292">動的モジュールのシンボル リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="19511-292">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="19511-293">[のモジュールのブレークポイントインターフェイス](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-293">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="19511-294">特定のモジュールにアクセスできるように `ICorDebugBreakpoint` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-294">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="19511-295">[いい Moduledebugevent インターフェイス](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-295">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="19511-296">モジュールレベルのイベントをサポートするように、のモジュールレベル [のイベントを](icordebugdebugevent-interface.md) 拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-296">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="19511-297">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-297">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-298">[のモジュール列挙型インターフェイス](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-298">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="19511-299">`ICorDebugEnum` メソッドを実装し、`ICorDebugModule` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="19511-299">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="19511-300">[ICorDebugMutableDataTarget インターフェイス](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-300">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="19511-301">変更可能なデータターゲットをサポートするために、の機能を拡張[します。](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-301">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="19511-302">[テキストフレームインターフェイス](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-302">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="19511-303">ネイティブ フレームで使用される `ICorDebugFrame` の特化された実装。</span><span class="sxs-lookup"><span data-stu-id="19511-303">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="19511-304">[ICorDebugNativeFrame2 インターフェイス](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-304">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="19511-305">子と親のフレームの関係をテストするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-305">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="19511-306">[このインターフェイス](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-306">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="19511-307">`ICorDebugEnum` メソッドを実装し、オブジェクトの配列を相対仮想アドレス (RVA: Relative Virtual Address) で列挙します。</span><span class="sxs-lookup"><span data-stu-id="19511-307">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="19511-308">[の値インターフェイス](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-308">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="19511-309">オブジェクトが含まれた値を表す `ICorDebugValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="19511-309">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="19511-310">[ICorDebugObjectValue2 インターフェイス](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-310">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="19511-311">継承およびオーバーライドをサポートするように `ICorDebugObjectValue` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-311">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="19511-312">[のプロセスインターフェイス](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-312">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="19511-313">マネージド コードを実行しているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-313">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="19511-314">[ICorDebugProcess2 インターフェイス](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="19511-314">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="19511-315">`ICorDebugProcess` の論理拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="19511-315">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="19511-316">[ICorDebugProcess3 インターフェイス](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-316">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="19511-317">カスタムのデバッガー通知を制御します。</span><span class="sxs-lookup"><span data-stu-id="19511-317">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="19511-318">[ICorDebugProcess4 インターフェイス](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-318">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="19511-319">アウトプロセス実行制御のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-319">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="19511-320">[ICorDebugProcess5 インターフェイス](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-320">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="19511-321">[は、](icordebugprocess-interface.md)マネージヒープへのアクセスをサポートし、マネージオブジェクトのガベージコレクションに関する情報を提供し、デバッガーがアプリケーションのローカルのネイティブイメージキャッシュからイメージを読み込むかどうかを判断するために、コードを拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-321">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="19511-322">[ICorDebugProcess6 インターフェイス](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-322">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="19511-323">コードを論理的に [拡張して、ネイティブ](icordebugprocess-interface.md) の例外デバッグイベントと仮想モジュール分割でエンコードされたマネージデバッグイベントをデコードするなどの機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="19511-323">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="19511-324">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-324">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-325">[ICorDebugProcess7 インターフェイス](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-325">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="19511-326">ターゲット プロセスでメモリ内のメタデータ更新を処理するようにデバッガーを構成するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-326">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="19511-327">[ICorDebugProcess8 インターフェイス](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-327">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="19511-328">ICorDebugManagedCallback2 [process](icordebugprocess-interface.md)インターフェイスを論理的に拡張して、特定の種類の[](icordebugmanagedcallback2-interface.md)例外コールバックを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="19511-328">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="19511-329">[の型の Processenum インターフェイス](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-329">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="19511-330">`ICorDebugEnum` メソッドを実装し、`ICorDebugProcess` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="19511-330">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="19511-331">[の値インターフェイス](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-331">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="19511-332">参照型をサポートする `ICorDebugValue` のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="19511-332">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="19511-333">[いいです。](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-333">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="19511-334">現在コードを実行しているマシン上で使用できるレジスタ セットを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-334">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="19511-335">[ICorDebugRegisterSet2 インターフェイス](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-335">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="19511-336">64 を超えるレジスタを持つハードウェア プラットフォーム用に `ICorDebugRegisterSet` の機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-336">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="19511-337">[のリモートインターフェイス](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-337">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="19511-338">リモート ターゲット プロセスに対してマネージド デバッガーを起動または接続する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-338">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="19511-339">[の Remotetarget インターフェイス](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-339">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="19511-340">開発者が CLR 環境で Silverlight ベース アプリケーションをデバッグできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-340">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="19511-341">[ICorDebugRuntimeUnwindableFrame インターフェイス](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-341">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="19511-342">共通言語ランタイム (CLR: Common Language Runtime) でフレームをアンワインドする必要のあるアンマネージ メソッドに対してサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-342">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="19511-343">[は、このインターフェイス](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-343">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="19511-344">スレッドのスタック上のマネージド メソッド (フレーム) を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-344">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="19511-345">[の場合は、コードインターフェイス](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-345">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="19511-346">静的フィールドのデバッグ シンボル情報を表します。</span><span class="sxs-lookup"><span data-stu-id="19511-346">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="19511-347">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-347">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-348">[ICorDebugStepper インターフェイス](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-348">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="19511-349">デバッガーが実行するコード実行内のステップを表します。コマンドの発行から完了までの間は識別子として機能します。これを使用するとステップをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="19511-349">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="19511-350">[ICorDebugStepper2 インターフェイス](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="19511-350">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="19511-351">マイ コードのみ (JMC: Just My Code) デバッグのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-351">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="19511-352">[というインターフェイス](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-352">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="19511-353">`ICorDebugEnum` メソッドを実装し、`ICorDebugStepper` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="19511-353">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="19511-354">[いいねインターフェイス](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-354">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="19511-355">文字列値に適用する `ICorDebugHeapValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="19511-355">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="19511-356">[は、プロバイダーインターフェイス](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-356">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="19511-357">デバッグ シンボル情報を取得するために使用できるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-357">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="19511-358">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-358">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-359">[ICorDebugSymbolProvider2 インターフェイス](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-359">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="19511-360">追加のデバッグシンボル情報を取得するために、この [プロバイダー](icordebugsymbolprovider-interface.md) インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-360">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="19511-361">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-361">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-362">[のスレッドインターフェイス](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-362">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="19511-363">プロセス内のスレッドを表します。</span><span class="sxs-lookup"><span data-stu-id="19511-363">Represents a thread in a process.</span></span> <span data-ttu-id="19511-364">`ICorDebugThread` インスタンスの有効期間は、それが表しているスレッドの有効期間と同じです。</span><span class="sxs-lookup"><span data-stu-id="19511-364">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="19511-365">[ICorDebugThread2 インターフェイス](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-365">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="19511-366">`ICorDebugThread` の論理的な拡張機能として動作します。</span><span class="sxs-lookup"><span data-stu-id="19511-366">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="19511-367">[ICorDebugThread3 インターフェイス](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-367">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="19511-368">とそれに対応するインターフェイス [へのエントリ](icordebugstackwalk-interface.md) ポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-368">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="19511-369">[ICorDebugThread4 インターフェイス](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-369">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="19511-370">スレッドのブロック情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-370">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="19511-371">[いい Threadenum インターフェイス](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="19511-371">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="19511-372">`ICorDebugEnum` メソッドを実装し、`ICorDebugThread` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="19511-372">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="19511-373">[の型のインターフェイス](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-373">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="19511-374">基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。</span><span class="sxs-lookup"><span data-stu-id="19511-374">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="19511-375">型がジェネリックの場合、`ICorDebugType` はインスタンス化されたジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="19511-375">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="19511-376">[ICorDebugType2 インターフェイス](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-376">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="19511-377">によって、テキスト型または複合型 (ユーザー定義型) の型識別子を取得するため [に、を拡張します](icordebugtype-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="19511-377">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="19511-378">[の型のインターフェイス](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-378">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="19511-379">`ICorDebugEnum` メソッドを実装し、`ICorDebugType` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="19511-379">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="19511-380">[ICorDebugUnmanagedCallback インターフェイス](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-380">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="19511-381">CLR に直接関連していないネイティブ イベントについて通知します。</span><span class="sxs-lookup"><span data-stu-id="19511-381">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="19511-382">[ICorDebugValue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-382">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="19511-383">デバッグ中のプロセス内の読み取り値または書き込み値を表します。</span><span class="sxs-lookup"><span data-stu-id="19511-383">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="19511-384">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-384">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="19511-385">`ICorDebugValue` をサポートできるように `ICorDebugType` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-385">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="19511-386">[ICorDebugValue3 インターフェイス](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-386">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="19511-387">"ICorDebugValue" インターフェイスと "ICorDebugValue2" インターフェイスを拡張して、2 GB を超える配列のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-387">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="19511-388">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-388">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="19511-389">特定の値にアクセスできるように `ICorDebugBreakpoint` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="19511-389">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="19511-390">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-390">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="19511-391">`ICorDebugEnum` メソッドを実装し、`ICorDebugValue` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="19511-391">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="19511-392">[ページホームインターフェイス](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-392">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="19511-393">関数のローカル変数または引数を表します。</span><span class="sxs-lookup"><span data-stu-id="19511-393">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="19511-394">[の型の変数の列挙型インターフェイス](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-394">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="19511-395">関数のローカル変数および引数に列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-395">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="19511-396">[ICorDebugVariableSymbol インターフェイス](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-396">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="19511-397">変数のデバッグ シンボル情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="19511-397">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="19511-398">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-398">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-399">[ICorDebugVirtualUnwinder インターフェイス](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-399">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="19511-400">スタック アンワインドを支援するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-400">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="19511-401">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="19511-401">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="19511-402">[ICorPublish インターフェイス](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-402">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="19511-403">発行プロセスの汎用インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="19511-403">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="19511-404">[ICorPublishAppDomain インターフェイス](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-404">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="19511-405">アプリケーション ドメインの情報を表し、提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-405">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="19511-406">[ICorPublishAppDomainEnum インターフェイス](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-406">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="19511-407">現在プロセス内に存在する `ICorPublishAppDomain` オブジェクトのコレクションを走査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-407">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="19511-408">[ICorPublishEnum インターフェイス](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-408">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="19511-409">発行する列挙子の抽象ベースとして機能します。</span><span class="sxs-lookup"><span data-stu-id="19511-409">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="19511-410">[ICorPublishProcess インターフェイス](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-410">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="19511-411">プロセスの情報にアクセスするメソッドを適用します。</span><span class="sxs-lookup"><span data-stu-id="19511-411">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="19511-412">[ICorPublishProcessEnum インターフェイス](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-412">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="19511-413">`ICorPublishProcess` オブジェクトのコレクションを走査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-413">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="19511-414">[ISOSDacInterface インターフェイス](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-414">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="19511-415">からデータにアクセスするためのヘルパーメソッドを提供 `SOS` します。</span><span class="sxs-lookup"><span data-stu-id="19511-415">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="19511-416">[IXCLRDataMethodDefinition インターフェイス](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-416">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="19511-417">メソッド定義に関する情報を照会するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-417">Provides methods for querying information about a method definition.</span></span>

 <span data-ttu-id="19511-418">[IXCLRDataMethodInstance インターフェイス](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-418">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="19511-419">メソッドインスタンスに関する情報を照会するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-419">Provides methods for querying information about a method instance.</span></span>

 <span data-ttu-id="19511-420">[IXCLRDataModule インターフェイス](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-420">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="19511-421">読み込まれたモジュールに関する情報を照会するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-421">Provides methods for querying information about a loaded module.</span></span>

 <span data-ttu-id="19511-422">[IXCLRDataProcess インターフェイス](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="19511-422">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="19511-423">プロセスに関する情報を照会するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19511-423">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="19511-424">関連項目</span><span class="sxs-lookup"><span data-stu-id="19511-424">Related Sections</span></span>  

 <span data-ttu-id="19511-425">[デバッグコクラス](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="19511-425">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="19511-426">[デバッググローバル静的関数](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="19511-426">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="19511-427">[列挙型のデバッグ](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="19511-427">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="19511-428">[デバッグ構造体](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="19511-428">[Debugging Structures](debugging-structures.md)</span></span>\

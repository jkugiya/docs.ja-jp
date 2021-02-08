---
description: '詳細情報: シンボルストアの診断インターフェイス'
title: シンボル ストア診断インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: 253a6e5eaa97c91332bca62f8fc47ad2945bf741
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800436"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="bef2d-103">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-103">Diagnostics Symbol Store Interfaces</span></span>

<span data-ttu-id="bef2d-104">このトピックでは、コンパイラがデバッガーで使用するシンボル情報を生成できるようにするアンマネージインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-104">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bef2d-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bef2d-105">In This Section</span></span>  

 [<span data-ttu-id="bef2d-106">IBindingDisplay インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-106">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)  
 <span data-ttu-id="bef2d-107">実行中のアプリケーションに関する現在のバインド情報を表示するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-107">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="bef2d-108">IDebugAutoAttach インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-108">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)  
 <span data-ttu-id="bef2d-109">サーバーによって呼び出されるデバッガーの自動アタッチのインターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-109">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="bef2d-110">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-110">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)  
 <span data-ttu-id="bef2d-111">接続通知ソースを登録および登録解除するためのメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-111">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="bef2d-112">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-112">INotifySink2 Interface</span></span>](inotifysink2-interface.md)  
 <span data-ttu-id="bef2d-113">シンク通知のメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-113">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="bef2d-114">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)  
 <span data-ttu-id="bef2d-115">通知フィルターを設定するためのメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-115">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="bef2d-116">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-116">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="bef2d-117">エディットコンティニュ機能に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-117">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="bef2d-118">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-118">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="bef2d-119">このインターフェイスは、 [ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス](isymunmanagedasyncmethodpropertieswriter-interface.md)への読み取り補数です。</span><span class="sxs-lookup"><span data-stu-id="bef2d-119">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="bef2d-120">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-120">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="bef2d-121">メソッドシンボルごとにオプションの非同期メソッド情報を定義できます。</span><span class="sxs-lookup"><span data-stu-id="bef2d-121">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="bef2d-122">は、開いているメソッド (つまり、 [Openmethod メソッド](isymunmanagedwriter-openmethod-method.md)と [closemethod メソッド](isymunmanagedwriter-closemethod-method.md)の呼び出しの間) でを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bef2d-122">Must use with an opened method (that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="bef2d-123">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-123">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)  
 <span data-ttu-id="bef2d-124">アンマネージド コードのシンボル バインダーを表します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-124">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="bef2d-125">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-125">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="bef2d-126">アンマネージコードのシンボルバインダーを表し、インターフェイスを拡張し `ISymUnmanagedBinder` ます。</span><span class="sxs-lookup"><span data-stu-id="bef2d-126">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="bef2d-127">ISymUnmanagedBinder3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-127">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="bef2d-128">アンマネージコードのシンボルバインダーを表し、インターフェイスを拡張し `ISymUnmanagedBinder` ます。</span><span class="sxs-lookup"><span data-stu-id="bef2d-128">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="bef2d-129">ISymUnmanagedConstant インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-129">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)  
 <span data-ttu-id="bef2d-130">アンマネージ定数へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-130">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="bef2d-131">ISymUnmanagedDispose インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-131">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)  
 <span data-ttu-id="bef2d-132">アンマネージリソースを破棄します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-132">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="bef2d-133">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-133">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)  
 <span data-ttu-id="bef2d-134">シンボル ストアによって参照されるドキュメントを表します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-134">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="bef2d-135">ISymUnmanagedDocumentWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-135">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="bef2d-136">シンボル ストアで参照されるドキュメントに書き込むためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-136">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="bef2d-137">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-137">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="bef2d-138">エディットコンティニュ機能のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-138">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="bef2d-139">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-139">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)  
 <span data-ttu-id="bef2d-140">シンボル ストア内のメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-140">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="bef2d-141">ISymUnmanagedNamespace インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-141">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)  
 <span data-ttu-id="bef2d-142">名前空間を表します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-142">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="bef2d-143">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-143">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)  
 <span data-ttu-id="bef2d-144">シンボル ストア内のドキュメント、メソッド、および変数へのアクセスを提供するシンボル リーダーを表します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-144">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="bef2d-145">ISymUnmanagedReader2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-145">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)  
 <span data-ttu-id="bef2d-146">メソッドトークンと編集およびコピーバージョン番号を指定して、シンボルリーダーメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-146">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="bef2d-147">ISymUnmanagedReaderSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-147">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="bef2d-148">シンボル検索情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-148">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="bef2d-149">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-149">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)  
 <span data-ttu-id="bef2d-150">メソッド内の構文のスコープを表します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-150">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="bef2d-151">ISymUnmanagedScope2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-151">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)  
 <span data-ttu-id="bef2d-152">メソッド内の構文のスコープを表し、 `ISymUnmanagedScope` スコープ内で定義された定数に関する情報を取得するメソッドを使用してインターフェイスを拡張します。「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bef2d-152">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="bef2d-153">ISymUnmanagedSourceServerModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-153">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="bef2d-154">モジュールのソースサーバーデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-154">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="bef2d-155">ISymUnmanagedSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-155">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="bef2d-156">検索パスに関する情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-156">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="bef2d-157">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-157">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)  
 <span data-ttu-id="bef2d-158">パラメーター、ローカル変数、またはフィールドなどの変数を表します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-158">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="bef2d-159">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-159">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)  
 <span data-ttu-id="bef2d-160">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文スコープ、変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-160">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="bef2d-161">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-161">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="bef2d-162">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文スコープ、変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-162">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="bef2d-163">インターフェイスを拡張 `ISymUnmanagedWriter` します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-163">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="bef2d-164">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-164">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="bef2d-165">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文スコープ、変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-165">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="bef2d-166">インターフェイスを拡張 `ISymUnmanagedWriter` します。</span><span class="sxs-lookup"><span data-stu-id="bef2d-166">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="bef2d-167">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-167">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="bef2d-168">ISymUnmanagedWriter4 インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="bef2d-168">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="bef2d-169">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bef2d-169">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="bef2d-170">ISymUnmanagedWriter5 インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="bef2d-170">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bef2d-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="bef2d-171">Related Sections</span></span>  

 [<span data-ttu-id="bef2d-172">シンボル ストア診断列挙型</span><span class="sxs-lookup"><span data-stu-id="bef2d-172">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="bef2d-173">シンボル ストア診断構造体</span><span class="sxs-lookup"><span data-stu-id="bef2d-173">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="bef2d-174">デバッグ</span><span class="sxs-lookup"><span data-stu-id="bef2d-174">Debugging</span></span>](../debugging/index.md)

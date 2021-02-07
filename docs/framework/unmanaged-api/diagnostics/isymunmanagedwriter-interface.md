---
description: 詳細については、「ISymUnmanagedWriter インターフェイス」を参照してください。
title: ISymUnmanagedWriter インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
ms.openlocfilehash: 20fc0fd9b76b1aae4090582fe48a8a8e77d77c9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762241"
---
# <a name="isymunmanagedwriter-interface"></a><span data-ttu-id="63273-103">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63273-103">ISymUnmanagedWriter Interface</span></span>

<span data-ttu-id="63273-104">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文スコープ、変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="63273-104">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63273-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-105">Methods</span></span>  
  
|<span data-ttu-id="63273-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-106">Method</span></span>|<span data-ttu-id="63273-107">説明</span><span class="sxs-lookup"><span data-stu-id="63273-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63273-108">Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-108">Abort Method</span></span>](isymunmanagedwriter-abort-method.md)|<span data-ttu-id="63273-109">シンボルストアにシンボルをコミットせずにシンボルライターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="63273-109">Closes the symbol writer without committing the symbols to the symbol store.</span></span>|  
|[<span data-ttu-id="63273-110">Close メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-110">Close Method</span></span>](isymunmanagedwriter-close-method.md)|<span data-ttu-id="63273-111">シンボルをシンボルストアにコミットした後、シンボルライターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="63273-111">Closes the symbol writer after committing the symbols to the symbol store.</span></span>|  
|[<span data-ttu-id="63273-112">CloseMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-112">CloseMethod Method</span></span>](isymunmanagedwriter-closemethod-method.md)|<span data-ttu-id="63273-113">現在のメソッドを閉じます。</span><span class="sxs-lookup"><span data-stu-id="63273-113">Closes the current method.</span></span> <span data-ttu-id="63273-114">メソッドを閉じると、それ以上シンボルを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="63273-114">Once a method is closed, no more symbols can be defined within it.</span></span>|  
|[<span data-ttu-id="63273-115">CloseNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-115">CloseNamespace Method</span></span>](isymunmanagedwriter-closenamespace-method.md)|<span data-ttu-id="63273-116">最近開いた名前空間を閉じます。</span><span class="sxs-lookup"><span data-stu-id="63273-116">Closes the most recently opened namespace.</span></span>|  
|[<span data-ttu-id="63273-117">CloseScope メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-117">CloseScope Method</span></span>](isymunmanagedwriter-closescope-method.md)|<span data-ttu-id="63273-118">現在の構文のスコープを閉じます。</span><span class="sxs-lookup"><span data-stu-id="63273-118">Closes the current lexical scope.</span></span>|  
|[<span data-ttu-id="63273-119">DefineConstant メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-119">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)|<span data-ttu-id="63273-120">定数値の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="63273-120">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="63273-121">DefineDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-121">DefineDocument Method</span></span>](isymunmanagedwriter-definedocument-method.md)|<span data-ttu-id="63273-122">ソース ドキュメントを定義します。</span><span class="sxs-lookup"><span data-stu-id="63273-122">Defines a source document.</span></span>|  
|[<span data-ttu-id="63273-123">DefineField メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-123">DefineField Method</span></span>](isymunmanagedwriter-definefield-method.md)|<span data-ttu-id="63273-124">メソッド内にない単一の変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="63273-124">Defines a single variable that is not within a method.</span></span>|  
|[<span data-ttu-id="63273-125">DefineGlobalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-125">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)|<span data-ttu-id="63273-126">グローバル変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="63273-126">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="63273-127">DefineLocalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-127">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)|<span data-ttu-id="63273-128">現在の構文のスコープの変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="63273-128">Defines a single variable in the current lexical scope.</span></span>|  
|[<span data-ttu-id="63273-129">DefineParameter メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-129">DefineParameter Method</span></span>](isymunmanagedwriter-defineparameter-method.md)|<span data-ttu-id="63273-130">現在のメソッドのパラメーターを 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="63273-130">Defines a single parameter in the current method.</span></span>|  
|[<span data-ttu-id="63273-131">DefineSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-131">DefineSequencePoints Method</span></span>](isymunmanagedwriter-definesequencepoints-method.md)|<span data-ttu-id="63273-132">現在のメソッド内のシーケンス ポイントのグループを定義します。</span><span class="sxs-lookup"><span data-stu-id="63273-132">Defines a group of sequence points within the current method.</span></span>|  
|[<span data-ttu-id="63273-133">GetDebugInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-133">GetDebugInfo Method</span></span>](isymunmanagedwriter-getdebuginfo-method.md)|<span data-ttu-id="63273-134">コンパイラがポータブル実行可能 (PE) ファイルヘッダーにデバッグディレクトリエントリを書き込むために必要な情報を返します。</span><span class="sxs-lookup"><span data-stu-id="63273-134">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span>|  
|[<span data-ttu-id="63273-135">Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-135">Initialize Method</span></span>](isymunmanagedwriter-initialize-method.md)|<span data-ttu-id="63273-136">このライターが関連付けられるメタデータエミッタインターフェイスを設定し、デバッグシンボルの書き込み先となる出力ファイル名を設定します。</span><span class="sxs-lookup"><span data-stu-id="63273-136">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>|  
|[<span data-ttu-id="63273-137">Initialize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-137">Initialize2 Method</span></span>](isymunmanagedwriter-initialize2-method.md)|<span data-ttu-id="63273-138">このライターが関連付けられるメタデータエミッタインターフェイスを設定し、デバッグシンボルの書き込み先となる出力ファイル名を設定し、プログラムデータベース (PDB) ファイルの最終的な場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="63273-138">Sets the metadata emitter interface with which this writer will be associated, sets the output file name to which the debugging symbols will be written, and sets the final location of the program database (PDB) file.</span></span>|  
|[<span data-ttu-id="63273-139">OpenMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-139">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)|<span data-ttu-id="63273-140">シンボル情報を出力するメソッドを開きます。</span><span class="sxs-lookup"><span data-stu-id="63273-140">Opens a method into which symbol information is emitted.</span></span>|  
|[<span data-ttu-id="63273-141">OpenNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-141">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)|<span data-ttu-id="63273-142">新しい名前空間を開きます。</span><span class="sxs-lookup"><span data-stu-id="63273-142">Opens a new namespace.</span></span>|  
|[<span data-ttu-id="63273-143">OpenScope メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-143">OpenScope Method</span></span>](isymunmanagedwriter-openscope-method.md)|<span data-ttu-id="63273-144">現在のメソッドの構文の新しいスコープを開きます。</span><span class="sxs-lookup"><span data-stu-id="63273-144">Opens a new lexical scope in the current method.</span></span>|  
|[<span data-ttu-id="63273-145">RemapToken メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-145">RemapToken Method</span></span>](isymunmanagedwriter-remaptoken-method.md)|<span data-ttu-id="63273-146">メタデータが生成されたときにメタデータトークンが再マップされたことをシンボルライターに通知します。</span><span class="sxs-lookup"><span data-stu-id="63273-146">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span>|  
|[<span data-ttu-id="63273-147">SetMethodSourceRange メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-147">SetMethodSourceRange Method</span></span>](isymunmanagedwriter-setmethodsourcerange-method.md)|<span data-ttu-id="63273-148">ソース ファイル内にメソッドの実際の先頭と末尾を指定します。</span><span class="sxs-lookup"><span data-stu-id="63273-148">Specifies the true start and end of a method within a source file.</span></span>|  
|[<span data-ttu-id="63273-149">SetScopeRange メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-149">SetScopeRange Method</span></span>](isymunmanagedwriter-setscoperange-method.md)|<span data-ttu-id="63273-150">指定した構文のスコープのオフセット範囲を定義します。</span><span class="sxs-lookup"><span data-stu-id="63273-150">Defines the offset range for the specified lexical scope.</span></span>|  
|[<span data-ttu-id="63273-151">SetSymAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-151">SetSymAttribute Method</span></span>](isymunmanagedwriter-setsymattribute-method.md)|<span data-ttu-id="63273-152">名前に基づいてカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="63273-152">Defines a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="63273-153">SetUserEntryPoint メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-153">SetUserEntryPoint Method</span></span>](isymunmanagedwriter-setuserentrypoint-method.md)|<span data-ttu-id="63273-154">このモジュールのエントリポイントであるユーザー定義メソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="63273-154">Specifies the user-defined method that is the entry point for this module.</span></span>|  
|[<span data-ttu-id="63273-155">UsingNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="63273-155">UsingNamespace Method</span></span>](isymunmanagedwriter-usingnamespace-method.md)|<span data-ttu-id="63273-156">現在開いている構文のスコープ内で、指定された完全修飾名前空間名が使用されていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="63273-156">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63273-157">要件</span><span class="sxs-lookup"><span data-stu-id="63273-157">Requirements</span></span>  

 <span data-ttu-id="63273-158">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="63273-158">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63273-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="63273-159">See also</span></span>

- [<span data-ttu-id="63273-160">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63273-160">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="63273-161">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63273-161">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="63273-162">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63273-162">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)

---
description: 詳細については、「ISymUnmanagedReader インターフェイス」を参照してください。
title: ISymUnmanagedReader インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
ms.openlocfilehash: bad4fdbac3bf6f03fa0db79ce54a5b0ca897028f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763801"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="7c639-103">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c639-103">ISymUnmanagedReader Interface</span></span>

<span data-ttu-id="7c639-104">シンボル ストア内のドキュメント、メソッド、および変数へのアクセスを提供するシンボル リーダーを表します。</span><span class="sxs-lookup"><span data-stu-id="7c639-104">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c639-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-105">Methods</span></span>  
  
|<span data-ttu-id="7c639-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-106">Method</span></span>|<span data-ttu-id="7c639-107">説明</span><span class="sxs-lookup"><span data-stu-id="7c639-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c639-108">GetDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-108">GetDocument Method</span></span>](isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="7c639-109">ドキュメントを検索します。</span><span class="sxs-lookup"><span data-stu-id="7c639-109">Finds a document.</span></span>|  
|[<span data-ttu-id="7c639-110">GetDocuments メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-110">GetDocuments Method</span></span>](isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="7c639-111">シンボルストアに定義されているすべてのドキュメントの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="7c639-111">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="7c639-112">GetDocumentVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-112">GetDocumentVersion Method</span></span>](isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="7c639-113">指定したドキュメントの指定したバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="7c639-113">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="7c639-114">GetGlobalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-114">GetGlobalVariables Method</span></span>](isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="7c639-115">すべてのグローバル変数を返します。</span><span class="sxs-lookup"><span data-stu-id="7c639-115">Returns all global variables.</span></span>|  
|[<span data-ttu-id="7c639-116">GetMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-116">GetMethod Method</span></span>](isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="7c639-117">メソッドトークンを指定して、シンボルリーダーメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="7c639-117">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="7c639-118">GetMethodByVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-118">GetMethodByVersion Method</span></span>](isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="7c639-119">メソッドトークンと編集およびコピーバージョン番号を指定して、シンボルリーダーメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="7c639-119">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="7c639-120">GetMethodFromDocumentPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-120">GetMethodFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="7c639-121">ドキュメント内の指定された位置にあるブレークポイントを含むメソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="7c639-121">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="7c639-122">GetMethodsFromDocumentPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-122">GetMethodsFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="7c639-123">メソッドの配列を返します。各メソッドには、ドキュメント内の指定された位置にあるブレークポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c639-123">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="7c639-124">GetMethodVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-124">GetMethodVersion Method</span></span>](isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="7c639-125">メソッドのバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="7c639-125">Gets the method version.</span></span>|  
|[<span data-ttu-id="7c639-126">GetNamespaces メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-126">GetNamespaces Method</span></span>](isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="7c639-127">このシンボルストア内のグローバルスコープで定義されている名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="7c639-127">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="7c639-128">GetSymAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-128">GetSymAttribute Method</span></span>](isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="7c639-129">名前に基づいてカスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="7c639-129">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="7c639-130">GetSymbolStoreFileName メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-130">GetSymbolStoreFileName Method</span></span>](isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="7c639-131">シンボルストアのディスク上のファイル名を提供します。</span><span class="sxs-lookup"><span data-stu-id="7c639-131">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="7c639-132">GetUserEntryPoint メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-132">GetUserEntryPoint Method</span></span>](isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="7c639-133">モジュールのユーザーエントリポイントとして指定されたメソッド (存在する場合) を返します。</span><span class="sxs-lookup"><span data-stu-id="7c639-133">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="7c639-134">GetVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-134">GetVariables Method</span></span>](isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="7c639-135">親と名前を指定して、非ローカル変数を返します。</span><span class="sxs-lookup"><span data-stu-id="7c639-135">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="7c639-136">Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-136">Initialize Method</span></span>](isymunmanagedreader-initialize-method.md)|<span data-ttu-id="7c639-137">このリーダーが関連付けられるメタデータインポーターインターフェイスと、モジュールのファイル名を使用して、シンボルリーダーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="7c639-137">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="7c639-138">ReplaceSymbolStore メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-138">ReplaceSymbolStore Method</span></span>](isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="7c639-139">既存のシンボル ストアをデルタ シンボル ストアで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7c639-139">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="7c639-140">UpdateSymbolStore メソッド</span><span class="sxs-lookup"><span data-stu-id="7c639-140">UpdateSymbolStore Method</span></span>](isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="7c639-141">既存のシンボル ストアをデルタ シンボル ストアで更新します。</span><span class="sxs-lookup"><span data-stu-id="7c639-141">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c639-142">要件</span><span class="sxs-lookup"><span data-stu-id="7c639-142">Requirements</span></span>  

 <span data-ttu-id="7c639-143">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="7c639-143">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c639-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c639-144">See also</span></span>

- [<span data-ttu-id="7c639-145">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c639-145">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="7c639-146">ISymUnmanagedReader2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c639-146">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)

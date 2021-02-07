---
description: 詳細については、「ISymUnmanagedDocument インターフェイス」を参照してください。
title: ISymUnmanagedDocument インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
ms.openlocfilehash: cd1907e570dd15ebcac3ee12aa09c626c9bb7787
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710141"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="312e4-103">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="312e4-103">ISymUnmanagedDocument Interface</span></span>

<span data-ttu-id="312e4-104">シンボル ストアによって参照されるドキュメントを表します。</span><span class="sxs-lookup"><span data-stu-id="312e4-104">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="312e4-105">ドキュメントは、URL (uniform resource locator) とドキュメントの種類の GUID によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="312e4-105">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="312e4-106">URL とドキュメントの種類の GUID を使用して、ドキュメントがどのように格納されているかに関係なく、ドキュメントを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="312e4-106">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="312e4-107">ドキュメントソースをシンボルストアに格納し、このインターフェイスを使用して取得することができます。</span><span class="sxs-lookup"><span data-stu-id="312e4-107">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="312e4-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="312e4-108">Methods</span></span>  
  
|<span data-ttu-id="312e4-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="312e4-109">Method</span></span>|<span data-ttu-id="312e4-110">説明</span><span class="sxs-lookup"><span data-stu-id="312e4-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="312e4-111">FindClosestLine メソッド</span><span class="sxs-lookup"><span data-stu-id="312e4-111">FindClosestLine Method</span></span>](isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="312e4-112">このドキュメント内の行が指定されている場合は、シーケンスポイントで最も近い行を返します。</span><span class="sxs-lookup"><span data-stu-id="312e4-112">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="312e4-113">GetCheckSum メソッド</span><span class="sxs-lookup"><span data-stu-id="312e4-113">GetCheckSum Method</span></span>](isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="312e4-114">チェックサムを取得します。</span><span class="sxs-lookup"><span data-stu-id="312e4-114">Gets the checksum.</span></span>|  
|[<span data-ttu-id="312e4-115">GetCheckSumAlgorithmId メソッド</span><span class="sxs-lookup"><span data-stu-id="312e4-115">GetCheckSumAlgorithmId Method</span></span>](isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="312e4-116">チェックサムアルゴリズム識別子を取得します。チェックサムがない場合は、すべての0の GUID を返します。</span><span class="sxs-lookup"><span data-stu-id="312e4-116">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="312e4-117">GetDocumentType メソッド</span><span class="sxs-lookup"><span data-stu-id="312e4-117">GetDocumentType Method</span></span>](isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="312e4-118">このドキュメントのドキュメントの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="312e4-118">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="312e4-119">GetLanguage メソッド</span><span class="sxs-lookup"><span data-stu-id="312e4-119">GetLanguage Method</span></span>](isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="312e4-120">このドキュメントの言語識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="312e4-120">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="312e4-121">GetLanguageVendor メソッド</span><span class="sxs-lookup"><span data-stu-id="312e4-121">GetLanguageVendor Method</span></span>](isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="312e4-122">このドキュメントの言語販売元を取得します。</span><span class="sxs-lookup"><span data-stu-id="312e4-122">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="312e4-123">GetSourceLength メソッド</span><span class="sxs-lookup"><span data-stu-id="312e4-123">GetSourceLength Method</span></span>](isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="312e4-124">埋め込まれたソースの長さをバイト数で取得します。</span><span class="sxs-lookup"><span data-stu-id="312e4-124">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="312e4-125">GetSourceRange メソッド</span><span class="sxs-lookup"><span data-stu-id="312e4-125">GetSourceRange Method</span></span>](isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="312e4-126">指定されたバッファーに、埋め込みソースの指定された範囲を返します。</span><span class="sxs-lookup"><span data-stu-id="312e4-126">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="312e4-127">GetURL メソッド</span><span class="sxs-lookup"><span data-stu-id="312e4-127">GetURL Method</span></span>](isymunmanageddocument-geturl-method.md)|<span data-ttu-id="312e4-128">このドキュメントの URL を返します。</span><span class="sxs-lookup"><span data-stu-id="312e4-128">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="312e4-129">HasEmbeddedSource メソッド</span><span class="sxs-lookup"><span data-stu-id="312e4-129">HasEmbeddedSource Method</span></span>](isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="312e4-130">`true`ドキュメントがデバッグシンボルに埋め込まれている場合はを返します。それ以外の場合はを返し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="312e4-130">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="312e4-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="312e4-131">See also</span></span>

- [<span data-ttu-id="312e4-132">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="312e4-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)

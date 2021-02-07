---
description: '詳細については、次を参照してください: ISymUnmanagedWriter:: Setmethod Ourcer メソッド'
title: ISymUnmanagedWriter::SetMethodSourceRange メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
ms.openlocfilehash: 2e2f0f664d8be30a8c3628100fafb3740d34f54f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762072"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="f40c6-103">ISymUnmanagedWriter::SetMethodSourceRange メソッド</span><span class="sxs-lookup"><span data-stu-id="f40c6-103">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>

<span data-ttu-id="f40c6-104">ソース ファイル内にメソッドの実際の先頭と末尾を指定します。</span><span class="sxs-lookup"><span data-stu-id="f40c6-104">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="f40c6-105">メソッドの範囲を、メソッド内に存在するシーケンスポイントとは別に指定するには、このメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f40c6-105">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f40c6-106">構文</span><span class="sxs-lookup"><span data-stu-id="f40c6-106">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f40c6-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f40c6-107">Parameters</span></span>  

 `startDoc`  
 <span data-ttu-id="f40c6-108">から開始位置を格納しているドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f40c6-108">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="f40c6-109">から開始行番号。</span><span class="sxs-lookup"><span data-stu-id="f40c6-109">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="f40c6-110">から開始列。</span><span class="sxs-lookup"><span data-stu-id="f40c6-110">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="f40c6-111">から終了位置を含むドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f40c6-111">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="f40c6-112">から終了行番号。</span><span class="sxs-lookup"><span data-stu-id="f40c6-112">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="f40c6-113">から終了列番号。</span><span class="sxs-lookup"><span data-stu-id="f40c6-113">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f40c6-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="f40c6-114">Return Value</span></span>  

 <span data-ttu-id="f40c6-115">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="f40c6-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f40c6-116">要件</span><span class="sxs-lookup"><span data-stu-id="f40c6-116">Requirements</span></span>  

 <span data-ttu-id="f40c6-117">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="f40c6-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f40c6-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f40c6-118">See also</span></span>

- [<span data-ttu-id="f40c6-119">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f40c6-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)

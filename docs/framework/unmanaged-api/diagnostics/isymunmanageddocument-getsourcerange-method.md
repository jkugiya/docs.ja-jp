---
description: '詳細について: ISymUnmanagedDocument:: GetSourceRange メソッド'
title: ISymUnmanagedDocument::GetSourceRange メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
ms.openlocfilehash: 98718298d7bf2f44d418a40f17ad19cdee0b6771
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790166"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="0a55a-103">ISymUnmanagedDocument::GetSourceRange メソッド</span><span class="sxs-lookup"><span data-stu-id="0a55a-103">ISymUnmanagedDocument::GetSourceRange Method</span></span>

<span data-ttu-id="0a55a-104">指定されたバッファーに、埋め込みソースの指定された範囲を返します。</span><span class="sxs-lookup"><span data-stu-id="0a55a-104">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="0a55a-105">バッファーは、ソースを保持するのに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a55a-105">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a55a-106">構文</span><span class="sxs-lookup"><span data-stu-id="0a55a-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a55a-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a55a-107">Parameters</span></span>  

 `startLine`  
 <span data-ttu-id="0a55a-108">から現在のドキュメントの開始行。</span><span class="sxs-lookup"><span data-stu-id="0a55a-108">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="0a55a-109">から現在のドキュメントの開始列。</span><span class="sxs-lookup"><span data-stu-id="0a55a-109">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="0a55a-110">から現在のドキュメントの最終行。</span><span class="sxs-lookup"><span data-stu-id="0a55a-110">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="0a55a-111">から現在のドキュメントの最後の列。</span><span class="sxs-lookup"><span data-stu-id="0a55a-111">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="0a55a-112">からソースのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="0a55a-112">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="0a55a-113">入出力ソースサイズを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a55a-113">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="0a55a-114">入出力ソースドキュメントの指定した範囲のサイズと長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="0a55a-114">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a55a-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a55a-115">Return Value</span></span>  

 <span data-ttu-id="0a55a-116">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="0a55a-116">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a55a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a55a-117">See also</span></span>

- [<span data-ttu-id="0a55a-118">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a55a-118">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)

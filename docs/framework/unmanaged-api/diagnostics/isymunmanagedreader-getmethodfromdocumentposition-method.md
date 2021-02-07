---
description: '詳細について: ISymUnmanagedReader:: GetMethodFromDocumentPosition メソッド'
title: ISymUnmanagedReader::GetMethodFromDocumentPosition メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type:
- apiref
ms.openlocfilehash: 1289b02f8ea8440dcd1b308b6c91a46a213cabb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764087"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="cd87c-103">ISymUnmanagedReader::GetMethodFromDocumentPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="cd87c-103">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>

<span data-ttu-id="cd87c-104">ドキュメント内の指定された位置にあるブレークポイントを含むメソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="cd87c-104">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd87c-105">構文</span><span class="sxs-lookup"><span data-stu-id="cd87c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd87c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd87c-106">Parameters</span></span>  

 `document`  
 <span data-ttu-id="cd87c-107">から指定されたドキュメント。</span><span class="sxs-lookup"><span data-stu-id="cd87c-107">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="cd87c-108">から指定したドキュメントの行。</span><span class="sxs-lookup"><span data-stu-id="cd87c-108">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="cd87c-109">から指定されたドキュメントの列。</span><span class="sxs-lookup"><span data-stu-id="cd87c-109">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="cd87c-110">入出力ブレークポイントを含むメソッドを表す [ISymUnmanagedMethod Interface](isymunmanagedmethod-interface.md) オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cd87c-110">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd87c-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="cd87c-111">Return Value</span></span>  

 <span data-ttu-id="cd87c-112">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd87c-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd87c-113">要件</span><span class="sxs-lookup"><span data-stu-id="cd87c-113">Requirements</span></span>  

 <span data-ttu-id="cd87c-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="cd87c-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd87c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd87c-115">See also</span></span>

- [<span data-ttu-id="cd87c-116">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd87c-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

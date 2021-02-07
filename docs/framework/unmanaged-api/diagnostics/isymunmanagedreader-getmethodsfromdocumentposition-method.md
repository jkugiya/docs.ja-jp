---
description: '詳細については、次を参照してください: ISymUnmanagedReader:: Getmethod Fromdocumentposition メソッド'
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
ms.openlocfilehash: 033bdce2cd70e578ebd3be8a187d983a2c58b99d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764035"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="55a1c-103">ISymUnmanagedReader::GetMethodsFromDocumentPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="55a1c-103">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>

<span data-ttu-id="55a1c-104">メソッドの配列を返します。各メソッドには、ドキュメント内の指定された位置にあるブレークポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55a1c-104">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55a1c-105">構文</span><span class="sxs-lookup"><span data-stu-id="55a1c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55a1c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="55a1c-106">Parameters</span></span>  

 `document`  
 <span data-ttu-id="55a1c-107">から指定されたドキュメント。</span><span class="sxs-lookup"><span data-stu-id="55a1c-107">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="55a1c-108">から指定したドキュメントの行。</span><span class="sxs-lookup"><span data-stu-id="55a1c-108">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="55a1c-109">から指定されたドキュメントの列。</span><span class="sxs-lookup"><span data-stu-id="55a1c-109">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="55a1c-110">[in] `pRetVal` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="55a1c-110">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="55a1c-111">入出力配列で返された要素の数を受け取る変数へのポインター `pRetVal` 。</span><span class="sxs-lookup"><span data-stu-id="55a1c-111">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="55a1c-112">入出力ポインターの配列。各ポインターは、ブレークポイントを含むメソッドを表す [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="55a1c-112">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55a1c-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="55a1c-113">Return Value</span></span>  

 <span data-ttu-id="55a1c-114">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="55a1c-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55a1c-115">要件</span><span class="sxs-lookup"><span data-stu-id="55a1c-115">Requirements</span></span>  

 <span data-ttu-id="55a1c-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="55a1c-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a1c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="55a1c-117">See also</span></span>

- [<span data-ttu-id="55a1c-118">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55a1c-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

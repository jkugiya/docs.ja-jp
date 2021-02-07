---
description: '詳細について: ISymUnmanagedReader:: GetGlobalVariables メソッド'
title: ISymUnmanagedReader::GetGlobalVariables メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
ms.openlocfilehash: 2b017d2a5746942f701cf79d3d29f1eb571dceab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689652"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="d7877-103">ISymUnmanagedReader::GetGlobalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="d7877-103">ISymUnmanagedReader::GetGlobalVariables Method</span></span>

<span data-ttu-id="d7877-104">すべてのグローバル変数を返します。</span><span class="sxs-lookup"><span data-stu-id="d7877-104">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7877-105">構文</span><span class="sxs-lookup"><span data-stu-id="d7877-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7877-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d7877-106">Parameters</span></span>  

 `cVars`  
 <span data-ttu-id="d7877-107">からが指すバッファーの長さ `pcVars` 。</span><span class="sxs-lookup"><span data-stu-id="d7877-107">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="d7877-108">入出力 `ULONG32` 変数を格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d7877-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="d7877-109">入出力変数を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="d7877-109">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7877-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="d7877-110">Return Value</span></span>  

 <span data-ttu-id="d7877-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d7877-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7877-112">要件</span><span class="sxs-lookup"><span data-stu-id="d7877-112">Requirements</span></span>  

 <span data-ttu-id="d7877-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="d7877-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7877-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7877-114">See also</span></span>

- [<span data-ttu-id="d7877-115">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7877-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

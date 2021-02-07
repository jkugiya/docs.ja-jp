---
description: '詳細情報: ISymUnmanagedReader:: GetVariables メソッド'
title: ISymUnmanagedReader::GetVariables メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
ms.openlocfilehash: 93208e6c5c65c4c770c533b7ea72de513451d97d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763905"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="978d8-103">ISymUnmanagedReader::GetVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="978d8-103">ISymUnmanagedReader::GetVariables Method</span></span>

<span data-ttu-id="978d8-104">親と名前を指定して、ローカルでない変数を返します。</span><span class="sxs-lookup"><span data-stu-id="978d8-104">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="978d8-105">構文</span><span class="sxs-lookup"><span data-stu-id="978d8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="978d8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="978d8-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="978d8-107">から変数の親。</span><span class="sxs-lookup"><span data-stu-id="978d8-107">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="978d8-108">[in] `pVars` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="978d8-108">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="978d8-109">入出力で返された変数の数を受け取る変数へのポインター `pVars` 。</span><span class="sxs-lookup"><span data-stu-id="978d8-109">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="978d8-110">入出力変数を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="978d8-110">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="978d8-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="978d8-111">Return Value</span></span>  

 <span data-ttu-id="978d8-112">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="978d8-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="978d8-113">要件</span><span class="sxs-lookup"><span data-stu-id="978d8-113">Requirements</span></span>  

 <span data-ttu-id="978d8-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="978d8-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="978d8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="978d8-115">See also</span></span>

- [<span data-ttu-id="978d8-116">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="978d8-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

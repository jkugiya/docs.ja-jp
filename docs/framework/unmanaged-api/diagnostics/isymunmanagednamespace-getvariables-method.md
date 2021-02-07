---
description: '詳細情報: ISymUnmanagedNamespace:: GetVariables メソッド'
title: ISymUnmanagedNamespace::GetVariables メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
ms.openlocfilehash: 63316bf3ba1e4736d542be3362076c3ae6e95def
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721204"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="fce18-103">ISymUnmanagedNamespace::GetVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="fce18-103">ISymUnmanagedNamespace::GetVariables Method</span></span>

<span data-ttu-id="fce18-104">この名前空間内のグローバルスコープで定義されているすべての変数を返します。</span><span class="sxs-lookup"><span data-stu-id="fce18-104">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fce18-105">構文</span><span class="sxs-lookup"><span data-stu-id="fce18-105">Syntax</span></span>  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fce18-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fce18-106">Parameters</span></span>  

 `cVars`  
 <span data-ttu-id="fce18-107">から `ULONG32` 配列のサイズを示す `pVars` 。</span><span class="sxs-lookup"><span data-stu-id="fce18-107">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="fce18-108">入出力 `ULONG32` 名前空間を格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fce18-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="fce18-109">入出力名前空間を格納しているバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fce18-109">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fce18-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="fce18-110">Return Value</span></span>  

 <span data-ttu-id="fce18-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="fce18-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fce18-112">要件</span><span class="sxs-lookup"><span data-stu-id="fce18-112">Requirements</span></span>  

 <span data-ttu-id="fce18-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="fce18-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce18-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="fce18-114">See also</span></span>

- [<span data-ttu-id="fce18-115">ISymUnmanagedNamespace インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fce18-115">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)

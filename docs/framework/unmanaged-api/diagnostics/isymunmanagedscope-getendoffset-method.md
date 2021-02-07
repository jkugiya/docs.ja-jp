---
description: '詳細について: ISymUnmanagedScope:: GetEndOffset メソッド'
title: ISymUnmanagedScope::GetEndOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
ms.openlocfilehash: ac95b98bb87fbf3dc3b42b5a2e5413f76dfffa34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763477"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="04444-103">ISymUnmanagedScope::GetEndOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="04444-103">ISymUnmanagedScope::GetEndOffset Method</span></span>

<span data-ttu-id="04444-104">このスコープの終了オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="04444-104">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04444-105">構文</span><span class="sxs-lookup"><span data-stu-id="04444-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04444-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="04444-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="04444-107">入出力終了オフセットを受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="04444-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04444-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="04444-108">Return Value</span></span>  

 <span data-ttu-id="04444-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="04444-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04444-110">要件</span><span class="sxs-lookup"><span data-stu-id="04444-110">Requirements</span></span>  

 <span data-ttu-id="04444-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="04444-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04444-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="04444-112">See also</span></span>

- [<span data-ttu-id="04444-113">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="04444-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="04444-114">GetStartOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="04444-114">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)

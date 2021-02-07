---
description: '詳細について: ISymUnmanagedReader:: GetUserEntryPoint メソッド'
title: ISymUnmanagedReader::GetUserEntryPoint メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type:
- apiref
ms.openlocfilehash: b8696a339fc8aefca2b1a1f9b960ba94ce565d8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763918"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="57af7-103">ISymUnmanagedReader::GetUserEntryPoint メソッド</span><span class="sxs-lookup"><span data-stu-id="57af7-103">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>

<span data-ttu-id="57af7-104">モジュールのユーザーエントリポイントとして指定されたメソッド (存在する場合) を返します。</span><span class="sxs-lookup"><span data-stu-id="57af7-104">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="57af7-105">たとえば、このメソッドは、main メソッドの前にコンパイラで生成されたスタブではなく、ユーザーのメインメソッドである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="57af7-105">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57af7-106">構文</span><span class="sxs-lookup"><span data-stu-id="57af7-106">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57af7-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="57af7-107">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="57af7-108">入出力エントリポイントを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="57af7-108">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57af7-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="57af7-109">Return Value</span></span>  

 <span data-ttu-id="57af7-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="57af7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57af7-111">要件</span><span class="sxs-lookup"><span data-stu-id="57af7-111">Requirements</span></span>  

 <span data-ttu-id="57af7-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="57af7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57af7-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="57af7-113">See also</span></span>

- [<span data-ttu-id="57af7-114">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="57af7-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

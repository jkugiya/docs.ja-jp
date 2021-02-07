---
description: '詳細について: ISymUnmanagedNamespace:: GetNamespaces メソッド'
title: ISymUnmanagedNamespace::GetNamespaces メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
ms.openlocfilehash: f17b16e2a3a7001d16c86dd6dc95241c1b0785e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709907"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="ea2ca-103">ISymUnmanagedNamespace::GetNamespaces メソッド</span><span class="sxs-lookup"><span data-stu-id="ea2ca-103">ISymUnmanagedNamespace::GetNamespaces Method</span></span>

<span data-ttu-id="ea2ca-104">この名前空間の子を取得します。</span><span class="sxs-lookup"><span data-stu-id="ea2ca-104">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea2ca-105">構文</span><span class="sxs-lookup"><span data-stu-id="ea2ca-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea2ca-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea2ca-106">Parameters</span></span>  

 `cNameSpaces`  
 <span data-ttu-id="ea2ca-107">から `ULONG32` 配列のサイズを示す `namespaces` 。</span><span class="sxs-lookup"><span data-stu-id="ea2ca-107">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="ea2ca-108">入出力 `ULONG32` 名前空間を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ea2ca-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="ea2ca-109">入出力名前空間を格納しているバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ea2ca-109">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea2ca-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="ea2ca-110">Return Value</span></span>  

 <span data-ttu-id="ea2ca-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="ea2ca-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea2ca-112">要件</span><span class="sxs-lookup"><span data-stu-id="ea2ca-112">Requirements</span></span>  

 <span data-ttu-id="ea2ca-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="ea2ca-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2ca-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea2ca-114">See also</span></span>

- [<span data-ttu-id="ea2ca-115">ISymUnmanagedNamespace インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea2ca-115">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)

---
description: '詳細について: ISymUnmanagedReader:: GetNamespaces メソッド'
title: ISymUnmanagedReader::GetNamespaces メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
ms.openlocfilehash: 47f7bff829ca2a52eb95d7d7693a7486301de092
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764009"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="f71a7-103">ISymUnmanagedReader::GetNamespaces メソッド</span><span class="sxs-lookup"><span data-stu-id="f71a7-103">ISymUnmanagedReader::GetNamespaces Method</span></span>

<span data-ttu-id="f71a7-104">このシンボルストア内のグローバルスコープで定義されている名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="f71a7-104">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f71a7-105">構文</span><span class="sxs-lookup"><span data-stu-id="f71a7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f71a7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f71a7-106">Parameters</span></span>  

 `cNameSpaces`  
 <span data-ttu-id="f71a7-107">から名前空間配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="f71a7-107">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="f71a7-108">入出力名前空間リストの長さを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f71a7-108">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="f71a7-109">入出力名前空間リストを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f71a7-109">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f71a7-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="f71a7-110">Return Value</span></span>  

 <span data-ttu-id="f71a7-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="f71a7-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f71a7-112">要件</span><span class="sxs-lookup"><span data-stu-id="f71a7-112">Requirements</span></span>  

 <span data-ttu-id="f71a7-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="f71a7-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f71a7-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f71a7-114">See also</span></span>

- [<span data-ttu-id="f71a7-115">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f71a7-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

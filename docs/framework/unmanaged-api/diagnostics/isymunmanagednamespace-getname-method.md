---
description: '詳細情報: ISymUnmanagedNamespace:: GetName メソッド'
title: ISymUnmanagedNamespace::GetName メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
ms.openlocfilehash: f4d366363cd089995f98039389f59077e949fb79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721217"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="d01a0-103">ISymUnmanagedNamespace::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="d01a0-103">ISymUnmanagedNamespace::GetName Method</span></span>

<span data-ttu-id="d01a0-104">この名前空間の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="d01a0-104">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d01a0-105">構文</span><span class="sxs-lookup"><span data-stu-id="d01a0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d01a0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d01a0-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="d01a0-107">から `ULONG32` バッファーのサイズを示す `szName` 。</span><span class="sxs-lookup"><span data-stu-id="d01a0-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d01a0-108">入出力 `ULONG32` Null 終了を含む、名前空間の名前を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d01a0-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="d01a0-109">入出力名前空間の名前を格納しているバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d01a0-109">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d01a0-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="d01a0-110">Return Value</span></span>  

 <span data-ttu-id="d01a0-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d01a0-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d01a0-112">要件</span><span class="sxs-lookup"><span data-stu-id="d01a0-112">Requirements</span></span>  

 <span data-ttu-id="d01a0-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="d01a0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d01a0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d01a0-114">See also</span></span>

- [<span data-ttu-id="d01a0-115">ISymUnmanagedNamespace インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d01a0-115">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)

---
description: '詳細について: ISymUnmanagedMethod:: GetSequencePointCount メソッド'
title: ISymUnmanagedMethod::GetSequencePointCount メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
ms.openlocfilehash: 6e0341ddc151454de8764a47a92556ab1925bfa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710005"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="b2add-103">ISymUnmanagedMethod::GetSequencePointCount メソッド</span><span class="sxs-lookup"><span data-stu-id="b2add-103">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>

<span data-ttu-id="b2add-104">このメソッド内のシーケンスポイントの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="b2add-104">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2add-105">構文</span><span class="sxs-lookup"><span data-stu-id="b2add-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2add-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b2add-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="b2add-107">入出力 `ULONG32` シーケンスポイントを格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b2add-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2add-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="b2add-108">Return Value</span></span>  

 <span data-ttu-id="b2add-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b2add-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2add-110">要件</span><span class="sxs-lookup"><span data-stu-id="b2add-110">Requirements</span></span>  

 <span data-ttu-id="b2add-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="b2add-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2add-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2add-112">See also</span></span>

- [<span data-ttu-id="b2add-113">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2add-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)

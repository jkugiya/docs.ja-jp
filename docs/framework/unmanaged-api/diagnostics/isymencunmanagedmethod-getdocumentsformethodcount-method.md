---
description: '詳細について: ISymENCUnmanagedMethod:: GetDocumentsForMethodCount メソッド'
title: ISymENCUnmanagedMethod::GetDocumentsForMethodCount メソッド
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type:
- apiref
ms.openlocfilehash: 0594771c544ad1de32531e92f30fe96f245b5699
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738014"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="71434-103">ISymENCUnmanagedMethod::GetDocumentsForMethodCount メソッド</span><span class="sxs-lookup"><span data-stu-id="71434-103">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>

<span data-ttu-id="71434-104">このメソッドに行があるドキュメントの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="71434-104">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71434-105">構文</span><span class="sxs-lookup"><span data-stu-id="71434-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71434-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71434-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="71434-107">入出力 `ULONG32` ドキュメントを格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="71434-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71434-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="71434-108">Return Value</span></span>  

 <span data-ttu-id="71434-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="71434-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71434-110">要件</span><span class="sxs-lookup"><span data-stu-id="71434-110">Requirements</span></span>  

 <span data-ttu-id="71434-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="71434-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71434-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="71434-112">See also</span></span>

- [<span data-ttu-id="71434-113">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71434-113">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)

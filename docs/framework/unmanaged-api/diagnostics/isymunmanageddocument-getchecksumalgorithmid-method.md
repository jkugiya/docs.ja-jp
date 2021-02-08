---
description: '詳細について: ISymUnmanagedDocument:: GetCheckSumAlgorithmId メソッド'
title: ISymUnmanagedDocument::GetCheckSumAlgorithmId メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
ms.openlocfilehash: 835f56875a1adc3a3b6617a5a0b280f60f918236
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772121"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="55c7b-103">ISymUnmanagedDocument::GetCheckSumAlgorithmId メソッド</span><span class="sxs-lookup"><span data-stu-id="55c7b-103">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>

<span data-ttu-id="55c7b-104">チェックサムアルゴリズム識別子を取得します。チェックサムがない場合は、すべての0の GUID を返します。</span><span class="sxs-lookup"><span data-stu-id="55c7b-104">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55c7b-105">構文</span><span class="sxs-lookup"><span data-stu-id="55c7b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55c7b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="55c7b-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="55c7b-107">入出力チェックサムアルゴリズム識別子を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="55c7b-107">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55c7b-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="55c7b-108">Return Value</span></span>  

 <span data-ttu-id="55c7b-109">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="55c7b-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c7b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="55c7b-110">See also</span></span>

- [<span data-ttu-id="55c7b-111">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55c7b-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)

---
description: '詳細について: ISymUnmanagedDocument:: GetLanguage メソッド'
title: ISymUnmanagedDocument::GetLanguage メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
ms.openlocfilehash: f30636303d310ed91aa4229f52a3197a29190d3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710310"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="94caa-103">ISymUnmanagedDocument::GetLanguage メソッド</span><span class="sxs-lookup"><span data-stu-id="94caa-103">ISymUnmanagedDocument::GetLanguage Method</span></span>

<span data-ttu-id="94caa-104">このドキュメントの言語識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="94caa-104">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94caa-105">構文</span><span class="sxs-lookup"><span data-stu-id="94caa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94caa-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="94caa-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="94caa-107">入出力言語識別子を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="94caa-107">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94caa-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="94caa-108">Return Value</span></span>  

 <span data-ttu-id="94caa-109">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="94caa-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94caa-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="94caa-110">See also</span></span>

- [<span data-ttu-id="94caa-111">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94caa-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)

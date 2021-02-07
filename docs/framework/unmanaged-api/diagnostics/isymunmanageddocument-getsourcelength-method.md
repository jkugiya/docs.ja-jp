---
description: '詳細について: ISymUnmanagedDocument:: GetSourceLength メソッド'
title: ISymUnmanagedDocument::GetSourceLength メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
ms.openlocfilehash: 91ac1327afc84458c87122dddc31d0f5b2186f10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721516"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="1af5a-103">ISymUnmanagedDocument::GetSourceLength メソッド</span><span class="sxs-lookup"><span data-stu-id="1af5a-103">ISymUnmanagedDocument::GetSourceLength Method</span></span>

<span data-ttu-id="1af5a-104">埋め込まれたソースの長さをバイト数で取得します。</span><span class="sxs-lookup"><span data-stu-id="1af5a-104">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1af5a-105">構文</span><span class="sxs-lookup"><span data-stu-id="1af5a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1af5a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1af5a-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="1af5a-107">入出力埋め込まれたソースの長さ (バイト単位) を示す変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1af5a-107">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1af5a-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="1af5a-108">Return Value</span></span>  

 <span data-ttu-id="1af5a-109">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="1af5a-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af5a-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="1af5a-110">See also</span></span>

- [<span data-ttu-id="1af5a-111">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1af5a-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)

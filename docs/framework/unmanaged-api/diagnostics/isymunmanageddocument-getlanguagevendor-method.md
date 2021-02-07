---
description: '詳細について: ISymUnmanagedDocument:: GetLanguageVendor メソッド'
title: ISymUnmanagedDocument::GetLanguageVendor メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguageVendor
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type:
- apiref
ms.openlocfilehash: 247c6c24f57211b3b46ad773d8e77d7e0f16fd01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710245"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="dd72e-103">ISymUnmanagedDocument::GetLanguageVendor メソッド</span><span class="sxs-lookup"><span data-stu-id="dd72e-103">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>

<span data-ttu-id="dd72e-104">このドキュメントの言語販売元を取得します。</span><span class="sxs-lookup"><span data-stu-id="dd72e-104">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd72e-105">構文</span><span class="sxs-lookup"><span data-stu-id="dd72e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd72e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd72e-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="dd72e-107">入出力言語ベンダーを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="dd72e-107">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd72e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="dd72e-108">Return Value</span></span>  

 <span data-ttu-id="dd72e-109">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="dd72e-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd72e-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd72e-110">See also</span></span>

- [<span data-ttu-id="dd72e-111">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd72e-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)

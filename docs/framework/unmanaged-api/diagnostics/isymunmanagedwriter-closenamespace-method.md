---
description: '詳細について: ISymUnmanagedWriter:: CloseNamespace メソッド'
title: ISymUnmanagedWriter::CloseNamespace メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type:
- apiref
ms.openlocfilehash: c552d8bc86ab2bbd93918fdd6be3f880b3d83178
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762566"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="924fb-103">ISymUnmanagedWriter::CloseNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="924fb-103">ISymUnmanagedWriter::CloseNamespace Method</span></span>

<span data-ttu-id="924fb-104">最近開いた名前空間を閉じます。</span><span class="sxs-lookup"><span data-stu-id="924fb-104">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="924fb-105">構文</span><span class="sxs-lookup"><span data-stu-id="924fb-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="924fb-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="924fb-106">Return Value</span></span>  

 <span data-ttu-id="924fb-107">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="924fb-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="924fb-108">要件</span><span class="sxs-lookup"><span data-stu-id="924fb-108">Requirements</span></span>  

 <span data-ttu-id="924fb-109">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="924fb-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="924fb-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="924fb-110">See also</span></span>

- [<span data-ttu-id="924fb-111">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="924fb-111">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="924fb-112">OpenNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="924fb-112">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)

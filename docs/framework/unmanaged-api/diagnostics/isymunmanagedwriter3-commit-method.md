---
description: '詳細情報: ISymUnmanagedWriter3:: Commit メソッド'
title: ISymUnmanagedWriter3::Commit メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
ms.openlocfilehash: 308f5d3a16cf60a0e77a581a318d6fd6c398b3f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761760"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="e8d31-103">ISymUnmanagedWriter3::Commit メソッド</span><span class="sxs-lookup"><span data-stu-id="e8d31-103">ISymUnmanagedWriter3::Commit Method</span></span>

<span data-ttu-id="e8d31-104">これまでに書き込まれた変更をストリームにコミットします。</span><span class="sxs-lookup"><span data-stu-id="e8d31-104">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8d31-105">構文</span><span class="sxs-lookup"><span data-stu-id="e8d31-105">Syntax</span></span>  
  
```cpp  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e8d31-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="e8d31-106">Return Value</span></span>  

 <span data-ttu-id="e8d31-107">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8d31-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8d31-108">要件</span><span class="sxs-lookup"><span data-stu-id="e8d31-108">Requirements</span></span>  

 <span data-ttu-id="e8d31-109">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="e8d31-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d31-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8d31-110">See also</span></span>

- [<span data-ttu-id="e8d31-111">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8d31-111">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)

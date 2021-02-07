---
description: '詳細情報: ISymUnmanagedWriter:: CloseMethod メソッド'
title: ISymUnmanagedWriter::CloseMethod メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
ms.openlocfilehash: 8d19de0827f94d52c92852b0d1f2b5567e109c15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762579"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="fa933-103">ISymUnmanagedWriter::CloseMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="fa933-103">ISymUnmanagedWriter::CloseMethod Method</span></span>

<span data-ttu-id="fa933-104">現在のメソッドを閉じます。</span><span class="sxs-lookup"><span data-stu-id="fa933-104">Closes the current method.</span></span> <span data-ttu-id="fa933-105">メソッドを閉じると、それ以上シンボルを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="fa933-105">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa933-106">構文</span><span class="sxs-lookup"><span data-stu-id="fa933-106">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fa933-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="fa933-107">Return Value</span></span>  

 <span data-ttu-id="fa933-108">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="fa933-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa933-109">要件</span><span class="sxs-lookup"><span data-stu-id="fa933-109">Requirements</span></span>  

 <span data-ttu-id="fa933-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="fa933-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa933-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa933-111">See also</span></span>

- [<span data-ttu-id="fa933-112">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fa933-112">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="fa933-113">OpenMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="fa933-113">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)

---
description: '詳細について: ISymUnmanagedWriter:: Abort メソッド'
title: ISymUnmanagedWriter::Abort メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
ms.openlocfilehash: 312694bf2b667ea78bf5ddc993d0e2b71c85a8ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762683"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="38781-103">ISymUnmanagedWriter::Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="38781-103">ISymUnmanagedWriter::Abort Method</span></span>

<span data-ttu-id="38781-104">シンボルストアにシンボルをコミットせずにシンボルライターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="38781-104">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="38781-105">この呼び出しの後、シンボルライターは、さらに更新するために無効になります。</span><span class="sxs-lookup"><span data-stu-id="38781-105">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="38781-106">シンボルをコミットし、シンボルライターを閉じるには、代わりに [ISymUnmanagedWriter:: close](isymunmanagedwriter-close-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="38781-106">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38781-107">構文</span><span class="sxs-lookup"><span data-stu-id="38781-107">Syntax</span></span>  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="38781-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="38781-108">Return Value</span></span>  

 <span data-ttu-id="38781-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="38781-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38781-110">要件</span><span class="sxs-lookup"><span data-stu-id="38781-110">Requirements</span></span>  

 <span data-ttu-id="38781-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="38781-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38781-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="38781-112">See also</span></span>

- [<span data-ttu-id="38781-113">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38781-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)

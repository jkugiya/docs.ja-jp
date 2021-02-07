---
description: '詳細情報: ISymUnmanagedWriter:: Close メソッド'
title: ISymUnmanagedWriter::Close メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
ms.openlocfilehash: 02f4d8d4a232240160ad5065947282f40af42f4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762631"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="67584-103">ISymUnmanagedWriter::Close メソッド</span><span class="sxs-lookup"><span data-stu-id="67584-103">ISymUnmanagedWriter::Close Method</span></span>

<span data-ttu-id="67584-104">シンボルをシンボルストアにコミットした後、シンボルライターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="67584-104">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67584-105">構文</span><span class="sxs-lookup"><span data-stu-id="67584-105">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="67584-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="67584-106">Return Value</span></span>  

 <span data-ttu-id="67584-107">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="67584-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67584-108">解説</span><span class="sxs-lookup"><span data-stu-id="67584-108">Remarks</span></span>  

 <span data-ttu-id="67584-109">この呼び出しの後、シンボルライターは、さらに更新するために無効になります。</span><span class="sxs-lookup"><span data-stu-id="67584-109">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="67584-110">シンボルをコミットせずにシンボルライターを閉じるには、代わりに [ISymUnmanagedWriter:: Abort](isymunmanagedwriter-abort-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="67584-110">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67584-111">要件</span><span class="sxs-lookup"><span data-stu-id="67584-111">Requirements</span></span>  

 <span data-ttu-id="67584-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="67584-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67584-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="67584-113">See also</span></span>

- [<span data-ttu-id="67584-114">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="67584-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)

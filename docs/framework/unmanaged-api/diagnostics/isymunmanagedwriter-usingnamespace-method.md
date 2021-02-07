---
description: '詳細について: ISymUnmanagedWriter:: 名前空間メソッドを参照してください。'
title: ISymUnmanagedWriter::UsingNamespace メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
ms.openlocfilehash: e7d56cded125aac6154d4315c587f58f946a9a82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761955"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="7a2f6-103">ISymUnmanagedWriter::UsingNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="7a2f6-103">ISymUnmanagedWriter::UsingNamespace Method</span></span>

<span data-ttu-id="7a2f6-104">現在開いている構文のスコープ内で、指定された完全修飾名前空間名が使用されていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a2f6-104">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="7a2f6-105">名前空間は、現在開いているスコープから継承されるすべてのスコープ内で使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a2f6-105">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="7a2f6-106">現在のスコープを終了すると、名前空間も使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="7a2f6-106">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a2f6-107">構文</span><span class="sxs-lookup"><span data-stu-id="7a2f6-107">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a2f6-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a2f6-108">Parameters</span></span>  

 `fullName`  
 <span data-ttu-id="7a2f6-109">から名前空間の完全修飾名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7a2f6-109">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a2f6-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="7a2f6-110">Return Value</span></span>  

 <span data-ttu-id="7a2f6-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a2f6-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a2f6-112">要件</span><span class="sxs-lookup"><span data-stu-id="7a2f6-112">Requirements</span></span>  

 <span data-ttu-id="7a2f6-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="7a2f6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a2f6-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a2f6-114">See also</span></span>

- [<span data-ttu-id="7a2f6-115">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a2f6-115">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)

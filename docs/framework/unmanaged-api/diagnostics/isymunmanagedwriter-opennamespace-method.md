---
description: '詳細について: ISymUnmanagedWriter:: OpenNamespace メソッド'
title: ISymUnmanagedWriter::OpenNamespace メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
ms.openlocfilehash: ab848e44dfda1f5caaa92bfd3376bdcbd67d8a9b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762124"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="a6129-103">ISymUnmanagedWriter::OpenNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="a6129-103">ISymUnmanagedWriter::OpenNamespace Method</span></span>

<span data-ttu-id="a6129-104">新しい名前空間を開きます。</span><span class="sxs-lookup"><span data-stu-id="a6129-104">Opens a new namespace.</span></span> <span data-ttu-id="a6129-105">名前空間を占有するメソッドまたは変数を定義する前に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a6129-105">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="a6129-106">名前空間は入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a6129-106">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6129-107">構文</span><span class="sxs-lookup"><span data-stu-id="a6129-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6129-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a6129-108">Parameters</span></span>  

 `name`  
 <span data-ttu-id="a6129-109">から新しい名前空間の名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a6129-109">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6129-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="a6129-110">Return Value</span></span>  

 <span data-ttu-id="a6129-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a6129-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6129-112">要件</span><span class="sxs-lookup"><span data-stu-id="a6129-112">Requirements</span></span>  

 <span data-ttu-id="a6129-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="a6129-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6129-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6129-114">See also</span></span>

- [<span data-ttu-id="a6129-115">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6129-115">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="a6129-116">CloseNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="a6129-116">CloseNamespace Method</span></span>](isymunmanagedwriter-closenamespace-method.md)

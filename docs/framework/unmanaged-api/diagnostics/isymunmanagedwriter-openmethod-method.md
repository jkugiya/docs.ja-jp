---
description: '詳細情報: ISymUnmanagedWriter:: OpenMethod メソッド'
title: ISymUnmanagedWriter::OpenMethod メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: 2cf7e6bf7c632449c25a2b49c7658fa7b1cc287e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762228"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="d79c8-103">ISymUnmanagedWriter::OpenMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="d79c8-103">ISymUnmanagedWriter::OpenMethod Method</span></span>

<span data-ttu-id="d79c8-104">シンボル情報を出力するメソッドを開きます。</span><span class="sxs-lookup"><span data-stu-id="d79c8-104">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="d79c8-105">指定されたメソッドは、シーケンスポイント、パラメーター、および構文のスコープを定義するための呼び出しの現在のメソッドになります。</span><span class="sxs-lookup"><span data-stu-id="d79c8-105">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="d79c8-106">メソッド全体を囲む構文の暗黙的なスコープがあります。</span><span class="sxs-lookup"><span data-stu-id="d79c8-106">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="d79c8-107">以前に閉じられたメソッドを再度開くと、そのメソッドに対して定義されていたシンボルはすべて消去されます。</span><span class="sxs-lookup"><span data-stu-id="d79c8-107">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="d79c8-108">開いているメソッドは一度に1つしか存在できません。</span><span class="sxs-lookup"><span data-stu-id="d79c8-108">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d79c8-109">構文</span><span class="sxs-lookup"><span data-stu-id="d79c8-109">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d79c8-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d79c8-110">Parameters</span></span>  

 `method`  
 <span data-ttu-id="d79c8-111">から開くメソッドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="d79c8-111">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d79c8-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="d79c8-112">Return Value</span></span>  

 <span data-ttu-id="d79c8-113">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d79c8-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d79c8-114">要件</span><span class="sxs-lookup"><span data-stu-id="d79c8-114">Requirements</span></span>  

 <span data-ttu-id="d79c8-115">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="d79c8-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d79c8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d79c8-116">See also</span></span>

- [<span data-ttu-id="d79c8-117">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d79c8-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="d79c8-118">CloseMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="d79c8-118">CloseMethod Method</span></span>](isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="d79c8-119">OpenMethod2 メソッド</span><span class="sxs-lookup"><span data-stu-id="d79c8-119">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)

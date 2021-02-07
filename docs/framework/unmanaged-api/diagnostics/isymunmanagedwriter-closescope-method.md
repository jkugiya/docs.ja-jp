---
description: '詳細について: ISymUnmanagedWriter:: Cloの対処方法'
title: ISymUnmanagedWriter::CloseScope メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
ms.openlocfilehash: bb41e69955632d1e4d86250a63a9f25a7d1ae807
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762553"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="2c43f-103">ISymUnmanagedWriter::CloseScope メソッド</span><span class="sxs-lookup"><span data-stu-id="2c43f-103">ISymUnmanagedWriter::CloseScope Method</span></span>

<span data-ttu-id="2c43f-104">現在の構文のスコープを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2c43f-104">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c43f-105">構文</span><span class="sxs-lookup"><span data-stu-id="2c43f-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c43f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2c43f-106">Parameters</span></span>  

 `endOffset`  
 <span data-ttu-id="2c43f-107">から構文のスコープの最後の命令の末尾にある点の、メソッドの先頭からのオフセット (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2c43f-107">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c43f-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="2c43f-108">Return Value</span></span>  

 <span data-ttu-id="2c43f-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c43f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c43f-110">解説</span><span class="sxs-lookup"><span data-stu-id="2c43f-110">Remarks</span></span>  

 <span data-ttu-id="2c43f-111">スコープを閉じた後は、それ以上の変数を定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="2c43f-111">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="2c43f-112">[ISymUnmanagedWriter:: OpenScope](isymunmanagedwriter-openscope-method.md) は、 [ISymUnmanagedWriter:: SetScopeRange](isymunmanagedwriter-setscoperange-method.md) と共に使用してスコープの開始オフセットと終了オフセットを後で定義できる、不透明なスコープ識別子を返します。</span><span class="sxs-lookup"><span data-stu-id="2c43f-112">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="2c43f-113">この場合、`ISymUnmanagedWriter::OpenScope` と `ISymUnmanagedWriter::CloseScope` に渡したオフセットは無視されます。</span><span class="sxs-lookup"><span data-stu-id="2c43f-113">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="2c43f-114">スコープ識別子は、現在のメソッドでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="2c43f-114">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c43f-115">要件</span><span class="sxs-lookup"><span data-stu-id="2c43f-115">Requirements</span></span>  

 <span data-ttu-id="2c43f-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="2c43f-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c43f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c43f-117">See also</span></span>

- [<span data-ttu-id="2c43f-118">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c43f-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)

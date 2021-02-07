---
description: '詳細について: ISymUnmanagedWriter:: OpenScope メソッド'
title: ISymUnmanagedWriter::OpenScope メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
ms.openlocfilehash: 1e47d97941b053fedcf08c7582e1083988a9fed4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762111"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="ce4e0-103">ISymUnmanagedWriter::OpenScope メソッド</span><span class="sxs-lookup"><span data-stu-id="ce4e0-103">ISymUnmanagedWriter::OpenScope Method</span></span>

<span data-ttu-id="ce4e0-104">現在のメソッドの構文の新しいスコープを開きます。</span><span class="sxs-lookup"><span data-stu-id="ce4e0-104">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="ce4e0-105">スコープは新しい現在のスコープになり、スコープのスタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="ce4e0-105">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="ce4e0-106">スコープは階層を形成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce4e0-106">Scopes must form a hierarchy.</span></span> <span data-ttu-id="ce4e0-107">兄弟を重ねることはできません。</span><span class="sxs-lookup"><span data-stu-id="ce4e0-107">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce4e0-108">構文</span><span class="sxs-lookup"><span data-stu-id="ce4e0-108">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce4e0-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ce4e0-109">Parameters</span></span>  

 `startOffset`  
 <span data-ttu-id="ce4e0-110">からメソッドの先頭からの、構文のスコープの最初の命令のオフセット (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="ce4e0-110">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ce4e0-111">入出力スコープ識別子を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="ce4e0-111">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce4e0-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="ce4e0-112">Return Value</span></span>  

 <span data-ttu-id="ce4e0-113">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="ce4e0-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce4e0-114">解説</span><span class="sxs-lookup"><span data-stu-id="ce4e0-114">Remarks</span></span>  

 <span data-ttu-id="ce4e0-115">`ISymUnmanagedWriter::OpenScope` スコープの開始オフセットと終了オフセットを後で定義するために [ISymUnmanagedWriter:: SetScopeRange](isymunmanagedwriter-setscoperange-method.md) と共に使用できる非透過スコープ識別子を返します。</span><span class="sxs-lookup"><span data-stu-id="ce4e0-115">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="ce4e0-116">この場合、 `ISymUnmanagedWriter::OpenScope` と [ISymUnmanagedWriter:: cloに](isymunmanagedwriter-closescope-method.md) 渡されるオフセットは無視されます。</span><span class="sxs-lookup"><span data-stu-id="ce4e0-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="ce4e0-117">スコープ識別子は、現在のメソッドでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="ce4e0-117">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce4e0-118">要件</span><span class="sxs-lookup"><span data-stu-id="ce4e0-118">Requirements</span></span>  

 <span data-ttu-id="ce4e0-119">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="ce4e0-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce4e0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce4e0-120">See also</span></span>

- [<span data-ttu-id="ce4e0-121">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ce4e0-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)

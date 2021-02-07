---
description: '詳細について: ISymUnmanagedWriter2::D efineGlobalVariable2 メソッド'
title: ISymUnmanagedWriter2::DefineGlobalVariable2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineGlobalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type:
- apiref
ms.openlocfilehash: 9a33ff8d452419ff103c9f4402620bd28196ae54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761903"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="0755c-103">ISymUnmanagedWriter2::DefineGlobalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="0755c-103">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>

<span data-ttu-id="0755c-104">グローバル変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="0755c-104">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0755c-105">構文</span><span class="sxs-lookup"><span data-stu-id="0755c-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0755c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0755c-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="0755c-107">からグローバル変数名。</span><span class="sxs-lookup"><span data-stu-id="0755c-107">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="0755c-108">からグローバル変数属性。</span><span class="sxs-lookup"><span data-stu-id="0755c-108">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="0755c-109">から署名のメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="0755c-109">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="0755c-110">からアドレスの種類。</span><span class="sxs-lookup"><span data-stu-id="0755c-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="0755c-111">からパラメーター指定の最初のアドレス。</span><span class="sxs-lookup"><span data-stu-id="0755c-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="0755c-112">からパラメーター指定の2番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="0755c-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="0755c-113">からパラメーター指定の3番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="0755c-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0755c-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="0755c-114">Return Value</span></span>  

 <span data-ttu-id="0755c-115">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="0755c-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0755c-116">要件</span><span class="sxs-lookup"><span data-stu-id="0755c-116">Requirements</span></span>  

 <span data-ttu-id="0755c-117">**ヘッダー:** CorSym .idl</span><span class="sxs-lookup"><span data-stu-id="0755c-117">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0755c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="0755c-118">See also</span></span>

- [<span data-ttu-id="0755c-119">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0755c-119">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="0755c-120">DefineGlobalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="0755c-120">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)

---
description: '詳細について: ISymUnmanagedVariable:: GetEndOffset メソッド'
title: ISymUnmanagedVariable::GetEndOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
ms.openlocfilehash: 302f19c0d9fce1864e94a79efe3a3d1515478c0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762800"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="8fda7-103">ISymUnmanagedVariable::GetEndOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="8fda7-103">ISymUnmanagedVariable::GetEndOffset Method</span></span>

<span data-ttu-id="8fda7-104">親内のこの変数の終了オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="8fda7-104">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="8fda7-105">スコープ内のローカル変数の場合は、スコープに対して定義されたオフセット内に終了オフセットが適用されます。</span><span class="sxs-lookup"><span data-stu-id="8fda7-105">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fda7-106">構文</span><span class="sxs-lookup"><span data-stu-id="8fda7-106">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fda7-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8fda7-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="8fda7-108">入出力終了オフセットを受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="8fda7-108">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8fda7-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="8fda7-109">Return Value</span></span>  

 <span data-ttu-id="8fda7-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="8fda7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fda7-111">要件</span><span class="sxs-lookup"><span data-stu-id="8fda7-111">Requirements</span></span>  

 <span data-ttu-id="8fda7-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="8fda7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fda7-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fda7-113">See also</span></span>

- [<span data-ttu-id="8fda7-114">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8fda7-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="8fda7-115">GetStartOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="8fda7-115">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)

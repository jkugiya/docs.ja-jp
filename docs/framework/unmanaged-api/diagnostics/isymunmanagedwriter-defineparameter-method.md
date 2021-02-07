---
description: '詳細について: ISymUnmanagedWriter::D efineParameter メソッド'
title: ISymUnmanagedWriter::DefineParameter メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
ms.openlocfilehash: 1e42140e33a99b224ccf3eff7ea29b7aa3ff1b15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762358"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="651d9-103">ISymUnmanagedWriter::DefineParameter メソッド</span><span class="sxs-lookup"><span data-stu-id="651d9-103">ISymUnmanagedWriter::DefineParameter Method</span></span>

<span data-ttu-id="651d9-104">現在のメソッドのパラメーターを 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="651d9-104">Defines a single parameter in the current method.</span></span> <span data-ttu-id="651d9-105">パラメーターの型は、メソッドのシグネチャ内のパラメーターの位置 (シーケンス) から取得されます。</span><span class="sxs-lookup"><span data-stu-id="651d9-105">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="651d9-106">パラメーターが特定のメソッドのメタデータで定義されている場合は、このメソッドを使用してこれらを再定義する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="651d9-106">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="651d9-107">シンボルリーダーは、シンボルストアを確認する前に、パラメーターの通常のメタデータを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="651d9-107">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="651d9-108">構文</span><span class="sxs-lookup"><span data-stu-id="651d9-108">Syntax</span></span>  
  
```cpp  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="651d9-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="651d9-109">Parameters</span></span>  

 `name`  
 <span data-ttu-id="651d9-110">からパラメーター名。</span><span class="sxs-lookup"><span data-stu-id="651d9-110">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="651d9-111">からパラメーターの属性。</span><span class="sxs-lookup"><span data-stu-id="651d9-111">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="651d9-112">からパラメーターシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="651d9-112">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="651d9-113">からアドレスの種類。</span><span class="sxs-lookup"><span data-stu-id="651d9-113">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="651d9-114">からパラメーター指定の最初のアドレス。</span><span class="sxs-lookup"><span data-stu-id="651d9-114">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="651d9-115">からパラメーター指定の2番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="651d9-115">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="651d9-116">からパラメーター指定の3番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="651d9-116">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="651d9-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="651d9-117">Return Value</span></span>  

 <span data-ttu-id="651d9-118">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="651d9-118">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="651d9-119">要件</span><span class="sxs-lookup"><span data-stu-id="651d9-119">Requirements</span></span>  

 <span data-ttu-id="651d9-120">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="651d9-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="651d9-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="651d9-121">See also</span></span>

- [<span data-ttu-id="651d9-122">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="651d9-122">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)

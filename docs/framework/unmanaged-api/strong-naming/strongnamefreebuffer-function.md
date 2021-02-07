---
description: '詳細情報: StrongNameFreeBuffer 関数'
title: StrongNameFreeBuffer 関数
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
ms.openlocfilehash: fa1b1d7710a981c5284ee79d551cbf51ede285db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736454"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="8b3a7-103">StrongNameFreeBuffer 関数</span><span class="sxs-lookup"><span data-stu-id="8b3a7-103">StrongNameFreeBuffer Function</span></span>

<span data-ttu-id="8b3a7-104">[StrongNameGetPublicKey](strongnamegetpublickey-function.md)、[StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)、または[StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md) などの厳密な名前の関数に対する前の呼び出しで割り当てられたメモリが解放されます。</span><span class="sxs-lookup"><span data-stu-id="8b3a7-104">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="8b3a7-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="8b3a7-105">This function has been deprecated.</span></span> <span data-ttu-id="8b3a7-106">代わりに [ICLRStrongName:: StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="8b3a7-106">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b3a7-107">構文</span><span class="sxs-lookup"><span data-stu-id="8b3a7-107">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b3a7-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8b3a7-108">Parameters</span></span>  

 `pbMemory`  
 <span data-ttu-id="8b3a7-109">から解放するメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8b3a7-109">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b3a7-110">要件</span><span class="sxs-lookup"><span data-stu-id="8b3a7-110">Requirements</span></span>  

 <span data-ttu-id="8b3a7-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b3a7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b3a7-112">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="8b3a7-112">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8b3a7-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8b3a7-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b3a7-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b3a7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b3a7-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b3a7-115">See also</span></span>

- [<span data-ttu-id="8b3a7-116">StrongNameFreeBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="8b3a7-116">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="8b3a7-117">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b3a7-117">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)

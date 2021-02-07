---
description: '詳細情報: GetAssemblyRefHash メソッド'
title: GetAssemblyRefHash メソッド
ms.date: 03/30/2017
api_name:
- IALink.GetAssemblyRefHash
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetAssemblyRefHash
helpviewer_keywords:
- GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type:
- apiref
ms.openlocfilehash: d8222d2fdd2c05ca1a23f881989dc344ba294bc1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718474"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="570b1-103">GetAssemblyRefHash メソッド</span><span class="sxs-lookup"><span data-stu-id="570b1-103">GetAssemblyRefHash Method</span></span>

<span data-ttu-id="570b1-104">指定されたアセンブリのハッシュ blob を取得します。</span><span class="sxs-lookup"><span data-stu-id="570b1-104">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="570b1-105">構文</span><span class="sxs-lookup"><span data-stu-id="570b1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="570b1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="570b1-106">Parameters</span></span>  

 `FileToken`  
 <span data-ttu-id="570b1-107">ハッシュが参照するアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="570b1-107">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="570b1-108">結果のハッシュ blob を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="570b1-108">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="570b1-109">ハッシュ blob のサイズをバイト単位で受信します。</span><span class="sxs-lookup"><span data-stu-id="570b1-109">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="570b1-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="570b1-110">Return Value</span></span>  

 <span data-ttu-id="570b1-111">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="570b1-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="570b1-112">要件</span><span class="sxs-lookup"><span data-stu-id="570b1-112">Requirements</span></span>  

 <span data-ttu-id="570b1-113">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="570b1-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="570b1-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="570b1-114">See also</span></span>

- [<span data-ttu-id="570b1-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="570b1-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="570b1-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="570b1-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="570b1-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="570b1-117">ALink API</span></span>](index.md)

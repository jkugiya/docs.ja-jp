---
description: '詳細情報: ITypeNameBuilder:: ToString メソッド'
title: ITypeNameBuilder::ToString メソッド
ms.date: 03/30/2017
api_name:
- ITypeNameBuilder.ToString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ToString
helpviewer_keywords:
- ToString method [.NET Framework hosting]
- ITypeNameBuilder::ToString method [.NET Framework hosting]
ms.assetid: 6372aca7-869a-4af6-ba2b-0eb1047ef5c0
topic_type:
- apiref
ms.openlocfilehash: 7caa6fd12fe8cbcebeaa19a7ae6da9931eacce8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680357"
---
# <a name="itypenamebuildertostring-method"></a><span data-ttu-id="f12c0-103">ITypeNameBuilder::ToString メソッド</span><span class="sxs-lookup"><span data-stu-id="f12c0-103">ITypeNameBuilder::ToString Method</span></span>

<span data-ttu-id="f12c0-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="f12c0-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f12c0-105">構文</span><span class="sxs-lookup"><span data-stu-id="f12c0-105">Syntax</span></span>  
  
```cpp  
HRESULT ToString (  
    [out, retval] BSTR* pszStringRepresentation  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f12c0-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="f12c0-106">Requirements</span></span>  

 <span data-ttu-id="f12c0-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f12c0-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f12c0-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f12c0-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f12c0-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f12c0-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f12c0-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f12c0-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12c0-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="f12c0-111">See also</span></span>

- [<span data-ttu-id="f12c0-112">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f12c0-112">Hosting Interfaces</span></span>](hosting-interfaces.md)

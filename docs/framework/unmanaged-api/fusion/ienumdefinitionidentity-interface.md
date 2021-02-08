---
description: 詳細については、「IEnumDefinitionIdentity インターフェイス」を参照してください。
title: IEnumDefinitionIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
ms.openlocfilehash: 1055031c064115410334bbe4b20b48deee7ec4c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800163"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="283bb-103">IEnumDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="283bb-103">IEnumDefinitionIdentity Interface</span></span>

<span data-ttu-id="283bb-104">オブジェクトのコレクションの列挙子として機能し `IDefinitionIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="283bb-104">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="283bb-105">構文</span><span class="sxs-lookup"><span data-stu-id="283bb-105">Syntax</span></span>  
  
```cpp  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="283bb-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="283bb-106">Methods</span></span>  
  
|<span data-ttu-id="283bb-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="283bb-107">Method</span></span>|<span data-ttu-id="283bb-108">説明</span><span class="sxs-lookup"><span data-stu-id="283bb-108">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="283bb-109">このと同じメンバーを含む新しいオブジェクトへのインターフェイスポインターを取得し `IEnumDefinitionIdentity` `IEnumDefinitionIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="283bb-109">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="283bb-110">現在の位置から開始して、指定した数の `IDefinitionIdentity` オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="283bb-110">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="283bb-111">命令ポインターをこのの先頭に移動し `IEnumDefinitionIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="283bb-111">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="283bb-112">現在位置を開始位置として、指定した要素数だけ前方に命令ポインターを移動します。</span><span class="sxs-lookup"><span data-stu-id="283bb-112">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="283bb-113">要件</span><span class="sxs-lookup"><span data-stu-id="283bb-113">Requirements</span></span>  

 <span data-ttu-id="283bb-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="283bb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="283bb-115">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="283bb-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="283bb-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="283bb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="283bb-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="283bb-117">See also</span></span>

- [<span data-ttu-id="283bb-118">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="283bb-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="283bb-119">IDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="283bb-119">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)

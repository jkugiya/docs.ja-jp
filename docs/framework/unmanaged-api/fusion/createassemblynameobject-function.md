---
description: '詳細情報: CreateAssemblyNameObject 関数'
title: CreateAssemblyNameObject 関数
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
ms.openlocfilehash: 0eaa74bdb37a098ad58b81658229f8c04259b730
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761182"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="32c87-103">CreateAssemblyNameObject 関数</span><span class="sxs-lookup"><span data-stu-id="32c87-103">CreateAssemblyNameObject Function</span></span>

<span data-ttu-id="32c87-104">指定された名前を持つアセンブリの一意の id を表す [IAssemblyName](iassemblyname-interface.md) インスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="32c87-104">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32c87-105">構文</span><span class="sxs-lookup"><span data-stu-id="32c87-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="32c87-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="32c87-106">Parameters</span></span>  

 `ppAssemblyNameObj`  
 <span data-ttu-id="32c87-107">入出力返された `IAssemblyName` 。</span><span class="sxs-lookup"><span data-stu-id="32c87-107">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="32c87-108">から新しいインスタンスを作成する対象のアセンブリの名前 `IAssemblyName` 。</span><span class="sxs-lookup"><span data-stu-id="32c87-108">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="32c87-109">からオブジェクトコンストラクターに渡すフラグ。</span><span class="sxs-lookup"><span data-stu-id="32c87-109">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="32c87-110">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="32c87-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="32c87-111">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c87-111">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32c87-112">要件</span><span class="sxs-lookup"><span data-stu-id="32c87-112">Requirements</span></span>  

 <span data-ttu-id="32c87-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c87-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32c87-114">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="32c87-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="32c87-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="32c87-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32c87-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32c87-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c87-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="32c87-117">See also</span></span>

- [<span data-ttu-id="32c87-118">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32c87-118">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="32c87-119">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="32c87-119">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)

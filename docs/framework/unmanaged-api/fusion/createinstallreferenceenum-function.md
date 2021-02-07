---
description: '詳細情報: CreateInstallReferenceEnum 関数'
title: CreateInstallReferenceEnum 関数
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
ms.openlocfilehash: cc7551707cb46bcf0c475a0095684dbc790836e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761147"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="7d499-103">CreateInstallReferenceEnum 関数</span><span class="sxs-lookup"><span data-stu-id="7d499-103">CreateInstallReferenceEnum Function</span></span>

<span data-ttu-id="7d499-104">指定したアセンブリへのアプリケーションの参照のリストを表す [Iinstallreferenceenum](iinstallreferenceenum-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="7d499-104">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d499-105">構文</span><span class="sxs-lookup"><span data-stu-id="7d499-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d499-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7d499-106">Parameters</span></span>  

 `ppRefEnum`  
 <span data-ttu-id="7d499-107">入出力返された `IInstallReferenceEnum` ポインター。</span><span class="sxs-lookup"><span data-stu-id="7d499-107">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="7d499-108">から参照を列挙する対象のアセンブリを識別する [IAssemblyName](iassemblyname-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="7d499-108">[in] The [IAssemblyName](iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7d499-109">から列挙子の動作に影響を与えるフラグ。</span><span class="sxs-lookup"><span data-stu-id="7d499-109">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="7d499-110">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="7d499-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="7d499-111">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d499-111">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d499-112">要件</span><span class="sxs-lookup"><span data-stu-id="7d499-112">Requirements</span></span>  

 <span data-ttu-id="7d499-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d499-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d499-114">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="7d499-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7d499-115">**Library:** Fusion.dll し、Mscorwks.dll します。</span><span class="sxs-lookup"><span data-stu-id="7d499-115">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="7d499-116">Mscorwks.dll ではなく Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にするようにします。</span><span class="sxs-lookup"><span data-stu-id="7d499-116">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="7d499-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d499-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d499-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d499-118">See also</span></span>

- [<span data-ttu-id="7d499-119">IInstallReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d499-119">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
- [<span data-ttu-id="7d499-120">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d499-120">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="7d499-121">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="7d499-121">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)

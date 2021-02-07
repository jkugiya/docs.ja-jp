---
description: '詳細情報: CreateApplicationContext 関数'
title: CreateApplicationContext 関数
ms.date: 03/30/2017
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
ms.openlocfilehash: f192e1ccc371cb6d50e4a41a286c412825ee4181
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761183"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="be7f0-103">CreateApplicationContext 関数</span><span class="sxs-lookup"><span data-stu-id="be7f0-103">CreateApplicationContext Function</span></span>

<span data-ttu-id="be7f0-104">この関数は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="be7f0-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be7f0-105">構文</span><span class="sxs-lookup"><span data-stu-id="be7f0-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="be7f0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="be7f0-106">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="be7f0-107">からフレンドリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="be7f0-107">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="be7f0-108">入出力アプリケーションコンテキストへのポインター。</span><span class="sxs-lookup"><span data-stu-id="be7f0-108">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be7f0-109">要件</span><span class="sxs-lookup"><span data-stu-id="be7f0-109">Requirements</span></span>  

 <span data-ttu-id="be7f0-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be7f0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be7f0-111">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="be7f0-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="be7f0-112">**ライブラリ:** Fusion.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="be7f0-112">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="be7f0-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be7f0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be7f0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="be7f0-114">See also</span></span>

- [<span data-ttu-id="be7f0-115">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be7f0-115">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="be7f0-116">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="be7f0-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="be7f0-117">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="be7f0-117">Global Assembly Cache</span></span>](../../app-domains/gac.md)

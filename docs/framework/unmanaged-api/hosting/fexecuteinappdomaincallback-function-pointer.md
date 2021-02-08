---
description: 詳細については、「FExecuteInAppDomainCallback 関数ポインター」を参照してください。
title: FExecuteInAppDomainCallback 関数ポインター
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
ms.openlocfilehash: 97c7fe14a3eafd6f4626d8729be3b45ad5502f1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785394"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="2ff8f-103">FExecuteInAppDomainCallback 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="2ff8f-103">FExecuteInAppDomainCallback Function Pointer</span></span>

<span data-ttu-id="2ff8f-104">マネージコードを実行するために共通言語ランタイム (CLR) によって呼び出される関数を指します。</span><span class="sxs-lookup"><span data-stu-id="2ff8f-104">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="2ff8f-105">この関数ポインターは .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="2ff8f-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff8f-106">構文</span><span class="sxs-lookup"><span data-stu-id="2ff8f-106">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ff8f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2ff8f-107">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="2ff8f-108">から実行されるマネージコードを含む、非透過的な呼び出し元割り当てメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2ff8f-108">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="2ff8f-109">このメモリの割り当てと有効期間は、呼び出し元 (つまり CLR) によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="2ff8f-109">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="2ff8f-110">これは CLR マネージヒープメモリではありません。</span><span class="sxs-lookup"><span data-stu-id="2ff8f-110">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ff8f-111">要件</span><span class="sxs-lookup"><span data-stu-id="2ff8f-111">Requirements</span></span>  

 <span data-ttu-id="2ff8f-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ff8f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ff8f-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2ff8f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ff8f-114">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="2ff8f-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="2ff8f-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ff8f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff8f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ff8f-116">See also</span></span>

- [<span data-ttu-id="2ff8f-117">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="2ff8f-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)

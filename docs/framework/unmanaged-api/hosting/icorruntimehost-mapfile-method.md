---
description: '詳細情報: ICorRuntimeHost:: MapFile メソッド'
title: ICorRuntimeHost::MapFile メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.MapFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type:
- apiref
ms.openlocfilehash: 80c01a036de83b32b9d0de745d76bb97825c980b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789633"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="f118e-103">ICorRuntimeHost::MapFile メソッド</span><span class="sxs-lookup"><span data-stu-id="f118e-103">ICorRuntimeHost::MapFile Method</span></span>

<span data-ttu-id="f118e-104">指定されたファイルをメモリにマップします。</span><span class="sxs-lookup"><span data-stu-id="f118e-104">Maps the specified file into memory.</span></span> <span data-ttu-id="f118e-105">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f118e-105">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f118e-106">構文</span><span class="sxs-lookup"><span data-stu-id="f118e-106">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f118e-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f118e-107">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="f118e-108">からマップするファイルのハンドル。</span><span class="sxs-lookup"><span data-stu-id="f118e-108">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="f118e-109">入出力ファイルのマッピングを開始する開始メモリアドレス。</span><span class="sxs-lookup"><span data-stu-id="f118e-109">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f118e-110">要件</span><span class="sxs-lookup"><span data-stu-id="f118e-110">Requirements</span></span>  

 <span data-ttu-id="f118e-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f118e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f118e-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f118e-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f118e-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f118e-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f118e-114">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="f118e-114">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f118e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f118e-115">See also</span></span>

- [<span data-ttu-id="f118e-116">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f118e-116">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)

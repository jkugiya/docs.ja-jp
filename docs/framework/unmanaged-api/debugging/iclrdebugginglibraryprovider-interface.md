---
description: 詳細については、「ICLRDebuggingLibraryProvider インターフェイス」を参照してください。
title: ICLRDebuggingLibraryProvider インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider
helpviewer_keywords:
- ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type:
- apiref
ms.openlocfilehash: 8aaec87e97d45c8b7b6f87aee64154ea3f48b133
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723284"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="a4efc-103">ICLRDebuggingLibraryProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4efc-103">ICLRDebuggingLibraryProvider Interface</span></span>

<span data-ttu-id="a4efc-104">には、提供 [ライブラリのメソッド](iclrdebugginglibraryprovider-providelibrary-method.md) メソッドが含まれています。このメソッドは、共通言語ランタイムのバージョン固有のデバッグライブラリをオンデマンドで検索して読み込むことができるようにする、ライブラリプロバイダーのコールバックインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="a4efc-104">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4efc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a4efc-105">Methods</span></span>  
  
|<span data-ttu-id="a4efc-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a4efc-106">Method</span></span>|<span data-ttu-id="a4efc-107">説明</span><span class="sxs-lookup"><span data-stu-id="a4efc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4efc-108">ProvideLibrary メソッド</span><span class="sxs-lookup"><span data-stu-id="a4efc-108">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="a4efc-109">デバッガーが、デバッグライブラリの読み込みに使用できるモジュールへのハンドルを提供できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a4efc-109">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a4efc-110">要件</span><span class="sxs-lookup"><span data-stu-id="a4efc-110">Requirements</span></span>  

 <span data-ttu-id="a4efc-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4efc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4efc-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4efc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4efc-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4efc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4efc-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4efc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4efc-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4efc-115">See also</span></span>

- [<span data-ttu-id="a4efc-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4efc-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a4efc-117">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a4efc-117">Debugging</span></span>](index.md)

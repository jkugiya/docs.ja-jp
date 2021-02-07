---
description: 詳細については、次を参照してください:、アセンブリインターフェイス
title: ICorDebugAssembly インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
ms.openlocfilehash: 746b5f4b2f26550788708d93bf0dd50f5f495041
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711948"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="cf147-103">ICorDebugAssembly インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf147-103">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="cf147-104">アセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="cf147-104">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf147-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cf147-105">Methods</span></span>  
  
|<span data-ttu-id="cf147-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="cf147-106">Method</span></span>|<span data-ttu-id="cf147-107">説明</span><span class="sxs-lookup"><span data-stu-id="cf147-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf147-108">EnumerateModules メソッド</span><span class="sxs-lookup"><span data-stu-id="cf147-108">EnumerateModules Method</span></span>](icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="cf147-109">アセンブリに格納されているモジュールの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="cf147-109">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="cf147-110">GetAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="cf147-110">GetAppDomain Method</span></span>](icordebugassembly-getappdomain-method.md)|<span data-ttu-id="cf147-111">このインスタンスを含むアプリケーションドメインへのインターフェイスポインターを取得し `ICorDebugAssembly` ます。</span><span class="sxs-lookup"><span data-stu-id="cf147-111">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="cf147-112">GetCodeBase メソッド</span><span class="sxs-lookup"><span data-stu-id="cf147-112">GetCodeBase Method</span></span>](icordebugassembly-getcodebase-method.md)|<span data-ttu-id="cf147-113">.NET Framework の現在のバージョンでは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="cf147-113">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="cf147-114">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="cf147-114">GetName Method</span></span>](icordebugassembly-getname-method.md)|<span data-ttu-id="cf147-115">アセンブリの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="cf147-115">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="cf147-116">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="cf147-116">GetProcess Method</span></span>](icordebugassembly-getprocess-method.md)|<span data-ttu-id="cf147-117">アセンブリが実行されている、のプロセスインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="cf147-117">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf147-118">解説</span><span class="sxs-lookup"><span data-stu-id="cf147-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf147-119">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cf147-119">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf147-120">要件</span><span class="sxs-lookup"><span data-stu-id="cf147-120">Requirements</span></span>  

 <span data-ttu-id="cf147-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf147-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf147-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf147-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf147-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf147-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf147-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf147-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf147-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf147-125">See also</span></span>

- [<span data-ttu-id="cf147-126">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf147-126">Debugging Interfaces</span></span>](debugging-interfaces.md)

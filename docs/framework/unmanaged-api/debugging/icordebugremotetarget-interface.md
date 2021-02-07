---
description: '詳細については、次を参照してください: いいね。'
title: ICorDebugRemoteTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
ms.openlocfilehash: c6567ebb76c7a3c415c9978dc50941cb0b8985a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717876"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="cb7fc-103">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb7fc-103">ICorDebugRemoteTarget Interface</span></span>

<span data-ttu-id="cb7fc-104">開発者が共通言語ランタイム (CLR: Common Language Runtime) 環境で Silverlight ベース アプリケーションをデバッグできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="cb7fc-104">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb7fc-105">構文</span><span class="sxs-lookup"><span data-stu-id="cb7fc-105">Syntax</span></span>  
  
```cpp  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cb7fc-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="cb7fc-106">Methods</span></span>  
  
|<span data-ttu-id="cb7fc-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="cb7fc-107">Method</span></span>|<span data-ttu-id="cb7fc-108">説明</span><span class="sxs-lookup"><span data-stu-id="cb7fc-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb7fc-109">ICorDebugRemoteTarget::GetHostName メソッド</span><span class="sxs-lookup"><span data-stu-id="cb7fc-109">ICorDebugRemoteTarget::GetHostName Method</span></span>](icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="cb7fc-110">リモート マシンのホスト名または IP アドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="cb7fc-110">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb7fc-111">解説</span><span class="sxs-lookup"><span data-stu-id="cb7fc-111">Remarks</span></span>  

 <span data-ttu-id="cb7fc-112">Windows 95、Windows 98、Windows ME、または x86 以外のプラットフォーム (IA-64、AMD64 など) では、混合モード (つまり、マネージド コードとネイティブ コード) デバッグはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="cb7fc-112">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb7fc-113">要件</span><span class="sxs-lookup"><span data-stu-id="cb7fc-113">Requirements</span></span>  

 <span data-ttu-id="cb7fc-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb7fc-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb7fc-115">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="cb7fc-115">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="cb7fc-116">**Library:** : corguids .lib</span><span class="sxs-lookup"><span data-stu-id="cb7fc-116">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb7fc-117">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="cb7fc-117">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb7fc-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb7fc-118">See also</span></span>

- [<span data-ttu-id="cb7fc-119">ICorDebugRemote インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb7fc-119">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="cb7fc-120">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb7fc-120">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="cb7fc-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb7fc-121">Debugging Interfaces</span></span>](debugging-interfaces.md)

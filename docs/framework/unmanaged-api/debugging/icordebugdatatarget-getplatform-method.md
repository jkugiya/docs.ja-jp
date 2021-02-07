---
description: '詳細については、次のページを参照してください: いいね。:: GetPlatform メソッド'
title: ICorDebugDataTarget::GetPlatform メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
ms.openlocfilehash: dec691238009ad69d2e48d994ac250bfb6641863
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764529"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="cd2cc-103">ICorDebugDataTarget::GetPlatform メソッド</span><span class="sxs-lookup"><span data-stu-id="cd2cc-103">ICorDebugDataTarget::GetPlatform Method</span></span>

<span data-ttu-id="cd2cc-104">ターゲットプロセスが実行されているプラットフォーム (プロセッサアーキテクチャやオペレーティングシステムなど) に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="cd2cc-104">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd2cc-105">構文</span><span class="sxs-lookup"><span data-stu-id="cd2cc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd2cc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd2cc-106">Parameters</span></span>  

 `pTargetPlatform`  
 <span data-ttu-id="cd2cc-107">入出力ターゲットプラットフォームを記述する [Cordebugplatformenum](cordebugplatform-enumeration.md) 列挙体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cd2cc-107">[out] A pointer to a [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd2cc-108">解説</span><span class="sxs-lookup"><span data-stu-id="cd2cc-108">Remarks</span></span>  

 <span data-ttu-id="cd2cc-109">`CorDebugPlatformEnum`列挙型の戻り値は、ポインターのサイズ、アドレス空間のレイアウト、レジスタセット、命令形式、コンテキストレイアウト、呼び出し規約などのターゲットプロセスの詳細を確認するために、 [ICorDebug](icordebug-interface.md)インターフェイスによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="cd2cc-109">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="cd2cc-110">値は、使用されている `pTargetPlatform` 実際のハードウェアを指定する代わりに、ターゲットに対してエミュレートされるプラットフォームを参照する場合があります。</span><span class="sxs-lookup"><span data-stu-id="cd2cc-110">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="cd2cc-111">たとえば、64-bit エディションの Windows オペレーティングシステムで Windows on Windows (WOW) 環境で実行されているプロセスでは、 `CORDB_PLATFORM_WINDOWS_X86` [Cordebugplatformenum](cordebugplatform-enumeration.md) 列挙型の値を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd2cc-111">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="cd2cc-112">このメソッドは成功する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd2cc-112">This method must succeed.</span></span> <span data-ttu-id="cd2cc-113">失敗した場合、ターゲットプラットフォームは使用できません。</span><span class="sxs-lookup"><span data-stu-id="cd2cc-113">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="cd2cc-114">メソッドは、次の理由により失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cd2cc-114">The method may fail for the following reasons:</span></span>  
  
- <span data-ttu-id="cd2cc-115">ターゲットに対してエミュレートされるプラットフォームは使用できません。</span><span class="sxs-lookup"><span data-stu-id="cd2cc-115">The platform that is being emulated for the target is unusable.</span></span>  
  
- <span data-ttu-id="cd2cc-116">ターゲットプラットフォームの実際のハードウェアは使用できません。</span><span class="sxs-lookup"><span data-stu-id="cd2cc-116">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd2cc-117">要件</span><span class="sxs-lookup"><span data-stu-id="cd2cc-117">Requirements</span></span>  

 <span data-ttu-id="cd2cc-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd2cc-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd2cc-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd2cc-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd2cc-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd2cc-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd2cc-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd2cc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2cc-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd2cc-122">See also</span></span>

- [<span data-ttu-id="cd2cc-123">ICorDebugDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd2cc-123">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="cd2cc-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd2cc-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cd2cc-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="cd2cc-125">Debugging</span></span>](index.md)

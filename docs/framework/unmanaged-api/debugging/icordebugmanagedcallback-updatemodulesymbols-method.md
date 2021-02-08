---
description: '詳細については、次を参照してください: UpdateModuleSymbols メソッド'
title: ICorDebugManagedCallback::UpdateModuleSymbols メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UpdateModuleSymbols
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type:
- apiref
ms.openlocfilehash: 1e20ee50cdbe0b36d0677051f1fe2b1c777e6cd6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790933"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="d4f22-103">ICorDebugManagedCallback::UpdateModuleSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="d4f22-103">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>

<span data-ttu-id="d4f22-104">共通言語ランタイムモジュールのシンボルが変更されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="d4f22-104">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4f22-105">構文</span><span class="sxs-lookup"><span data-stu-id="d4f22-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4f22-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d4f22-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="d4f22-107">からシンボルが変更されたモジュールを含むアプリケーションドメインを表す、コードのオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d4f22-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="d4f22-108">からシンボルが変更されたモジュールを表す、のモジュールオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d4f22-108">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="d4f22-109">から変更されたシンボルを格納している Win32 COM オブジェクトへのポインター `IStream` 。</span><span class="sxs-lookup"><span data-stu-id="d4f22-109">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4f22-110">解説</span><span class="sxs-lookup"><span data-stu-id="d4f22-110">Remarks</span></span>  

 <span data-ttu-id="d4f22-111">このメソッドは、 [ISymUnmanagedReader::::](../diagnostics/isymunmanagedreader-updatesymbolstore-method.md) ISymUnmanagedReader [:::: 置き換え esyman store](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md)を呼び出すことによって、モジュールのシンボルのデバッガービューを更新する機会を提供します。</span><span class="sxs-lookup"><span data-stu-id="d4f22-111">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="d4f22-112">このコールバックは、同じモジュールに対して複数回発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d4f22-112">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="d4f22-113">デバッガーは、バインドされていないソースレベルのブレークポイントをバインドしようとします。</span><span class="sxs-lookup"><span data-stu-id="d4f22-113">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4f22-114">要件</span><span class="sxs-lookup"><span data-stu-id="d4f22-114">Requirements</span></span>  

 <span data-ttu-id="d4f22-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4f22-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4f22-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4f22-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4f22-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4f22-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4f22-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4f22-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f22-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4f22-119">See also</span></span>

- [<span data-ttu-id="d4f22-120">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4f22-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

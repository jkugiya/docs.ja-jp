---
description: '詳細情報: CreateCordbObject 関数'
title: CreateCordbObject 関数
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: b6a585fc89f780b22f842127e1923414dbb8230f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801476"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="5d962-103">CreateCordbObject 関数</span><span class="sxs-lookup"><span data-stu-id="5d962-103">CreateCordbObject Function</span></span>

<span data-ttu-id="5d962-104">リモートプロセスでマネージデバッグセッションをインスタンス化する機能を提供するデバッガーインターフェイス ([ICorDebug](icordebug-interface.md)) を作成します。</span><span class="sxs-lookup"><span data-stu-id="5d962-104">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d962-105">構文</span><span class="sxs-lookup"><span data-stu-id="5d962-105">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d962-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5d962-106">Parameters</span></span>  

 `iDebuggerVersion`  
 <span data-ttu-id="5d962-107">[in] ターゲット プロセスのデバッガー バージョン。</span><span class="sxs-lookup"><span data-stu-id="5d962-107">[in] Debugger version of the target process.</span></span> <span data-ttu-id="5d962-108">リモート デバッグの場合、このパラメーターは CorDebugVersion_2_0 である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d962-108">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="5d962-109">入出力 [ICorDebug](icordebug-interface.md) インターフェイスにキャストされて返されるオブジェクトへのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5d962-109">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d962-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="5d962-110">Return Value</span></span>  

 <span data-ttu-id="5d962-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d962-111">S_OK</span></span>  
 <span data-ttu-id="5d962-112">プロセス内の CLR 数が正常に判別され、対応するハンドルとパスの配列が正しく入力されました。</span><span class="sxs-lookup"><span data-stu-id="5d962-112">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="5d962-113">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5d962-113">E_INVALIDARG</span></span>  
 <span data-ttu-id="5d962-114">`ppCordb` が null であるか、または `iDebuggerVersion` が CorDebugVersion_2_0 ではありません。</span><span class="sxs-lookup"><span data-stu-id="5d962-114">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="5d962-115">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5d962-115">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="5d962-116">`ppCordb` 用に十分なメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="5d962-116">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="5d962-117">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="5d962-117">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="5d962-118">その他のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5d962-118">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d962-119">解説</span><span class="sxs-lookup"><span data-stu-id="5d962-119">Remarks</span></span>  

 <span data-ttu-id="5d962-120">で返される [ICorDebug](icordebug-interface.md) インターフェイスは、 `ppCordb` すべてのマネージデバッグサービスの最上位レベルのデバッグインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="5d962-120">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d962-121">要件</span><span class="sxs-lookup"><span data-stu-id="5d962-121">Requirements</span></span>  

 <span data-ttu-id="5d962-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d962-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d962-123">**ヘッダー:** Coreclrremoteデバッグインターフェイス .h</span><span class="sxs-lookup"><span data-stu-id="5d962-123">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="5d962-124">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="5d962-124">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="5d962-125">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="5d962-125">**.NET Framework Versions:** 3.5 SP1</span></span>

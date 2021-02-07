---
description: '詳細情報: CreateDebuggingInterfaceFromVersion 関数'
title: CreateDebuggingInterfaceFromVersion 関数
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
ms.openlocfilehash: 163ada49f028071b48c93ee3c565152a773782ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760630"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="add41-103">CreateDebuggingInterfaceFromVersion 関数</span><span class="sxs-lookup"><span data-stu-id="add41-103">CreateDebuggingInterfaceFromVersion Function</span></span>

<span data-ttu-id="add41-104">指定されたバージョン情報に基づいて [ICorDebug](../debugging/icordebug-interface.md) オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="add41-104">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="add41-105">この関数は、.NET Framework 4 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="add41-105">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="add41-106">代わりに、共通言語ランタイム (CLR) 2.0 のインターフェイスを取得するには、 [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) メソッドを使用して、クラス識別子 CLSID_CLRDebuggingLegacy とインターフェイス識別子 IID_ICorDebug を指定します。</span><span class="sxs-lookup"><span data-stu-id="add41-106">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="add41-107">CLR 4 以降のインターフェイスを取得するには、 [Clrcreateinstance](clrcreateinstance-function.md) 関数を呼び出し、クラス識別子 CLSID_CLRDebugging とインターフェイス識別子 IID_ICLRDebugging を指定します。</span><span class="sxs-lookup"><span data-stu-id="add41-107">To get an interface for CLR 4 or later, call the [CLRCreateInstance](clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="add41-108">構文</span><span class="sxs-lookup"><span data-stu-id="add41-108">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="add41-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="add41-109">Parameters</span></span>  

 `iDebuggerVersion`  
 <span data-ttu-id="add41-110">から `ICorDebug` デバッガーによって想定されているのバージョン。</span><span class="sxs-lookup"><span data-stu-id="add41-110">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="add41-111">有効な値については、 [Cordebuginterfaceversion](../debugging/cordebuginterfaceversion-enumeration.md) 列挙体を参照してください。</span><span class="sxs-lookup"><span data-stu-id="add41-111">See the [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="add41-112">からデバッグ対象のアプリケーションまたはプロセスに関連付けられている共通言語ランタイムのバージョン。</span><span class="sxs-lookup"><span data-stu-id="add41-112">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="add41-113">この値を取得する方法については、「 [Getversionfromprocess](getversionfromprocess-function.md) 」または「 [Getversionfromprocess](getrequestedruntimeversion-function.md) メソッド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="add41-113">See the [GetVersionFromProcess](getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="add41-114">入出力オブジェクトへのポインターを受け取る位置 `ICorDebug` 。</span><span class="sxs-lookup"><span data-stu-id="add41-114">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="add41-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="add41-115">Return Value</span></span>  

 <span data-ttu-id="add41-116">このメソッドは、次の値に加えて、Winerror.h ファイルで定義されている標準 COM エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="add41-116">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="add41-117">リターン コード</span><span class="sxs-lookup"><span data-stu-id="add41-117">Return code</span></span>|<span data-ttu-id="add41-118">説明</span><span class="sxs-lookup"><span data-stu-id="add41-118">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="add41-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="add41-119">S_OK</span></span>|<span data-ttu-id="add41-120">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="add41-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="add41-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="add41-121">E_INVALIDARG</span></span>|<span data-ttu-id="add41-122">`szDebuggeeVersion` または `ppCordb` が null であるか、またはバージョン文字列が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="add41-122">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="add41-123">解説</span><span class="sxs-lookup"><span data-stu-id="add41-123">Remarks</span></span>  

 <span data-ttu-id="add41-124">パラメーターは、 `szDebuggeeVersion` 対応するバージョンの MSCorDbi.dll にマップされます。</span><span class="sxs-lookup"><span data-stu-id="add41-124">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="add41-125">要件</span><span class="sxs-lookup"><span data-stu-id="add41-125">Requirements</span></span>  

 <span data-ttu-id="add41-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="add41-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="add41-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="add41-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="add41-128">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="add41-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="add41-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="add41-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="add41-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="add41-130">See also</span></span>

- [<span data-ttu-id="add41-131">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="add41-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)

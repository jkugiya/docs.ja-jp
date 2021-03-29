---
description: '詳細情報: ICorProfilerInfo11::SetEnvironmentVariable メソッド'
title: ICorProfilerInfo11::SetEnvironmentVariable メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo11.SetEnvironmentVariable
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 77dc3fc992dec037881573323822dc11481a56be
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805606"
---
# <a name="icorprofilerinfo11setenvironmentvariable-method"></a><span data-ttu-id="38d9f-103">ICorProfilerInfo11::SetEnvironmentVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="38d9f-103">ICorProfilerInfo11::SetEnvironmentVariable Method</span></span>

<span data-ttu-id="38d9f-104">プロセスで環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="38d9f-104">Sets an environment variable in the process.</span></span> <span data-ttu-id="38d9f-105">Windows 以外のプラットフォームでは、スレッド セーフを確保するために、ランタイムに環境変数の内部キャッシュが保持されます。</span><span class="sxs-lookup"><span data-stu-id="38d9f-105">On non-Windows platforms the runtime keeps an internal cache of environment variables to ensure thread safety.</span></span> <span data-ttu-id="38d9f-106">つまり、プロファイラーで `setenv` を呼び出しても、新しい環境変数はプロセスで実行されているマネージド コードによって取得されません。</span><span class="sxs-lookup"><span data-stu-id="38d9f-106">This means that if the profiler calls `setenv` the new environment variable will not be picked up by managed code running in the process.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="38d9f-107">構文</span><span class="sxs-lookup"><span data-stu-id="38d9f-107">Syntax</span></span>  
  
```cpp  
    HRESULT SetEnvironmentVariable(
                [in, string] const WCHAR *szName,
                [in, string] const WCHAR *szValue);
```  
  
## <a name="parameters"></a><span data-ttu-id="38d9f-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="38d9f-108">Parameters</span></span>

<span data-ttu-id="38d9f-109">`szName` [入力] 設定する環境変数の名前が含まれている null で終わるワイド文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38d9f-109">`szName` [in] A pointer to a null terminated wide character string containing the name of the environment variable to set.</span></span>

<span data-ttu-id="38d9f-110">`szValue` [入力] 設定する環境変数の値が含まれている null で終わるワイド文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38d9f-110">`szValue` [in] A pointer to a null terminated wide character string containing the value of the environment variable to set.</span></span>

## <a name="requirements"></a><span data-ttu-id="38d9f-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="38d9f-111">Requirements</span></span>  

<span data-ttu-id="38d9f-112">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="38d9f-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="38d9f-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="38d9f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="38d9f-114">**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38d9f-114">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d9f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="38d9f-115">See also</span></span>

- [<span data-ttu-id="38d9f-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="38d9f-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="38d9f-117">ICorProfilerInfo11 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38d9f-117">ICorProfilerInfo11 Interface</span></span>](icorprofilerinfo11-interface.md)

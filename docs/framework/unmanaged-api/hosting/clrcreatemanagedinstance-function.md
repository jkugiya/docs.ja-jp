---
description: '詳細情報: ClrCreateManagedInstance 関数'
title: ClrCreateManagedInstance 関数
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: b6d3b014f54dd563e53cd8a4c48907d01945015f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799929"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="def0f-103">ClrCreateManagedInstance 関数</span><span class="sxs-lookup"><span data-stu-id="def0f-103">ClrCreateManagedInstance Function</span></span>

<span data-ttu-id="def0f-104">指定したマネージド型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="def0f-104">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="def0f-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="def0f-105">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="def0f-106">COM アクティブ化を使用してマネージ型のインスタンスを作成するか、ホストを使用します (「 [.NET Framework 4 および4.5 で追加された CLR ホストインターフェイス](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="def0f-106">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="def0f-107">構文</span><span class="sxs-lookup"><span data-stu-id="def0f-107">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="def0f-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="def0f-108">Parameters</span></span>  

 `pTypeName`  
 <span data-ttu-id="def0f-109">から要求されているインスタンス型の名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="def0f-109">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="def0f-110">から `IID` 要求されているインスタンス型の。</span><span class="sxs-lookup"><span data-stu-id="def0f-110">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="def0f-111">入出力呼び出し元によって要求されたマネージ型のインスタンスへのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="def0f-111">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="def0f-112">解説</span><span class="sxs-lookup"><span data-stu-id="def0f-112">Remarks</span></span>  

 <span data-ttu-id="def0f-113">共通言語ランタイムは、既にプロセスに読み込まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="def0f-113">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="def0f-114">たとえば、関数が呼び出される前に [Corbindtoruntimeex](corbindtoruntimeex-function.md) 関数の呼び出しを使用して読み込むことができ `ClrCreateManagedInstance` ます。</span><span class="sxs-lookup"><span data-stu-id="def0f-114">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="def0f-115">ランタイムが読み込まれていない場合、は `ClrCreateManagedInstance` まず、ランタイムの v v1.0.3705 の読み込みを試みます。</span><span class="sxs-lookup"><span data-stu-id="def0f-115">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="def0f-116">失敗した場合は、ランタイムの最新バージョンの読み込みが試行されます。</span><span class="sxs-lookup"><span data-stu-id="def0f-116">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="def0f-117">要件</span><span class="sxs-lookup"><span data-stu-id="def0f-117">Requirements</span></span>  

 <span data-ttu-id="def0f-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="def0f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="def0f-119">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="def0f-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="def0f-120">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="def0f-120">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="def0f-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="def0f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def0f-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="def0f-122">See also</span></span>

- [<span data-ttu-id="def0f-123">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="def0f-123">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="def0f-124">ホスティング</span><span class="sxs-lookup"><span data-stu-id="def0f-124">Hosting</span></span>](index.md)

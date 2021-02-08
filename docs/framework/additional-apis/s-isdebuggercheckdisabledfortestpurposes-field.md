---
description: '詳細情報: s_isDebuggerCheckDisabledForTestPurposes フィールド'
title: s_isDebuggerCheckDisabledForTestPurposes フィールド
ms.date: 03/30/2017
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: a71235c13a7a35872bcf5374be8077bafad5ff9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802659"
---
# <a name="s_isdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="05027-103">s_isDebuggerCheckDisabledForTestPurposes フィールド</span><span class="sxs-lookup"><span data-stu-id="05027-103">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="05027-104">クラスのこのプライベートフィールド `System.Windows.Diagnostics.VisualDiagnostics` は、アクティブなデバッガーの内部チェックが実行されるかどうかを判断するために Visual Studio によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="05027-104">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="05027-105">構文</span><span class="sxs-lookup"><span data-stu-id="05027-105">Syntax</span></span>

```csharp
private static bool s_isDebuggerCheckDisabledForTestPurposes
```

> [!WARNING]
> <span data-ttu-id="05027-106">クラスの Api `System.Windows.Diagnostics.VisualDiagnostics` は、アプリケーションがデバッガーで実行されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="05027-106">APIs in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="05027-107">`s_isDebuggerCheckDisabledForTestPurposes` `true` デバッガーの外部で api にアクセスするには、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="05027-107">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>
>
> <span data-ttu-id="05027-108">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのフィールドの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="05027-108">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="05027-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="05027-109">Requirements</span></span>

<span data-ttu-id="05027-110">**名前空間:** <xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="05027-110">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="05027-111">**アセンブリ:** プレゼンテーションコア (PresentationCore.dll)</span><span class="sxs-lookup"><span data-stu-id="05027-111">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="05027-112">**.NET Framework のバージョン:** 4.6 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="05027-112">**.NET Framework versions:** Available since 4.6.</span></span>

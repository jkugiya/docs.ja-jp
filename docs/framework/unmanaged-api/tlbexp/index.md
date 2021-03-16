---
description: '詳細情報: Tlbexp ヘルパー関数 (アンマネージ API リファレンス)'
title: Tlbexp ヘルパー関数 (アンマネージ API リファレンス)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: 8d5aacbe63d111b0b53f6bc76357a37ee4660d0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646258"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="d0484-103">Tlbexp ヘルパー関数 (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d0484-103">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>

<span data-ttu-id="d0484-104">[タイプ ライブラリ エクスポーター ツール](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) により、TlbRef.dll という名前のダイナミック リンク ライブラリが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="d0484-104">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="d0484-105">この DLL には、エクスポーター ツールによってアセンブリからタイプ ライブラリへの変換処理中に使用される、2 つのヘルパー関数とインターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d0484-105">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0484-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d0484-106">In This Section</span></span>  

 [<span data-ttu-id="d0484-107">GetTypeLibInfo 関数</span><span class="sxs-lookup"><span data-stu-id="d0484-107">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="d0484-108">タイプ ライブラリのローカライズとオペレーティング システムに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="d0484-108">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="d0484-109">LoadTypeLibWithResolver 関数</span><span class="sxs-lookup"><span data-stu-id="d0484-109">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="d0484-110">[ITypeLibResolver インターフェイス](itypelibresolver-interface.md)の実装を使ってタイプ ライブラリを読み込み、参照されたあらゆるタイプ ライブラリを解決します。</span><span class="sxs-lookup"><span data-stu-id="d0484-110">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="d0484-111">ITypeLibResolver インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0484-111">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="d0484-112">タイプ ライブラリの完全修飾パスを返す、[ResolveTypeLib メソッド](resolvetypelib-method.md)を提供します。</span><span class="sxs-lookup"><span data-stu-id="d0484-112">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>

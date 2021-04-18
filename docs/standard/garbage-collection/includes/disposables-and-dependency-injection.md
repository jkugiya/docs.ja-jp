---
author: IEvangelist
ms.topic: include
ms.date: 04/07/2021
ms.author: dapine
ms.custom: include
ms.openlocfilehash: 82802e0aef69a3c3e902edaefad621b4062de09e
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2021
ms.locfileid: "107260510"
---
> [!TIP]
> 依存関係の挿入に関して、サービスを <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> に登録すると、[サービスの有効期間](/dotnet/core/extensions/dependency-injection.md#service-lifetimes)がお客様に代り暗黙的に管理されます。 <xref:System.IServiceProvider> とそれに対応する <xref:Microsoft.Extensions.Hosting.IHost> によって、リソースのクリーンアップが調整されます。 具体的には、<xref:System.IDisposable> および <xref:System.IAsyncDisposable> の実装は、それらに指定した有効期間の終了時に適切に破棄されます。
>
> 詳細については、「[.NET での依存関係の挿入](/dotnet/core/extensions/dependency-injection.md)」を参照してください。

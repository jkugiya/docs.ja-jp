---
description: '詳細情報: 共有 Web ホストの最適化'
title: 共有 Web ホストの最適化
ms.date: 03/30/2017
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: 80627aba90825fe08f891672da4d598edb6f5686
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782443"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="5ea3d-103">共有 Web ホストの最適化</span><span class="sxs-lookup"><span data-stu-id="5ea3d-103">Optimization for Shared Web Hosting</span></span>

<span data-ttu-id="5ea3d-104">複数の小規模な Web サイトをホストして共有されているサーバーの管理者は、.NET ディレクトリの Aspnet.config ファイルの `runtime` ノードに次の `gcTrimCommitOnLowMemory` 設定を追加することで、パフォーマンスを最適化し、サイトの容量を増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-104">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> <span data-ttu-id="5ea3d-105">この設定は、共有 Web ホスティング シナリオの場合にのみお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-105">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="5ea3d-106">ガベージ コレクターは将来の割り当てのためにメモリを保持するので、コミットされる領域は厳密に必要な領域を超える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-106">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="5ea3d-107">この領域を減らすと、システム メモリにかかる負荷が高くなる時間に対応できます。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-107">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="5ea3d-108">このコミットされる領域を減らすと、パフォーマンスが向上し、より多くのサイトをホストできるようになります。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-108">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="5ea3d-109">`gcTrimCommitOnLowMemory` 設定が有効な場合、ガベージ コレクターはシステムのメモリ負荷を評価し、負荷が 90% に達するとトリミング モードに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-109">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="5ea3d-110">負荷が 85% 未満になるまでトリミング モードは維持されます。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-110">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="5ea3d-111">条件を満たしている場合、`gcTrimCommitOnLowMemory` 設定で現在のアプリケーションを助けずに無視することをガベージ コレクターで決定することができます。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-111">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ea3d-112">例</span><span class="sxs-lookup"><span data-stu-id="5ea3d-112">Example</span></span>  

 <span data-ttu-id="5ea3d-113">次の XML フラグメントは、`gcTrimCommitOnLowMemory` 設定を有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-113">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="5ea3d-114">省略記号は、`runtime` ノード内のその他の設定を示します。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-114">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ea3d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ea3d-115">See also</span></span>

- [<span data-ttu-id="5ea3d-116">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="5ea3d-116">Garbage Collection</span></span>](index.md)

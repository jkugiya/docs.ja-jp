---
title: marshaling MDA
description: マーシャリング マネージド デバッグ アシスタント (MDA) について確認します。これは、CLR によってメソッド パラメーターまたは構造体フィールドのマーシャリング情報が設定された場合に呼び出されます。
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
ms.openlocfilehash: afe54a2104e05f8fad57c7cbba4988b013aff761
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271175"
---
# <a name="marshaling-mda"></a><span data-ttu-id="2956f-103">marshaling MDA</span><span class="sxs-lookup"><span data-stu-id="2956f-103">marshaling MDA</span></span>

<span data-ttu-id="2956f-104">`marshaling` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) は、CLR がメソッドのパラメーターまたは構造体のフィールドに関するマーシャリング情報を設定するとアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="2956f-104">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="2956f-105">この MDA は、JIT コンパイルされたアセンブリでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="2956f-105">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2956f-106">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="2956f-106">Effect on the Runtime</span></span>  

 <span data-ttu-id="2956f-107">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="2956f-107">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2956f-108">出力</span><span class="sxs-lookup"><span data-stu-id="2956f-108">Output</span></span>  

 <span data-ttu-id="2956f-109">この MDA は、マネージド コンテキストとアンマネージド コンテキストのパラメーターまたはフィールドの型、およびその型を含む構造体またはメソッドを表示します。</span><span class="sxs-lookup"><span data-stu-id="2956f-109">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="2956f-110">フィールドの出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2956f-110">The following is an example of the output for a field:</span></span>  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="2956f-111">構成</span><span class="sxs-lookup"><span data-stu-id="2956f-111">Configuration</span></span>  

 <span data-ttu-id="2956f-112">この MDA の構成では、関連するフィールドまたはメソッドの名前を基にして、報告されたマーシャリング情報をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="2956f-112">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="2956f-113">`methodFilter`、`fieldFilter`、および `match` の各要素を使用してフィルターを指定する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="2956f-113">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="2956f-114">`name` 属性をアスタリスク (\*) に設定すると、すべてに一致します。</span><span class="sxs-lookup"><span data-stu-id="2956f-114">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2956f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="2956f-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="2956f-116">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="2956f-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="2956f-117">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="2956f-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)

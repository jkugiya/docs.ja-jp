---
description: '詳細情報: <ThrowUnobservedTaskExceptions> 要素'
title: <ThrowUnobservedTaskExceptions> 要素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
ms.openlocfilehash: 53f3f1275ea8419bed52fd73726c043e1c49eed7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802399"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="78b9a-103">\<ThrowUnobservedTaskExceptions> 要素</span><span class="sxs-lookup"><span data-stu-id="78b9a-103">\<ThrowUnobservedTaskExceptions> Element</span></span>

<span data-ttu-id="78b9a-104">タスクがハンドルされない例外によって実行中のプロセスを終了するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="78b9a-104">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
## <a name="syntax"></a><span data-ttu-id="78b9a-105">構文</span><span class="sxs-lookup"><span data-stu-id="78b9a-105">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78b9a-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="78b9a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="78b9a-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="78b9a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78b9a-108">属性</span><span class="sxs-lookup"><span data-stu-id="78b9a-108">Attributes</span></span>  
  
|<span data-ttu-id="78b9a-109">属性</span><span class="sxs-lookup"><span data-stu-id="78b9a-109">Attribute</span></span>|<span data-ttu-id="78b9a-110">説明</span><span class="sxs-lookup"><span data-stu-id="78b9a-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="78b9a-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="78b9a-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="78b9a-112">未処理のタスク例外が実行中のプロセスを終了するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="78b9a-112">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="78b9a-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="78b9a-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="78b9a-114">値</span><span class="sxs-lookup"><span data-stu-id="78b9a-114">Value</span></span>|<span data-ttu-id="78b9a-115">説明</span><span class="sxs-lookup"><span data-stu-id="78b9a-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="78b9a-116">は、未処理のタスク例外の実行中のプロセスを終了しません。</span><span class="sxs-lookup"><span data-stu-id="78b9a-116">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="78b9a-117">既定値です。</span><span class="sxs-lookup"><span data-stu-id="78b9a-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="78b9a-118">未処理のタスク例外の実行中のプロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="78b9a-118">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78b9a-119">子要素</span><span class="sxs-lookup"><span data-stu-id="78b9a-119">Child Elements</span></span>  

 <span data-ttu-id="78b9a-120">なし。</span><span class="sxs-lookup"><span data-stu-id="78b9a-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78b9a-121">親要素</span><span class="sxs-lookup"><span data-stu-id="78b9a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="78b9a-122">要素</span><span class="sxs-lookup"><span data-stu-id="78b9a-122">Element</span></span>|<span data-ttu-id="78b9a-123">説明</span><span class="sxs-lookup"><span data-stu-id="78b9a-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="78b9a-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="78b9a-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="78b9a-125">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="78b9a-125">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="78b9a-126">解説</span><span class="sxs-lookup"><span data-stu-id="78b9a-126">Remarks</span></span>  

 <span data-ttu-id="78b9a-127">に関連付けられている例外がまだ <xref:System.Threading.Tasks.Task> 確認されていない場合、操作がなく、親がアタッチされておらず、プロパティが読み取られていない場合 <xref:System.Threading.Tasks.Task.Wait%2A> <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> 、タスクの例外は監視されと見なされます。</span><span class="sxs-lookup"><span data-stu-id="78b9a-127">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="78b9a-128">.NET Framework 4 では、監視され例外が発生したが <xref:System.Threading.Tasks.Task> ガベージコレクションされた場合、ファイナライザーは例外をスローしてプロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="78b9a-128">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="78b9a-129">プロセスの終了は、ガベージコレクションと終了処理のタイミングによって決まります。</span><span class="sxs-lookup"><span data-stu-id="78b9a-129">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="78b9a-130">開発者がタスクに基づいて非同期コードを簡単に記述できるように、.NET Framework 4.5 では、監視され例外のこの既定の動作が変更されています。</span><span class="sxs-lookup"><span data-stu-id="78b9a-130">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="78b9a-131">監視され例外が発生しても <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> イベントは発生しますが、既定ではプロセスは終了しません。</span><span class="sxs-lookup"><span data-stu-id="78b9a-131">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="78b9a-132">代わりに、イベントハンドラーが例外を監視しているかどうかに関係なく、イベントが発生した後に例外が無視されます。</span><span class="sxs-lookup"><span data-stu-id="78b9a-132">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="78b9a-133">.NET Framework 4.5 では、アプリケーション構成ファイルの[ \<ThrowUnobservedTaskExceptions> 要素](throwunobservedtaskexceptions-element.md)を使用して、例外をスローする .NET Framework 4 つの動作を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="78b9a-133">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="78b9a-134">例外の動作は、次のいずれかの方法で指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="78b9a-134">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="78b9a-135">環境変数 () を設定する `COMPlus_ThrowUnobservedTaskExceptions` `set COMPlus_ThrowUnobservedTaskExceptions=1` 。</span><span class="sxs-lookup"><span data-stu-id="78b9a-135">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="78b9a-136">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoftでレジストリの DWORD 値 ThrowUnobservedTaskExceptions = 1 を設定し \\ ます。NETFramework キー。</span><span class="sxs-lookup"><span data-stu-id="78b9a-136">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78b9a-137">例</span><span class="sxs-lookup"><span data-stu-id="78b9a-137">Example</span></span>  

 <span data-ttu-id="78b9a-138">次の例では、アプリケーション構成ファイルを使用して、タスクで例外のスローを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="78b9a-138">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="78b9a-139">例</span><span class="sxs-lookup"><span data-stu-id="78b9a-139">Example</span></span>  

 <span data-ttu-id="78b9a-140">次の例では、タスクから監視され例外がスローされる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="78b9a-140">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="78b9a-141">コードを正常に動作させるには、リリースされたプログラムとして実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78b9a-141">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="78b9a-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="78b9a-142">See also</span></span>

- [<span data-ttu-id="78b9a-143">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="78b9a-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="78b9a-144">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="78b9a-144">Configuration File Schema</span></span>](../index.md)

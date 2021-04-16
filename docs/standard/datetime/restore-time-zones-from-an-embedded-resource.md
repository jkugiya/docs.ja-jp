---
description: '詳細情報: 方法: 埋め込みリソースからタイム ゾーンを復元する'
title: '方法: 埋め込みリソースからタイム ゾーンを復元する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], deserializing
- time zones [.NET], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: 593fb392c073ca0a3b557b7d82d430b024b3d13a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702484"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="67159-103">方法: 埋め込みリソースからタイム ゾーンを復元する</span><span class="sxs-lookup"><span data-stu-id="67159-103">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="67159-104">このトピックでは、リソース ファイルに保存されているタイム ゾーンを復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="67159-104">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="67159-105">タイム ゾーンの保存に関する情報および手順については、「[方法: 埋め込みリソースにタイム ゾーンを保存する](save-time-zones-to-an-embedded-resource.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="67159-105">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="67159-106">埋め込みリソースから TimeZoneInfo オブジェクトを逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="67159-106">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="67159-107">取得するタイム ゾーンがカスタム タイム ゾーンでない場合は、<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> メソッドを使用してインスタンス化してみてください。</span><span class="sxs-lookup"><span data-stu-id="67159-107">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="67159-108">埋め込みリソース ファイルの完全修飾名と、リソース ファイルを含むアセンブリへの参照を渡すことによって、<xref:System.Resources.ResourceManager> オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="67159-108">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="67159-109">埋め込みリソース ファイルの完全修飾名を特定できない場合は、[Ildasm.exe (IL 逆アセンブラー)](../../framework/tools/ildasm-exe-il-disassembler.md) を使用してアセンブリのマニフェストを確認します。</span><span class="sxs-lookup"><span data-stu-id="67159-109">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="67159-110">リソースを識別する `.mresource` エントリ。</span><span class="sxs-lookup"><span data-stu-id="67159-110">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="67159-111">この例では、リソースの完全修飾名は `SerializeTimeZoneData.SerializedTimeZones` です。</span><span class="sxs-lookup"><span data-stu-id="67159-111">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="67159-112">リソース ファイルが、タイム ゾーンのインスタンス化コードを含むのと同じアセンブリに埋め込まれている場合は、`static` (Visual Basic の場合は `Shared`) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> メソッドを呼び出すことによって、それへの参照を取得できます。</span><span class="sxs-lookup"><span data-stu-id="67159-112">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="67159-113"><xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> メソッドへの呼び出しが失敗する場合、またはカスタム タイム ゾーンをインスタンス化する場合は、<xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> メソッドを呼び出して、シリアル化されたタイム ゾーンを含む文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="67159-113">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="67159-114"><xref:System.TimeZoneInfo.FromSerializedString%2A> メソッドを呼び出してタイム ゾーン データを逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="67159-114">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="67159-115">例</span><span class="sxs-lookup"><span data-stu-id="67159-115">Example</span></span>

<span data-ttu-id="67159-116">次の例では、埋め込み .NET XML リソース ファイルに格納されている <xref:System.TimeZoneInfo> オブジェクトを逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="67159-116">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="67159-117">このコードでは、アプリケーションに必要な <xref:System.TimeZoneInfo> オブジェクトが存在することを確認するための例外処理を示します。</span><span class="sxs-lookup"><span data-stu-id="67159-117">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="67159-118">まず、<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> メソッドを使用してレジストリから <xref:System.TimeZoneInfo> オブジェクトを取得することによって、それのインスタンス化を試行します。</span><span class="sxs-lookup"><span data-stu-id="67159-118">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="67159-119">タイム ゾーンをインスタンス化できない場合、コードによって、埋め込みリソース ファイルからそれが取得されます。</span><span class="sxs-lookup"><span data-stu-id="67159-119">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="67159-120">カスタム タイム ゾーン (<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを使用してインスタンス化されたタイム ゾーン) のデータはレジストリに格納されないため、コードで <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> が呼び出されて南極のパーマー基地のタイム ゾーンがインスタンス化されることはありません。</span><span class="sxs-lookup"><span data-stu-id="67159-120">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="67159-121">代わりに、埋め込みリソース ファイルがすぐに検索されて、<xref:System.TimeZoneInfo.FromSerializedString%2A> メソッドが呼び出される前にタイム ゾーンのデータを含む文字列が取得されます。</span><span class="sxs-lookup"><span data-stu-id="67159-121">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="67159-122">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="67159-122">Compiling the code</span></span>

<span data-ttu-id="67159-123">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="67159-123">This example requires:</span></span>

- <span data-ttu-id="67159-124">System.Windows.Forms.dll および System.Core.dll への参照がプロジェクトに追加されること。</span><span class="sxs-lookup"><span data-stu-id="67159-124">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="67159-125">次の名前空間がインポートされていること。</span><span class="sxs-lookup"><span data-stu-id="67159-125">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="67159-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="67159-126">See also</span></span>

- [<span data-ttu-id="67159-127">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="67159-127">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="67159-128">タイム ゾーンの概要</span><span class="sxs-lookup"><span data-stu-id="67159-128">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="67159-129">方法: 埋め込みリソースにタイム ゾーンを保存する</span><span class="sxs-lookup"><span data-stu-id="67159-129">How to: Save time zones to an embedded resource</span></span>](save-time-zones-to-an-embedded-resource.md)

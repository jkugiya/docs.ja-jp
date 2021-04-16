---
description: '詳細情報: 方法: 埋め込みリソースにタイム ゾーンを保存する'
title: '方法: 埋め込みリソースにタイム ゾーンを保存する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], saving
- time zone objects [.NET], serializing
- time zone objects [.NET], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
ms.openlocfilehash: 4f1455ffa790652d2dad605a0eb71fb81a05326d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702471"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="c1ad6-103">方法: 埋め込みリソースにタイム ゾーンを保存する</span><span class="sxs-lookup"><span data-stu-id="c1ad6-103">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="c1ad6-104">タイム ゾーンに対応するアプリケーションでは、多くの場合、特定のタイム ゾーンが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-104">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="c1ad6-105">ただし、個々の <xref:System.TimeZoneInfo> オブジェクトの可用性は、ローカル システムのレジストリに格納されている情報によって異なるため、通常使用可能なタイム ゾーンも存在しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-105">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="c1ad6-106">また、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを使用してインスタンス化されたカスタム タイム ゾーンに関する情報は、他のタイム ゾーン情報と共にレジストリに格納されません。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-106">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="c1ad6-107">これらのタイム ゾーンが必要なときに確実に使用できるようにするには、それらをシリアル化して保存し、後でそれらを逆シリアル化して復元します。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-107">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="c1ad6-108">通常、<xref:System.TimeZoneInfo> オブジェクトのシリアル化は、タイム ゾーン対応アプリケーションとは別に行われます。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-108">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="c1ad6-109">シリアル化された <xref:System.TimeZoneInfo> オブジェクトを保持するために使用されるデータ ストアに応じて、タイム ゾーン データは、セットアップまたはインストール ルーチンの一部として (たとえば、データがレジストリのアプリケーション キーに格納されている場合)、または最終的なアプリケーションをコンパイルする前に実行されるユーティリティ ルーチンの一部として (たとえば、シリアル化されたデータが .NET XML リソース (.resx) ファイルに格納されている場合)、シリアル化することができます。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-109">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="c1ad6-110">アプリケーションと共にコンパイルされるリソース ファイルに加えて、他のいくつかのデータ ストアをタイム ゾーン情報に使用できます。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-110">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="c1ad6-111">これらには、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-111">These include the following:</span></span>

- <span data-ttu-id="c1ad6-112">レジストリ。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-112">The registry.</span></span> <span data-ttu-id="c1ad6-113">アプリケーションでは、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones のサブキーを使用するのではなく、独自のアプリケーション キーのサブキーを使用してカスタム タイム ゾーン データを格納する必要があることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-113">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

- <span data-ttu-id="c1ad6-114">構成ファイル。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-114">Configuration files.</span></span>

- <span data-ttu-id="c1ad6-115">その他のシステム ファイル。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-115">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="c1ad6-116">タイム ゾーンを .resx ファイルにシリアル化して保存する方法</span><span class="sxs-lookup"><span data-stu-id="c1ad6-116">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="c1ad6-117">既存のタイム ゾーンを取得するか、新しいタイム ゾーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-117">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="c1ad6-118">既存のタイム ゾーンを取得するには、「[方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする](access-utc-and-local.md)」と「[TimeZoneInfo オブジェクトをインスタンス化する](instantiate-time-zone-info.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-118">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="c1ad6-119">新しいタイム ゾーンを作成するには、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドのいずれかのオーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-119">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="c1ad6-120">詳細については、「[方法: 調整規則のないタイム ゾーンを作成する](create-time-zones-without-adjustment-rules.md)」と「[方法: 調整規則のあるタイム ゾーンを作成する](create-time-zones-with-adjustment-rules.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-120">For more information, see [How to: Create time zones without adjustment rules](create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="c1ad6-121"><xref:System.TimeZoneInfo.ToSerializedString%2A> メソッドを呼び出して、タイム ゾーンのデータを含む文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-121">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="c1ad6-122">名前を指定し、必要に応じて .resx ファイルへのパスを <xref:System.IO.StreamWriter> クラス コンストラクターに指定して、<xref:System.IO.StreamWriter> オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-122">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="c1ad6-123"><xref:System.IO.StreamWriter> オブジェクトを <xref:System.Resources.ResXResourceWriter> クラス コンストラクターに渡すことによって、<xref:System.Resources.ResXResourceWriter> オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-123">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="c1ad6-124">タイム ゾーンのシリアル化された文字列を <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-124">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="c1ad6-125"><xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-125">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="c1ad6-126"><xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-126">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="c1ad6-127"><xref:System.IO.StreamWriter.Close%2A> メソッドを呼び出して、<xref:System.IO.StreamWriter> オブジェクトを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-127">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="c1ad6-128">生成された .resx ファイルをアプリケーションの Visual Studio プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-128">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="c1ad6-129">Visual Studio の **[プロパティ]** ウィンドウを使用して、.resx ファイルの **[ビルド アクション]** プロパティが **[埋め込みリソース]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-129">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="c1ad6-130">例</span><span class="sxs-lookup"><span data-stu-id="c1ad6-130">Example</span></span>

<span data-ttu-id="c1ad6-131">次の例では、中部標準時を表す <xref:System.TimeZoneInfo> オブジェクトと、南極のパーマー基地の時刻を表す <xref:System.TimeZoneInfo> オブジェクトを、SerializedTimeZones.resx という名前の .NET XML リソース ファイルにシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-131">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="c1ad6-132">通常、中部標準時はレジストリで定義されています。南極のパーマー基地はカスタム タイム ゾーンです。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-132">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="c1ad6-133">この例では、コンパイル時にリソース ファイルで使用できるように <xref:System.TimeZoneInfo> オブジェクトをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-133">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="c1ad6-134"><xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> メソッドは、完全なヘッダー情報を .NET XML リソース ファイルに追加するため、既存のファイルにリソースを追加するために使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-134">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="c1ad6-135">この例では、SerializedTimeZones.resx ファイルを確認し、存在する場合は、2 つのシリアル化されたタイム ゾーン以外のすべてのリソースを汎用 <xref:System.Collections.Generic.Dictionary%602> オブジェクトに格納することで、この処理を行います。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-135">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="c1ad6-136">その後、既存のファイルが削除され、既存のリソースが新しい SerializedTimeZones.resx ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-136">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="c1ad6-137">シリアル化されたタイム ゾーン データもこのファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-137">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="c1ad6-138">リソースのキー (または **名前**) フィールドに、空白を埋め込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-138">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="c1ad6-139"><xref:System.String.Replace%28System.String%2CSystem.String%29> メソッドは、リソース ファイルに割り当てられる前に、タイム ゾーン識別子内の埋め込まれた空白をすべて削除するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-139">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="c1ad6-140">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c1ad6-140">Compiling the code</span></span>

<span data-ttu-id="c1ad6-141">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-141">This example requires:</span></span>

- <span data-ttu-id="c1ad6-142">System.Windows.Forms.dll および System.Core.dll への参照がプロジェクトに追加されること。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-142">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="c1ad6-143">次の名前空間がインポートされていること。</span><span class="sxs-lookup"><span data-stu-id="c1ad6-143">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="c1ad6-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1ad6-144">See also</span></span>

- [<span data-ttu-id="c1ad6-145">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="c1ad6-145">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="c1ad6-146">タイム ゾーンの概要</span><span class="sxs-lookup"><span data-stu-id="c1ad6-146">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="c1ad6-147">方法: 埋め込みリソースからタイム ゾーンを復元する</span><span class="sxs-lookup"><span data-stu-id="c1ad6-147">How to: Restore time zones from an embedded resource</span></span>](restore-time-zones-from-an-embedded-resource.md)

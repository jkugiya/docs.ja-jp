---
description: 詳細については、.NET Native でのはじめにに関するページを参照してください
title: .NET ネイティブの概要
ms.date: 03/30/2017
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
ms.openlocfilehash: 6079e21764ebc39515eb9b9f217057d916da8942
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747804"
---
# <a name="getting-started-with-net-native"></a><span data-ttu-id="59ea0-103">.NET ネイティブの概要</span><span class="sxs-lookup"><span data-stu-id="59ea0-103">Getting Started with .NET Native</span></span>

<span data-ttu-id="59ea0-104">Windows 10 用に新しい Windows アプリを作成する場合も、既存の Windows ストア アプリを移行する場合も、次に示す同じ手順を実行することになります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-104">Whether you are writing a new Windows app for Windows 10 or you are migrating an existing Windows Store app, you can follow the same set of procedures.</span></span> <span data-ttu-id="59ea0-105">.NET Native アプリを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="59ea0-105">To create a .NET Native app, follow these steps:</span></span>

1. <span data-ttu-id="59ea0-106">[Windows 10 を対象とするユニバーサル Windows プラットフォーム (UWP) ストア アプリを開発](#Step1)し、アプリのデバッグ ビルドをテストして、そのアプリが適切に動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="59ea0-106">[Develop a Universal Windows Platform (UWP) app that targets Windows 10](#Step1), and test the debug builds of your app to ensure that it works properly.</span></span>

2. <span data-ttu-id="59ea0-107">[追加のリフレクションおよびシリアル化の使用を処理](#Step2)します。</span><span class="sxs-lookup"><span data-stu-id="59ea0-107">[Handle additional reflection and serialization usage](#Step2).</span></span>

3. <span data-ttu-id="59ea0-108">[リリース ビルドのアプリを展開して、テストします](#Step3)。</span><span class="sxs-lookup"><span data-stu-id="59ea0-108">[Deploy and test the release builds of your app](#Step3).</span></span>

4. <span data-ttu-id="59ea0-109">[メタデータの欠落を手動で解決し](#Step4)、すべての問題が解決されるまで [手順 3](#Step3) を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="59ea0-109">[Manually resolve missing metadata](#Step4), and repeat [step 3](#Step3) until all issues are resolved.</span></span>

> [!NOTE]
> <span data-ttu-id="59ea0-110">既存の Windows ストアアプリを .NET Native に移行する場合は、「 [Windows ストアアプリの .NET Native への移行](migrating-your-windows-store-app-to-net-native.md)」を必ず確認してください。</span><span class="sxs-lookup"><span data-stu-id="59ea0-110">If you are migrating an existing Windows Store app to .NET Native, be sure to review [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

<a name="Step1"></a>

## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a><span data-ttu-id="59ea0-111">手順 1: UWP アプリのデバッグ ビルドを開発してテストする</span><span class="sxs-lookup"><span data-stu-id="59ea0-111">Step 1: Develop and test debug builds of your UWP app</span></span>

<span data-ttu-id="59ea0-112">新しいアプリを開発するか既存のアプリを移行するかに関係なく、Windows アプリについては同じ手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="59ea0-112">Whether you are developing a new app or migrating an existing one, you follow the same process as for any Windows app.</span></span>

1. <span data-ttu-id="59ea0-113">Visual C# または Visual Basic のユニバーサル Windows アプリ テンプレートを使用して、Visual Studio で新しい UWP プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="59ea0-113">Create a new UWP project in Visual Studio by using the Universal Windows app template for Visual C# or Visual Basic.</span></span> <span data-ttu-id="59ea0-114">既定では、すべての UWP アプリケーションは CoreCLR を対象としていて、.NET ネイティブ ツール チェーンを使用してリリース ビルドがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="59ea0-114">By default, all UWP applications target the CoreCLR and their release builds are compiled by using the .NET Native tool chain.</span></span>

2. <span data-ttu-id="59ea0-115">UWP アプリ プロジェクトのコンパイルに .NET ネイティブ ツール チェーンを使用する場合と使用しない場合では、両者の間に既知の互換性問題がある点にご注意ください。</span><span class="sxs-lookup"><span data-stu-id="59ea0-115">Note that there are some known compatibility issues between compiling UWP app projects with the .NET Native tool chain and without it.</span></span> <span data-ttu-id="59ea0-116">詳細については、 [移行ガイド](migrating-your-windows-store-app-to-net-native.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59ea0-116">Refer to the [migration guide](migrating-your-windows-store-app-to-net-native.md) for more information.</span></span>

<span data-ttu-id="59ea0-117">ローカルシステム (またはシミュレーター) で実行される .NET Native の領域に対して C# または Visual Basic コードを記述できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="59ea0-117">You can now write C# or Visual Basic code against the .NET Native surface area that runs on the local system (or in the simulator).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59ea0-118">アプリを開発するときに、コードでのシリアル化またはリフレクションを使用する場合は注意してください。</span><span class="sxs-lookup"><span data-stu-id="59ea0-118">As you develop your app, note any use of serialization or reflection in your code.</span></span>

<span data-ttu-id="59ea0-119">既定では、デバッグビルドは、F5 を使用した迅速な配置を可能にするために JIT でコンパイルされますが、リリースビルドは .NET Native プリコンパイルテクノロジを使用してコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="59ea0-119">By default, debug builds are JIT-compiled to enable rapid F5 deployment, while release builds are compiled by using the .NET Native pre-compilation technology.</span></span> <span data-ttu-id="59ea0-120">つまり、アプリのデバッグ ビルドが正常に動作するようにするには、.NET ネイティブ ツール チェーンでコンパイルする前に、これをビルドしてテストする必要があるということです。</span><span class="sxs-lookup"><span data-stu-id="59ea0-120">This means you should build and test the debug builds of your app to ensure that they work normally before compiling them with the .NET Native tool chain.</span></span>

<a name="Step2"></a>

## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a><span data-ttu-id="59ea0-121">手順 2: 追加のリフレクションおよびシリアル化の使用を処理する</span><span class="sxs-lookup"><span data-stu-id="59ea0-121">Step 2: Handle additional reflection and serialization usage</span></span>

<span data-ttu-id="59ea0-122">プロジェクト作成時に Default.rd.xml という名前のランタイム ディレクティブ ファイルがプロジェクトに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="59ea0-122">A runtime directives file, Default.rd.xml, is automatically added to your project when you create it.</span></span> <span data-ttu-id="59ea0-123">C# で開発する場合、このファイルはプロジェクトの **Properties** フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-123">If you develop in C#, it is found in your project's **Properties** folder.</span></span> <span data-ttu-id="59ea0-124">Visual Basic で開発する場合、このファイルはプロジェクトの **My Project** フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-124">If you develop in Visual Basic, it is found in your project's **My Project** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="59ea0-125">ランタイム ディレクティブ ファイルが必要となる理由の背景を含む .NET ネイティブのコンパイルの概要については、「 [.NET ネイティブとコンパイル](net-native-and-compilation.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="59ea0-125">For an overview of the .NET Native compilation process that provides background on why a runtime directives file is needed, see [.NET Native and Compilation](net-native-and-compilation.md).</span></span>

<span data-ttu-id="59ea0-126">ランタイム ディレクティブ ファイルは、アプリの実行時に必要なメタデータを定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="59ea0-126">The runtime directives file is used to define the metadata that your app needs at run time.</span></span> <span data-ttu-id="59ea0-127">この既定バージョンのファイルで十分な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-127">In some cases, the default version of the file may be adequate.</span></span> <span data-ttu-id="59ea0-128">ただし、シリアル化やリフレクションに依存するコードには、ランタイム ディレクティブ ファイルに追加のエントリが必要になるものがあります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-128">However, some code that relies on serialization or reflection may require additional entries in the runtime directives file.</span></span>

<span data-ttu-id="59ea0-129">**シリアル化**</span><span class="sxs-lookup"><span data-stu-id="59ea0-129">**Serialization**</span></span>

<span data-ttu-id="59ea0-130">シリアライザーには 2 つのカテゴリがあり、これらはいずれもランタイム ディレクティブ ファイルに追加エントリを必要とする場合があります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-130">There are two categories of serializers, and both may require additional entries in the runtime directives file:</span></span>

- <span data-ttu-id="59ea0-131">非リフレクション ベースのシリアライザー。</span><span class="sxs-lookup"><span data-stu-id="59ea0-131">Non-reflection based serializers.</span></span> <span data-ttu-id="59ea0-132"><xref:System.Runtime.Serialization.DataContractSerializer>、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>、および <xref:System.Xml.Serialization.XmlSerializer> クラスなど、.NET Framework クラス ライブラリ内にあるシリアライザーは、リフレクションに依存しません。</span><span class="sxs-lookup"><span data-stu-id="59ea0-132">The serializers found in the .NET Framework class library, such as the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes, do not rely on reflection.</span></span> <span data-ttu-id="59ea0-133">ただし、これらのシリアライザーでは、シリアル化または逆シリアル化されるオブジェクトに基づいてコードが生成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-133">However, they do require that code be generated based on the object to be serialized or deserialized.</span></span>  <span data-ttu-id="59ea0-134">詳しくは、「 [シリアル化とメタデータ](serialization-and-metadata.md)」の「Microsoft のシリアライザー」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="59ea0-134">For more information, see the "Microsoft Serializers" section in [Serialization and Metadata](serialization-and-metadata.md).</span></span>

- <span data-ttu-id="59ea0-135">サードパーティ シリアライザー。</span><span class="sxs-lookup"><span data-stu-id="59ea0-135">Third-party serializers.</span></span> <span data-ttu-id="59ea0-136">サードパーティ製のシリアル化ライブラリ (最も一般的なものは Newtonsoft JSON シリアライザー) であり、一般的にリフレクションベースであり、 \* オブジェクトのシリアル化と逆シリアル化をサポートするために.rd.xml ファイル内のエントリが必要です。</span><span class="sxs-lookup"><span data-stu-id="59ea0-136">Third-party serialization libraries, the most common of which is the Newtonsoft JSON serializer, are generally reflection-based and require entries in the \*.rd.xml file to support object serialization and deserialization.</span></span> <span data-ttu-id="59ea0-137">詳しくは、「 [Serialization and Metadata](serialization-and-metadata.md)」の「サードパーティ シリアライザー」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="59ea0-137">For more information, see the "Third-Party Serializers" section in [Serialization and Metadata](serialization-and-metadata.md).</span></span>

<span data-ttu-id="59ea0-138">**リフレクションに依存するメソッド**</span><span class="sxs-lookup"><span data-stu-id="59ea0-138">**Methods that rely on reflection**</span></span>

<span data-ttu-id="59ea0-139">コードでのリフレクションの使用は明確ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-139">In some cases, the use of reflection in code is not obvious.</span></span> <span data-ttu-id="59ea0-140">一般的な API やプログラミング パターンの中には、リフレクション API の一部とは見なされないが、正常な実行にリフレクションを必要とするものがあります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-140">Some common APIs or programming patterns aren't considered part of the reflection API but rely on reflection to execute successfully.</span></span> <span data-ttu-id="59ea0-141">これには、次のような型インスタンス化およびメソッド作成方法があります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-141">This includes the following type instantiation and method construction methods:</span></span>

- <span data-ttu-id="59ea0-142"><xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> メソッド</span><span class="sxs-lookup"><span data-stu-id="59ea0-142">The <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method</span></span>

- <span data-ttu-id="59ea0-143"><xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> メソッドと <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> メソッド</span><span class="sxs-lookup"><span data-stu-id="59ea0-143">The <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> and <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> methods</span></span>

- <span data-ttu-id="59ea0-144"><xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> メソッド。</span><span class="sxs-lookup"><span data-stu-id="59ea0-144">The <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="59ea0-145">詳細については、「 [リフレクションに依存する API](apis-that-rely-on-reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59ea0-145">For more information, see [APIs That Rely on Reflection](apis-that-rely-on-reflection.md).</span></span>

> [!NOTE]
> <span data-ttu-id="59ea0-146">ランタイム ディレクティブ ファイルで使用される型名は完全修飾である必要があります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-146">Type names used in runtime directives files must be fully qualified.</span></span> <span data-ttu-id="59ea0-147">たとえば、ファイルでは "String" ではなく "System.String" を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-147">For example, the file must specify "System.String" instead of "String".</span></span>

<a name="Step3"></a>

## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a><span data-ttu-id="59ea0-148">手順 3: リリース ビルドのアプリを展開してテストする</span><span class="sxs-lookup"><span data-stu-id="59ea0-148">Step 3: Deploy and test the release builds of your app</span></span>

<span data-ttu-id="59ea0-149">ランタイム ディレクティブ ファイルを更新したら、アプリのリリース ビルドを再ビルドして配置できます。</span><span class="sxs-lookup"><span data-stu-id="59ea0-149">After you’ve updated the runtime directives file, you can rebuild and deploy release builds of your app.</span></span> <span data-ttu-id="59ea0-150">.NET Native バイナリは、プロジェクトの [**プロパティ**] ダイアログボックスの [**コンパイル**] タブにある [**ビルド出力パス**] テキストボックスで指定したディレクトリの ILC サブディレクトリに配置されます。このフォルダーにないバイナリは .NET Native でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="59ea0-150">.NET Native binaries are placed in the ILC.out subdirectory of the directory specified in the **Build output path** text box of  the project's **Properties** dialog box, **Compile** tab. Binaries that aren't in this folder haven't been compiled with .NET Native.</span></span> <span data-ttu-id="59ea0-151">ターゲット プラットフォームごとに、アプリを十分にテストし、失敗シナリオを含むすべてのシナリオをテストします。</span><span class="sxs-lookup"><span data-stu-id="59ea0-151">Test your app thoroughly, and test all scenarios, including failure scenarios, on each of its target platforms.</span></span>

<span data-ttu-id="59ea0-152">アプリが正常に動作しない場合 (特に実行時に [MissingMetadataException](missingmetadataexception-class-net-native.md) 例外または [MissingInteropDataException](missinginteropdataexception-class-net-native.md) 例外をスローする場合)、次のセクション「[手順 4: メタデータの欠落を手動で解決する](#Step4)」の手順を実行してください。</span><span class="sxs-lookup"><span data-stu-id="59ea0-152">If your app doesn’t work properly (particularly in cases where it throws [MissingMetadataException](missingmetadataexception-class-net-native.md) or [MissingInteropDataException](missinginteropdataexception-class-net-native.md) exceptions at run time), follow the instructions in the next section, [Step 4: Manually resolve missing metadata](#Step4).</span></span> <span data-ttu-id="59ea0-153">初回例外を有効にすると、このようなバグの検出に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="59ea0-153">Enabling first-chance exceptions may help you find these bugs.</span></span>

<span data-ttu-id="59ea0-154">アプリのデバッグビルドをテストしてデバッグし、 [MissingMetadataException](missingmetadataexception-class-net-native.md) 例外と [MissingInteropDataException](missinginteropdataexception-class-net-native.md) 例外を削除したことが確実な場合は、アプリを最適化された .NET Native アプリとしてテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-154">When you’ve tested and debugged the debug builds of your app and you’re confident that you’ve eliminated the [MissingMetadataException](missingmetadataexception-class-net-native.md) and [MissingInteropDataException](missinginteropdataexception-class-net-native.md) exceptions, you should test your app as an optimized .NET Native app.</span></span> <span data-ttu-id="59ea0-155">これを行うには、アクティブ プロジェクトの構成を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="59ea0-155">To do this, change your active project configuration from **Debug** to **Release**.</span></span>

<a name="Step4"></a>

## <a name="step-4-manually-resolve-missing-metadata"></a><span data-ttu-id="59ea0-156">手順 4: メタデータの欠落を手動で解決する</span><span class="sxs-lookup"><span data-stu-id="59ea0-156">Step 4: Manually resolve missing metadata</span></span>

<span data-ttu-id="59ea0-157">デスクトップでは発生しない .NET Native で発生する最も一般的なエラーは、ランタイムの [MissingMetadataException](missingmetadataexception-class-net-native.md)、 [MissingInteropDataException](missinginteropdataexception-class-net-native.md)、または [誤 singruntimeartifactexception](missingruntimeartifactexception-class-net-native.md) 例外です。</span><span class="sxs-lookup"><span data-stu-id="59ea0-157">The most common failure you'll encounter with .NET Native that you don't encounter on the desktop is a runtime [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), or [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="59ea0-158">メタデータの欠落は、予期しない動作やアプリの失敗によって判明することもあります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-158">In some cases, the absence of metadata can manifest itself in unpredictable behavior or even in app failures.</span></span> <span data-ttu-id="59ea0-159">このセクションでは、ランタイム ディレクティブ ファイルにディレクティブを追加することによって、これらの例外をデバッグして解決する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="59ea0-159">This section discusses how you can debug and resolve these exceptions by adding directives to the runtime directives file.</span></span> <span data-ttu-id="59ea0-160">ランタイム ディレクティブの形式については、「[ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](runtime-directives-rd-xml-configuration-file-reference.md)」を参照してださい。</span><span class="sxs-lookup"><span data-stu-id="59ea0-160">For information about the format of runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="59ea0-161">ランタイム ディレクティブを追加したら、もう一度 [アプリを配置およびテスト](#Step3) して、例外が発生しなくなるまで新しい [MissingMetadataException](missingmetadataexception-class-net-native.md)、 [MissingInteropDataException](missinginteropdataexception-class-net-native.md)、および  [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 例外を解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59ea0-161">After you’ve added runtime directives, you should [deploy and test your app](#Step3) again and resolve any new [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and  [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions until you encounter no more exceptions.</span></span>

> [!TIP]
> <span data-ttu-id="59ea0-162">高いレベルでランタイム ディレクティブを指定して、アプリがコードの変更に対応できるようにします。</span><span class="sxs-lookup"><span data-stu-id="59ea0-162">Specify the runtime directives at a high level to enable your app to be resilient to code changes.</span></span>  <span data-ttu-id="59ea0-163">メンバー レベルではなく、名前空間レベルおよび型レベルでランタイム ディレクティブを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="59ea0-163">We recommend adding runtime directives at the namespace and type levels rather than the member level.</span></span> <span data-ttu-id="59ea0-164">回復性と、バイナリを大きくすることに伴うコンパイル時間の延長の間にはトレードオフがある場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="59ea0-164">Note that there may be a tradeoff between resiliency and larger binaries with longer compile times.</span></span>

<span data-ttu-id="59ea0-165">メタデータの欠落例外に対応する場合は、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="59ea0-165">When addressing a missing metadata exception, consider these issues:</span></span>

- <span data-ttu-id="59ea0-166">例外が発生する前にアプリが何を実行しようとしていたか。</span><span class="sxs-lookup"><span data-stu-id="59ea0-166">What was the app trying to do before the exception?</span></span>

  - <span data-ttu-id="59ea0-167">たとえば、データ バインド、シリアル化または逆シリアル化を行っていたか、またはリフレクション API を直接使用していましたか。</span><span class="sxs-lookup"><span data-stu-id="59ea0-167">For example, was it data binding, serializing or deserializing data, or directly using the reflection API?</span></span>

- <span data-ttu-id="59ea0-168">これは特殊なケースか、または他の型でも同じ問題が発生すると考えられるか。</span><span class="sxs-lookup"><span data-stu-id="59ea0-168">Is this an isolated case, or do you believe you'll encounter the same issue for other types?</span></span>

  - <span data-ttu-id="59ea0-169">たとえば、 [MissingMetadataException](missingmetadataexception-class-net-native.md) 例外は、アプリのオブジェクト モデル内の型をシリアル化するときにスローされます。</span><span class="sxs-lookup"><span data-stu-id="59ea0-169">For example, a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception is thrown when serializing a type in the app’s object model.</span></span>  <span data-ttu-id="59ea0-170">シリアル化されるその他の型がわかっている場合は、それらの型 (または、コードがどの程度構造的に作成されているかによって、それを含む名前空間) に同時にランタイム ディレクティブを追加できます。</span><span class="sxs-lookup"><span data-stu-id="59ea0-170">If you know other types that will be serialized, you can add runtime directives for those types (or for their containing namespaces, depending on how well the code is organized) at the same time.</span></span>

- <span data-ttu-id="59ea0-171">リフレクションを使用しないようにコードを書き換えることができるか。</span><span class="sxs-lookup"><span data-stu-id="59ea0-171">Can you rewrite the code so it doesn’t use reflection?</span></span>

  - <span data-ttu-id="59ea0-172">たとえば、予期される型がわかっている場合に、コードで `dynamic` キーワードが使用されていますか。</span><span class="sxs-lookup"><span data-stu-id="59ea0-172">For example, does the code use the `dynamic` keyword when you know what type to expect?</span></span>

  - <span data-ttu-id="59ea0-173">より適切な他の方法を使用できる場合に、リフレクションに依存するメソッドをコードで呼び出していますか。</span><span class="sxs-lookup"><span data-stu-id="59ea0-173">Does the code call a method that depends on reflection when some better alternative is available?</span></span>

> [!NOTE]
> <span data-ttu-id="59ea0-174">リフレクションの違い、およびデスクトップアプリと .NET Native でのメタデータの可用性に起因する問題の処理の詳細については、「 [リフレクションに依存する api](apis-that-rely-on-reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59ea0-174">For additional information about handling problems that stem from differences in reflection and the availability of metadata in desktop apps and .NET Native, see [APIs That Rely on Reflection](apis-that-rely-on-reflection.md).</span></span>

<span data-ttu-id="59ea0-175">アプリのテスト時に発生する例外およびその他の問題の処理に関する具体的な例については、次のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="59ea0-175">For some specific examples of handling exceptions and other issues that occur when testing your app, see:</span></span>

- [<span data-ttu-id="59ea0-176">例:データ バインド時の例外の処理</span><span class="sxs-lookup"><span data-stu-id="59ea0-176">Example: Handling Exceptions When Binding Data</span></span>](example-handling-exceptions-when-binding-data.md)

- [<span data-ttu-id="59ea0-177">例:動的プログラミングのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="59ea0-177">Example: Troubleshooting Dynamic Programming</span></span>](example-troubleshooting-dynamic-programming.md)

- [<span data-ttu-id="59ea0-178">.NET ネイティブ アプリでのランタイム例外</span><span class="sxs-lookup"><span data-stu-id="59ea0-178">Runtime Exceptions in .NET Native Apps</span></span>](runtime-exceptions-in-net-native-apps.md)

## <a name="see-also"></a><span data-ttu-id="59ea0-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="59ea0-179">See also</span></span>

- [<span data-ttu-id="59ea0-180">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="59ea0-180">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- <span data-ttu-id="59ea0-181">[.NET ネイティブのセットアップおよび構成](/previous-versions/dn600164(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="59ea0-181">[.NET Native Setup and Configuration](/previous-versions/dn600164(v=vs.110))</span></span>
- [<span data-ttu-id="59ea0-182">.NET Native とコンパイル</span><span class="sxs-lookup"><span data-stu-id="59ea0-182">.NET Native and Compilation</span></span>](net-native-and-compilation.md)
- [<span data-ttu-id="59ea0-183">リフレクションおよび .NET ネイティブ</span><span class="sxs-lookup"><span data-stu-id="59ea0-183">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
- [<span data-ttu-id="59ea0-184">リフレクションに依存する API</span><span class="sxs-lookup"><span data-stu-id="59ea0-184">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)
- [<span data-ttu-id="59ea0-185">シリアル化とメタデータ</span><span class="sxs-lookup"><span data-stu-id="59ea0-185">Serialization and Metadata</span></span>](serialization-and-metadata.md)
- [<span data-ttu-id="59ea0-186">Windows ストア アプリの .NET ネイティブへの移行</span><span class="sxs-lookup"><span data-stu-id="59ea0-186">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)

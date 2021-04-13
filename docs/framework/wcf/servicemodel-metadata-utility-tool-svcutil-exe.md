---
title: ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)
description: メタデータ ドキュメントから WFC サービス モデル コードを生成し、サービス モデル コードからメタデータ ドキュメントを生成する、ServiceModel メタデータ ユーティリティ ツールについて説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], building
- endpoints [WCF]
- Svcutil.exe
- clients [WCF], consuming services
ms.assetid: 1abf3d9f-b420-46f1-b628-df238751f308
ms.openlocfilehash: 65013f43aa0075b6de6999741afb448c2a35afb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689928"
---
# <a name="servicemodel-metadata-utility-tool-svcutilexe"></a>ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)

ServiceModel メタデータ ユーティリティ ツールを使用して、メタデータ ドキュメントからサービス モデル コードを生成し、サービス モデル コードからメタデータ ドキュメントを生成します。

## <a name="svcutilexe"></a>SvcUtil.exe

ServiceModel メタデータ ユーティリティ ツールは、Windows SDK のインストール場所である *%ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin* にあります。

### <a name="functionalities"></a>機能

次の表では、このツールによって提供されるさまざまな機能とその使用方法を説明する対応トピックをまとめています。

|タスク|トピック|
|----------|-----------|
|実行中のサービスまたは静的なメタデータ ドキュメントからコードを生成します。|[サービス メタデータからの WCF クライアントの生成](./feature-details/generating-a-wcf-client-from-service-metadata.md)|
|コンパイル済みのコードからメタデータ ドキュメントをエクスポートします。|[方法: Svcutil.exe を使用してコンパイル済みのサービス コードからメタデータをエクスポートする](./feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)|
|コンパイル済みサービス コードを検証します。|[方法: Svcutil.exe を使用してコンパイル済みサービス コードを検証する](./feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)|
|実行中のサービスからメタデータ ドキュメントをダウンロードします。|[方法: Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする](./feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)|
|シリアル化コードを生成します。|[方法: XmlSerializer を使用する WCF クライアント アプリケーションの起動時間を短縮する](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)|

> [!CAUTION]
> パラメーターに指定された名前が同じ場合は、Svcutil によってディスク上の既存のファイルが上書きされます。 これには、コード ファイル、構成ファイル、またはメタデータ ファイルが含まれます。 コードおよび構成ファイルの生成時にこれを回避するには、`/mergeConfig` スイッチを使用します。
>
> また、データ コントラクト生成には、型参照用の `/r` および `/ct` スイッチがあります。 XmlSerializer の使用時には、これらのスイッチは機能しません。

### <a name="timeout"></a>タイムアウト

メタデータを取得する場合、ツールには、5 分間のタイムアウトがあります。 このタイムアウトは、ネットワーク経由でメタデータを取得する場合にのみ適用されます。 タイムアウトは、そのメタデータの処理には適用されません。

### <a name="multi-targeting"></a>マルチターゲット

このツールは複数バージョン対応機能をサポートしていません。 *svcutil.exe* から .NET Framework 4 の成果物を生成する場合は、.NET Framework 4 SDK の *svcutil.exe* を使用します。 .NET Framework 3.5 の成果物を生成するには、.NET Framework 3.5 SDK の実行可能ファイルを使用します。

### <a name="accessing-wsdl-documents"></a>WSDL ドキュメントへのアクセス

Svcutil を使用して、セキュリティ トークン サービス (STS) への参照がある WSDL ドキュメントにアクセスする場合、Svcutil は WS-MetadataExchange を使用して STS を呼び出します。 ただし、サービスは、WS-MetadataExchange または HTTP GET を使用して WSDL ドキュメントを公開できます。 そのため、STS が HTTP GET のみを使用して WSDL ドキュメントを公開している場合、WinFX で作成されたクライアントは失敗します。 .NET Framework 3.5 で作成されたクライアントの場合、Svcutil では、WS-MetadataExchange と HTTP GET の両方を使用して、STS WSDL の取得を試みます。

## <a name="using-svcutilexe"></a>SvcUtil.exe の使用

### <a name="common-usages"></a>一般的な使用

次の表は、このツールで一般的に使用されるオプションを示しています。

|オプション|説明|
|------------|-----------------|
|/directory:\<directory>|ファイルを作成するためのディレクトリ。<br /><br /> 既定 : 現在のディレクトリ<br /><br /> 短縮形 : `/d`|
|/help|このツールのコマンド構文とオプションを表示します。<br /><br /> 短縮形 : `/?`|
|/noLogo|著作権やバナー メッセージを表示しません。|
|/svcutilConfig:\<configFile>|App.config ファイルの代わりに使用するカスタム構成ファイルを指定します。 これは、ツールの構成ファイルを変更せずに system.serviceModel 拡張を登録するために使用できます。|
|/target:\<output type>|ツールによって生成される出力を指定します。<br /><br /> 有効な値は、コード、メタデータ、または xmlSerializer です。<br /><br /> 短縮形 : `/t`|

### <a name="code-generation"></a>コード生成

Svcutil.exe は、メタデータ ドキュメントからサービス コントラクト、クライアント、およびデータ型のコードを生成できます。 これらのメタデータ ドキュメントは、永続ストレージにあるか、オンラインで取得できます。 オンライン取得は、WS-Metadata Exchange プロトコルまたは DISCO プロトコルに従います (詳細については、「メタデータのダウンロード」セクションを参照してください)。

定義済みの WSDL ドキュメントに基づいてサービスとデータ コントラクトを生成するために *SvcUtil.exe* ツールを使用できます。 /serviceContract スイッチを使用し、WSDL ドキュメントをダウンロードできるか見つけることができる URL またはファイルの場所を指定します。 こうすると、WSDL ドキュメントで定義されているサービスとデータ コントラクトが生成され、準拠サービスの実装に使用できます。 詳細については、「[方法: メタデータの取得および準拠サービスの実装をする](./feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)」を参照してください。

BasicHttpContextBinding エンドポイントを使用するサービスの場合は代わりに、*Svcutil.exe* によって、`allowCookies` 属性が `true` に設定された BasicHttpBinding が生成されます。 クッキーはサーバー側でのコンテキスト用に使用されます。 サービスでクッキーを使用するときにクライアント側でコンテキストを管理する場合は、コンテキスト バインディングを使用するように構成を手動で変更できます。

> [!CAUTION]
> Svcutil.exe は、WSDL またはサービスから受け取るポリシー ファイルに基づいてクライアントを生成します。 ユーザー プリンシパル名 (UPN) は、ユーザー名、"\@"、および完全修飾ドメイン名 (FQDN) を連結して生成されます。 ただし、Active Directory に登録されているユーザーの場合、この形式は無効であり、ツールが生成する UPN を使用すると、Kerberos 認証でエラーが発生し、エラー メッセージ "ログインに失敗しました" が表示されます。 この問題を解決するには、このツールが生成するクライアント ファイルを手動で修正する必要があります。

`svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>`

|引数|説明|
|--------------|-----------------|
|`epr`|WS-Metadata Exchange をサポートするサービス エンドポイントの WS-Addressing EndpointReference を含む XML ファイルへのパスです。 詳細については、「メタデータのダウンロード」セクションを参照してください。|
|`metadataDocumentPath`|コード (.wsdl、.xsd、.wspolicy、または .wsmex) にインポートするためのコントラクトを含むメタデータ ドキュメント (*wsdl* または *.xsd*) へのパス。<br /><br /> Svcutil は、メタデータにリモート URL を指定するときのインポートとインクルードに従います。 ただし、ローカル ファイル システムでメタデータ ファイルを処理する場合は、この引数にすべてのファイルを指定する必要があります。 この方法では Svcutil を、ネットワークの依存関係を持つことができないビルド環境で使用できます。 この引数には、ワイルドカード (*.xsd、\*.wsdl) を使用できます。|
|`url`|メタデータを提供するサービス エンドポイントの URL またはオンラインになっているメタデータ ドキュメントの URL。 これらのドキュメントの取得方法の詳細については、「メタデータのダウンロード」セクションを参照してください。|

|オプション|説明|
|------------|-----------------|
|/async|同期と非同期の両方のメソッド署名を生成します。<br /><br /> 既定 : 同期メソッド署名のみを生成します。<br /><br /> 短縮形: `/a`|
|/collectionType:\<type>|WCF クライアントのリスト コレクション型を指定します。<br/><br /> 既定値: コレクション型は System.Array です。 <br /><br /> 短縮形: `/ct`|
|/config:\<configFile>|生成される構成ファイルの名前を指定します。<br /><br /> 既定値: output.config|
|/dataContractOnly|データ コントラクト型に対してのみコードを生成します。 サービス コントラクト型は生成されません。<br /><br /> このオプションにはローカル メタデータ ファイルだけを指定する必要があります。<br /><br /> 短縮形: `/dconly`|
|/enableDataBinding|データ バインディングを有効にするために、すべてのデータ コントラクト型に <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装します。<br /><br /> 短縮形: `/edb`|
|/excludeType:\<type>|参照されるコントラクト型から除外する完全修飾またはアセンブリ修飾の型名を指定します。<br /><br /> このスイッチを個別の DLL から `/r` と共に使用する場合は、XSD クラスの完全名を参照します。<br /><br /> 短縮形: `/et`|
|/importXmlTypes|非データ コントラクト型を IXmlSerializable 型としてインポートするようにデータ コントラクト シリアライザーを構成します。|
|/internal|内部としてマークされるクラスを生成します。 既定 : パブリック クラスのみを生成します。<br /><br /> 短縮形: `/i`|
|/language:\<language>|コード生成に使用するプログラミング言語を指定します。 Machine.config ファイルに登録された言語名か、<xref:System.CodeDom.Compiler.CodeDomProvider> から継承するクラスの完全修飾名のいずれかを指定する必要があります。<br /><br /> 値 : c#、cs、csharp、vb、visualbasic、c++、cpp<br /><br /> 既定値: csharp<br /><br /> 短縮形 : `/l`|
|/mergeConfig|既存のファイルを上書きする代わりに、生成される構成ファイルを既存のファイルにマージします。|
|/messageContract|メッセージ コントラクト型を生成します。<br /><br /> 短縮形: `/mc`|
|/namespace:\<string,string>|WSDL または XML スキーマの targetNamespace から CLR 名前空間へのマッピングを指定します。 targetNamespace に '\*' を使用すると、マッピングを明示的に指定せずにすべての targetNamespace がその CLR 名前空間にマップされます。<br /><br /> メッセージ コントラクト名が操作名と競合しないようにするには、型参照を `::` で修飾するか、名前を一意にする必要があります。<br /><br /> 既定 : データ コントラクトのスキーマ ドキュメントのターゲット名前空間から派生します。 既定の名前空間は、生成される他のすべての型に使用されます。<br /><br /> 短縮形: `/n` **注:** XmlSerializer と共に使用する型を生成する場合、名前空間マッピングは 1 つだけサポートされます。 生成されるすべての型は、既定の名前空間または '*' によって指定された名前空間に含まれます。|
|/noConfig|構成ファイルを生成しません。|
|/noStdLib|標準ライブラリを参照しません。<br /><br /> 既定 : Mscorlib.dll と System.servicemodel.dll を参照します。|
|/out:\<file>|生成されるコードのファイル名を指定します。<br /><br /> 既定 : WSDL 定義名、WSDL サービス名、またはスキーマの 1 つのターゲット名前空間から派生します。<br /><br /> 短縮形 : `/o`|
|/reference:\<file path>|指定されたアセンブリの型を参照します。 クライアントの生成時に、このオプションを使用して、インポートするメタデータを表す型を含むアセンブリを指定します。<br /><br /> このスイッチを使用して、メッセージ コントラクト型と <xref:System.Xml.Serialization.XmlSerializer> 型は指定できません。<br /><br /> <xref:System.DateTimeOffset> が参照されている場合、新しい型を生成する代わりにこの型が使用されます。 アプリケーションが .NET Framework 3.5 を使用して記述されている場合、SvcUtil.exe では、自動的に <xref:System.DateTimeOffset> が参照されます。<br /><br /> 短縮形: `/r`|
|/serializable|シリアル化可能属性でマークされたクラスを生成します。<br /><br /> 短縮形: `/s`|
|/serviceContract|サービス コントラクトのコードのみを生成します。 クライアント クラスと構成は生成されません。<br /><br /> 短縮形: `/sc`|
|/serializer:Auto|シリアライザーを自動的に選択します。 これにより、データ コントラクト シリアライザーの使用を試み、失敗した場合には XmlSerializer を使用します。<br /><br /> 短縮形: `/ser`|
|/serializer:DataContractSerializer|シリアル化と逆シリアル化にデータ コントラクト シリアライザーを使用するデータ型を生成します。<br /><br /> 短縮形: `/ser:DataContractSerializer`|
|/serializer:XmlSerializer|シリアル化と逆シリアル化に <xref:System.Xml.Serialization.XmlSerializer> を使用するデータ型を生成します。<br /><br /> 短縮形: `/ser:XmlSerializer`|
|/targetClientVersion|アプリケーションが対象としている .NET Framework のバージョンを指定します。 有効値は `Version30` または `Version35` です。 既定値は `Version30` です。<br /><br /> 短縮形: `/tcv`<br /><br /> `Version30`: WinFX を使用するクライアントのコードを生成している場合は、`/tcv:Version30` を使用します。<br /><br /> `Version35`: .NET Framework 3.5 を使用するクライアントのコードを生成している場合は、`/tcv:Version35` を使用します。 `/tcv:Version35` スイッチを指定して `/async` を使用している場合は、イベントベースおよびコールバック/デリゲートベースの非同期メソッドが生成されます。 また、LINQ 対応のデータセットおよび <xref:System.DateTimeOffset> のサポートが有効になっています。|
|/wrapped|ラップされたパラメーターを含んでいるドキュメント リテラル スタイルのドキュメントに特別な大文字と小文字の規則が使用されるかどうかを制御します。 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) ツールと共に **/wrapped** スイッチを使用して、通常の大文字と小文字の規則を指定します。|

> [!NOTE]
> サービス バインディングがシステム指定のバインディング (「[システム指定のバインド](system-provided-bindings.md)」を参照) のいずれかであり、<xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> プロパティが `None` または `Sign` のどちらかに設定されている場合、Svcutil では、予期されるシステム指定の要素の代わりに [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) 要素を使用して構成ファイルが生成されます。 たとえば、サービスが、`<wsHttpBinding>` が `ProtectionLevel` に設定された `Sign` 要素を使用する場合、生成される構成には、バインディング セクションに `<customBinding>` の代わりに `<wsHttpBinding>` があります。 保護レベルの詳細については、「[保護レベルの理解](understanding-protection-level.md)」を参照してください。

### <a name="metadata-export"></a>メタデータのエクスポート

Svcutil.exe は、コンパイル済みアセンブリのサービス、コントラクト、およびデータ型のメタデータをエクスポートできます。 サービスのメタデータをエクスポートするには、`/serviceName` オプションを使用して、エクスポートするサービスを指定する必要があります。 アセンブリ内のすべてのデータ コントラクト型をエクスポートするには、`/dataContractOnly` オプションを使用する必要があります。 既定では、入力アセンブリのすべてのサービス コントラクトのメタデータがエクスポートされます。

`svcutil.exe [/t:metadata] [/serviceName:<serviceConfigName>] [/dataContractOnly] <assemblyPath>*`

|引数|説明|
|--------------|-----------------|
|`assemblyPath`|エクスポートされるサービス、コントラクト、またはデータ コントラクト型を格納するアセンブリへのパスを指定します。 標準のコマンド ライン ワイルドカードを使用して、複数のファイルを入力として指定できます。|

|オプション|説明|
|------------|-----------------|
|/serviceName:\<serviceConfigName>|エクスポートされるサービスの構成名を指定します。 このオプションを使用した場合、関連構成ファイルが存在する実行可能アセンブリを入力として渡す必要があります。 Svcutil.exe は、すべての関連構成ファイルからサービス構成を検索します。 構成ファイルが拡張型を含む場合、これらの型を含むアセンブリは GAC に存在するか、`/reference` オプションを使用して明示的に指定される必要があります。|
|/reference:\<file path>|指定したアセンブリを、型参照の解決に使用するアセンブリの集合に追加します。 サービスのエクスポートまたは検証に、構成に登録されているサードパーティ製拡張機能 (Behaviors、Bindings、および BindingElements) を使用している場合は、このオプションを使用して GAC に含まれていない拡張機能アセンブリを指定します。<br /><br /> 短縮形: `/r`|
|/dataContractOnly|データ コントラクト型に対してのみ機能します。 サービス コントラクトは処理されません。<br /><br /> このオプションにはローカル メタデータ ファイルだけを指定する必要があります。<br /><br /> 短縮形: `/dconly`|
|/excludeType:\<type>|エクスポートから除外する完全修飾またはアセンブリ修飾の型名を指定します。 このオプションは、エクスポートから型を除外するために、サービスのメタデータまたはサービス コントラクトのセットをエクスポートするときに使用できます。 このオプションは `/dconly` オプションとは併用できません。<br /><br /> 複数のサービスを含む単一のアセンブリが存在し、それぞれのサービスが同じ XSD 名の別のクラスを使用している場合は、このスイッチに XSD クラス名の代わりにサービス名を指定する必要があります。<br /><br /> XSD またはデータ コントラクト型はサポートされていません。<br /><br /> 短縮形: `/et`|

### <a name="service-validation"></a>サービスの検証

検証は、サービスをホストせずにサービス実装でエラーを検出するために使用できます。 `/serviceName` オプションを使用して、検証するサービスを指定する必要があります。

`svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*`

|引数|説明|
|--------------|-----------------|
|`assemblyPath`|検証するサービス型を格納するアセンブリへのパスを指定します。 アセンブリに、サービス構成を提供する関連構成ファイルが存在している必要があります。 標準のコマンド ライン ワイルドカードを使用して、複数のアセンブリを指定できます。|

|オプション|説明|
|------------|-----------------|
|/validate|`/serviceName` オプションによって指定されたサービス実装を検証します。 このオプションを使用した場合、関連構成ファイルが存在する実行可能アセンブリを入力として渡す必要があります。<br /><br /> 短縮形: `/v`|
|/serviceName:\<serviceConfigName>|検証するサービスの構成名を指定します。 Svcutil.exe は、すべての入力アセンブリのすべての関連構成ファイルからサービス構成を検索します。 構成ファイルが拡張型を含む場合、これらの型を含むアセンブリは GAC に存在するか、`/reference` オプションを使用して明示的に指定される必要があります。|
|/reference:\<file path>|指定したアセンブリを、型参照の解決に使用するアセンブリの集合に追加します。 サービスのエクスポートまたは検証に、構成に登録されているサードパーティ製拡張機能 (Behaviors、Bindings、および BindingElements) を使用している場合は、このオプションを使用して GAC に含まれていない拡張機能アセンブリを指定します。<br /><br /> 短縮形: `/r`|
|/dataContractOnly|データ コントラクト型に対してのみ機能します。 サービス コントラクトは処理されません。<br /><br /> このオプションにはローカル メタデータ ファイルだけを指定する必要があります。<br /><br /> 短縮形: `/dconly`|
|/excludeType:\<type>|検証から除外する完全修飾のまたはアセンブリ修飾の型名を指定します。<br /><br /> 短縮形: `/et`|

### <a name="metadata-download"></a>メタデータのダウンロード

Svcutil.exe を使用すると、実行中のサービスからメタデータをダウンロードして、ローカル ファイルに保存できます。 メタデータをダウンロードするには、`/t:metadata` オプションを指定する必要があります。 それ以外の場合は、クライアント コードが生成されます。 URL スキームが HTTP および HTTPS の場合、Svcutil.exe はメタデータの抽出に WS-Metadata Exchange および DISCO を使用します。 その他の URL スキームの場合、Svcutil.exe は WS-Metadata Exchange のみを使用します。

Svcutil は、メタデータを取得するために次のメタデータ要求を同時に発行します。

- 指定されたアドレスへの MEX (WS-Transfer) 要求

- 指定されたアドレスへの /mex 付きの MEX 要求

- 指定されたアドレスへの (ASMX から DiscoveryClientProtocol を使用した) DISCO 要求

既定では、Svcutil.exe は <xref:System.ServiceModel.Description.MetadataExchangeBindings> クラスに定義されているバインディングを使用して、MEX 要求を行います。 WS-Metadata Exchange で使用するバインディングを構成するには、IMetadataExchange コントラクトを使用するクライアント エンドポイントを構成に定義する必要があります。 これを定義できる場所は、Svcutil.exe の構成ファイルか、`/svcutilConfig` オプションを使用して指定された別の構成ファイルです。

`svcutil.exe /t:metadata  <url>* | <epr>`

|引数|説明|
|--------------|-----------------|
|`url`|メタデータを提供するサービス エンドポイントの URL またはオンラインになっているメタデータ ドキュメントの URL。|
|`epr`|WS-Metadata Exchange をサポートするサービス エンドポイントの WS-Addressing EndpointReference を含む XML ファイルへのパスです。|

### <a name="xmlserializer-type-generation"></a>XmlSerializer 型の生成

<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化できるデータ型を使用するサービスおよびクライアント アプリケーションは、実行時にこのようなデータ型のシリアル化コードを生成およびコンパイルします。このため、起動時のパフォーマンスが低下することがあります。

> [!NOTE]
> 事前生成済みシリアル化コードはクライアント アプリケーションでのみ使用できます。サービスでは使用できません。

Svcutil.exe は、必要な C# シリアル化コードをアプリケーションのコンパイル済みアセンブリから生成できるため、このようなアプリケーションの起動時のパフォーマンスが改善されます。 詳細については、「[方法: XmlSerializer を使用する WCF クライアント アプリケーションの起動時間を短縮する](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)」を参照してください。

> [!NOTE]
> Svcutil.exe は、入力アセンブリに存在するサービス コントラクトによって使用される型用のコードを生成します。

`svcutil.exe /t:xmlSerializer  <assemblyPath>*`

|引数|説明|
|--------------|-----------------|
|`assemblyPath`|サービス コントラクト型を格納するアセンブリへのパスを指定します。 シリアル化型は、各コントラクトのすべての Xml シリアル化可能型に対して生成されます。|

|オプション|説明|
|------------|-----------------|
|/reference:\<file path>|指定したアセンブリを、型参照の解決に使用するアセンブリの集合に追加します。<br /><br /> 短縮形: `/r`|
|/excludeType:\<type>|エクスポートや検証から除外する完全修飾のまたはアセンブリ修飾の型名を指定します。<br /><br /> 短縮形: `/et`|
|/out:\<file>|生成されるコードのファイル名を指定します。 このオプションは、複数のアセンブリが入力としてツールに渡される場合は無視されます。<br /><br /> 既定 : アセンブリ名から派生します。<br /><br /> 短縮形: `/o`|
|/UseSerializerForFaults|既定の <xref:System.Xml.Serialization.XmlSerializer> ではなく、<xref:System.Runtime.Serialization.DataContractSerializer> をエラーの読み書きに使用する必要があることを指定します。|

## <a name="examples"></a>例

次のコマンドにより、実行中のサービスまたはオンラインのメタデータ ドキュメントからクライアント コードが生成されます。

`svcutil http://service/metadataEndpoint`

次のコマンドにより、ローカルのメタデータ ドキュメントからクライアント コードが生成されます。

`svcutil *.wsdl *.xsd /language:C#`

次のコマンドにより、ローカルのスキーマ ドキュメントからデータ コントラクト型が Visual Basic で生成されます。

`svcutil /dconly *.xsd /language:VB`

次のコマンドにより、実行中のサービスからメタデータ ドキュメントがダウンロードされます。

`svcutil /t:metadata http://service/metadataEndpoint`

次のコマンドにより、アセンブリに含まれるサービス コントラクトと関連する型のメタデータ ドキュメントが生成されます。

`svcutil myAssembly.dll`

次のコマンドにより、アセンブリに含まれるサービス、すべての関連するサービス コントラクト、およびデータ型のメタデータ ドキュメントが生成されます。

`svcutil myServiceHost.exe /serviceName:myServiceName`

次のコマンドにより、アセンブリに含まれるデータ型のメタデータ ドキュメントが生成されます。

`svcutil myServiceHost.exe /dconly`

次のコマンドにより、サービス ホスティングが検証されます。

`svcutil /validate /serviceName:myServiceName myServiceHost.exe`

次のコマンドにより、アセンブリに含まれているサービス コントラクトによって使用される <xref:System.Xml.Serialization.XmlSerializer> 型用のシリアル化型を生成します。

`svcutil /t:xmlserializer myContractLibrary.exe`

## <a name="maximum-nametable-character-count-quota"></a>最大 Nametable 文字数のクォータ

svcutil を使用してサービスのメタデータを生成する場合、次のメッセージが表示されます。

エラー: `http://localhost:8000/somesservice/mex` からメタデータを取得できません。XML データの読み取り中に、最大 nametable 文字数のクォータ (16384) を超えました。 nametable は、XML 処理時に検出された文字列を格納するためのデータ構造です。反復されない要素名、属性名、および属性値が含まれた長い XML ドキュメントによってこのクォータがトリガーされることがあります。 このクォータを増やすには、XML リーダーの作成時に使用される XmlDictionaryReaderQuotas オブジェクトの MaxNameTableCharCount プロパティを変更してください。

このエラーの原因は、メタデータの要求時に大きな WSDL ファイルを返すサービスである可能性があります。 その結果、svcutil.exe ツールの文字のクォータを超えることになります。 この値は、サービス拒否 (dos) 攻撃を防止するために設定されています。 このクォータは、次の svcutil の構成ファイルを指定して増やすことができます。

次の構成ファイルは、svcutil のリーダーのクォータの設定方法を示しています。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <customBinding>
                <binding name="MyBinding">
                    <textMessageEncoding>
                        <readerQuotas maxDepth="2147483647" maxStringContentLength="2147483647"
                            maxArrayLength="2147483647" maxBytesPerRead="2147483647" maxNameTableCharCount="2147483647" />
                    </textMessageEncoding>
                    <httpTransport maxReceivedMessageSize="2147483647" maxBufferSize="2147483647" />
                </binding>
            </customBinding>
        </bindings>
        <client>
            <endpoint binding="customBinding" bindingConfiguration="MyBinding"
                contract="IMetadataExchange"
                name="http" />
        </client>
    </system.serviceModel>
</configuration>
```

svcutil.exe.config という名前の新しいファイルを作成し、XML のコード例をこのファイルにコピーします。 svcutil.exe と同じディレクトリにファイルを配置します。 次回 svcutil.exe が実行されると、新しい設定が適用されます。

## <a name="security-concerns"></a>セキュリティに関する注意事項

適切なアクセス制御リスト (ACL) を使用して、Svcutil.exe のインストール フォルダー、Svcutil.config、および `/svcutilConfig` によって示されるファイルを保護する必要があります。 これによって、悪質な拡張機能が登録されて実行されるのを防ぐことができます。

さらに、セキュリティの侵害を最小限に抑えるために、信頼できない拡張機能をシステムの一部として追加したり、信頼できないコード プロバイダーを Svcutil.exe で使用したりしないようにする必要があります。

また、現在のプロセスにサービス拒否を引き起こす可能性があるため、アプリケーションの中間層でツールを使用しないようにする必要があります。

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [方法: クライアントを作成する](how-to-create-a-wcf-client.md)

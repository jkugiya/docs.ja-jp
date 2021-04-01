---
title: C# を使用した JSON のシリアル化と逆シリアル化 - .NET
description: この概要では、.NET で JSON との間でシリアル化または逆シリアル化を行うための System.Text.Json 名前空間機能について説明します。
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 28f2b78de2533c659ea0fcf9d4990694dbfd411c
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584855"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a>.NET での JSON のシリアル化と逆シリアル化 (マーシャリングとマーシャリング解除) - 概要

`System.Text.Json` 名前空間は、JavaScript Object Notation (JSON) との間でのシリアル化と逆シリアル化の機能を提供します。

ライブラリの設計では、ハイ パフォーマンスと、高度な豊富なセットに対する少ないメモリ割り当てが強調されています。 組み込みの UTF-8 サポートによって、UTF-8 としてエンコードされた JSON テキストの読み取りと書き込みのプロセスが最適化されます。これは、web 上のデータおよびディスク上のファイルのための最も一般的なエンコードです。

ライブラリには、メモリ内のドキュメント オブジェクト モデル (DOM) を操作するためのクラスも用意されています。 この機能により、JSON ファイルまたは文字列内の要素に対する読み取り専用のランダムアクセスが可能になります。

Visual Basic コードから使用できるライブラリの部分には、いくつかの制限があります。 詳細については、「[Visual Basic のサポート](system-text-json-how-to.md#visual-basic-support)」をご覧ください。

## <a name="how-to-get-the-library"></a>ライブラリの入手方法

* ライブラリは、.NET Core 3.0 以降のバージョン用の共有フレームワークの一部として組み込まれています。
* それより前のバージョンの Framework では、[System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet パッケージをインストールします。 このパッケージで以下がサポートされます。

  * .NET Standard 2.0 以降のバージョン
  * .NET Framework 4.7.2 以降のバージョン
  * .NET Core 2.0、2.1、および 2.2

## <a name="additional-resources"></a>その他の技術情報

* [ライブラリを使用する方法](system-text-json-how-to.md)
* [JsonSerializerOptions インスタンスのインスタンスを作成する](system-text-json-configure-options.md)
* [大文字と小文字を区別しない一致を有効にする](system-text-json-character-casing.md)
* [プロパティの名前と値をカスタマイズする](system-text-json-customize-properties.md)
* [プロパティを無視する](system-text-json-ignore-properties.md)
* [無効な JSON を許可する](system-text-json-invalid-json.md)
* [オーバーフロー JSON の処理](system-text-json-handle-overflow.md)
* [参照を保持する](system-text-json-preserve-references.md)
* [変更できない型と非パブリック アクセサー](system-text-json-immutability.md)
* [ポリモーフィックなシリアル化](system-text-json-polymorphism.md)
* [Newtonsoft.Json から System.Text.Json に移行する](system-text-json-migrate-from-newtonsoft-how-to.md)
* [文字エンコードをカスタマイズする](system-text-json-character-encoding.md)
* [カスタム シリアライザーと逆シリアライザーを作成する](write-custom-serializer-deserializer.md)
* [JSON シリアル化のためのカスタム コンバーターの作成](system-text-json-converters-how-to.md)
* [DateTime および DateTimeOffset のサポート](../datetime/system-text-json-support.md)
* [System.Text.Json でサポートされているコレクション型](system-text-json-supported-collection-types.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
* [System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)

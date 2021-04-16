---
description: 各項目の詳細情報 <section> 要素
title: <section> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 7756f7ee3be2391a0d068708f3719083640b5595
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639940"
---
# <a name="section-element"></a>\<section> 要素

構成セクション宣言が含まれています。

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a>構文

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>必須属性

|           | 説明 |
| --------- | ----------- |
| **name**  | 構成セクションの名前を指定します。 |
| **type**  | 構成ファイルからセクションを読み取る構成セクション ハンドラー クラスの名前を指定します。 型の値には、"完全修飾セクション ハンドラー クラス名, 単純アセンブリ名" という構文があります。 単純アセンブリ名は、 *.dll* ファイル拡張子のないルート ファイル名です。 |

## <a name="optional-attributes"></a>省略可能な属性

次の属性は、ASP.NET アプリケーションにのみ適用されます。 構成システムでは、他のアプリケーションの種類に対してこれらの属性は無視されます。

|                     | 説明 |
| ------------------- | ----------- |
| **allowDefinition** | セクションを使用できる構成ファイルを指定します。 次のいずれかの値を使用します。<br><br>**すべての場所**<br>セクションをすべての構成ファイルで使用できるようにします。 既定値です。<br>**MachineOnly**<br>セクションを、コンピューターの構成ファイル (*Machine.config*) でのみ使用できるようにします。<br>**MachineToApplication**<br>セクションを、マシン構成ファイルまたはアプリケーション構成ファイルで使用できるようにします。 |
| **allowLocation**   | セクションを **\<location>** 要素内で使用できるようにするかどうかを決定します。 次のいずれかの値を使用します。<br><br>**true**<br>セクションを **\<location>** 要素内で使用できるようにします。 既定値です。<br>**false**<br>セクションを **\<location>** 要素内で使用できないようにします。 |

## <a name="parent-elements"></a>親要素

|     | 説明 |
| --- | ----------- |
| [ **\<configSections>** 要素](configsections-element-for-configuration.md) | 構成セクションと名前空間宣言が含まれています。 |
| [ **\<sectionGroup>** 要素](sectiongroup-element-for-configsections.md) | 構成セクションの名前空間を定義します。 |

> [!NOTE]
> **\<section>** 要素は **\<configSections>** または **\<sectionGroup>** のいずれかの子要素ですが、両方の子要素ではありません。

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>解説

構成セクションを宣言すると、基本的に構成ファイルの新しい要素が定義されます。 新しい要素には、構成セクション ハンドラー (つまり、<xref:System.Configuration.IConfigurationSectionHandler> インターフェイスを実装するクラス) によって読み取られる設定が格納されます。 定義するセクションの属性と子要素は、設定の読み取りに使用するセクション ハンドラーによって変わってきます。

*Machine.config* ファイルで構成セクション ハンドラーを宣言した場合は、**allowDefinition** 属性で特に指定されていない限り、そのコンピューター上の任意のアプリケーション構成ファイル内の構成セクションを使用できるようになります。

## <a name="example"></a>例

次の例は、構成セクションを定義し、そのセクションの設定を定義する方法を示しています。

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler"
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーション ディレクトリ レベルではない *Web.config* ファイルで使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイル スキーマ](index.md)

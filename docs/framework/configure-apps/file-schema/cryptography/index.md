---
description: '詳細情報: 暗号化設定スキーマ'
title: 暗号設定スキーマ
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: a7b3c020ed760aba24c9faf020281b7ad4bf3af7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730084"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="9af4f-103">暗号設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="9af4f-103">Cryptography Settings Schema</span></span>

<span data-ttu-id="9af4f-104">暗号設定スキーマには、アルゴリズムの表示名を、暗号化アルゴリズムを実装するクラスに割り当てる方法を指定する要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9af4f-104">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|<span data-ttu-id="9af4f-105">要素</span><span class="sxs-lookup"><span data-stu-id="9af4f-105">Element</span></span>|<span data-ttu-id="9af4f-106">説明</span><span class="sxs-lookup"><span data-stu-id="9af4f-106">Description</span></span>|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|<span data-ttu-id="9af4f-107">要素内の表示名へのマッピングを持つ暗号化クラスの一覧が含まれてい **\<nameEntry>** ます。</span><span class="sxs-lookup"><span data-stu-id="9af4f-107">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptoClass**>](cryptoclass-element.md)|<span data-ttu-id="9af4f-108">要素内のフレンドリ名へのマッピングを持つ暗号化クラスを格納 **\<nameEntry>** します。</span><span class="sxs-lookup"><span data-stu-id="9af4f-108">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|<span data-ttu-id="9af4f-109">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="9af4f-109">Contains cryptography settings.</span></span>|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|<span data-ttu-id="9af4f-110">表示名へのクラスのマッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="9af4f-110">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="9af4f-111">**\<mscorlib>** 暗号化設定の要素</span><span class="sxs-lookup"><span data-stu-id="9af4f-111">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="9af4f-112">要素が含まれてい **\<cryptographySettings>** ます。</span><span class="sxs-lookup"><span data-stu-id="9af4f-112">Contains the **\<cryptographySettings>** element.</span></span>|  
|[**\<nameEntry>**](nameentry-element.md)|<span data-ttu-id="9af4f-113">アルゴリズムの表示名にクラス名をマップして、1 つのクラスが多くの表示名を持つことを許可します。</span><span class="sxs-lookup"><span data-stu-id="9af4f-113">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[**\<oidEntry>**](oidentry-element.md)|<span data-ttu-id="9af4f-114">ASN.1 オブジェクト識別子 (OID) を表示名にマップします。</span><span class="sxs-lookup"><span data-stu-id="9af4f-114">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[**\<oidMap>**](oidmap-element.md)|<span data-ttu-id="9af4f-115">クラスへの ASN.1 OID マッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="9af4f-115">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9af4f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9af4f-116">See also</span></span>

- [<span data-ttu-id="9af4f-117">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="9af4f-117">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9af4f-118">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="9af4f-118">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)

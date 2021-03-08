---
title: Azure での .NET 開発の構成チェックリスト
description: Azure を使用して .net 開発を行うためにインストールしておく必要があるすべてのツールについて簡単にまとめます
ms.date: 1/1/2021
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 2f22f69ec99baf192d1cbdd28f884b7f47867389
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257981"
---
# <a name="net-on-azure-development-environment-checklist"></a>Azure での .NET 開発環境のチェックリスト

このチェックリストは、Azure を使用する .NET 開発用に開発環境が正しく構成されていることを確認するのに役立つように提供されています

## <a name="create-an-azure-account"></a>Azure アカウントの作成

Azure サービスにアクセスしたり、Azure でアプリケーションを実行したりするには、Azure アカウントが必要です。

* Visual Studio サブスクライバーである場合は、月単位の[無料の Azure クレジット](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)を毎月ご利用いただけます
* [無料の Azure アカウントを作成](https://azure.microsoft.com/free/dotnet/)し、$200 をクレジットで受け取り、12 か月間無料のサービスを選択します
* 会社の Azure 管理者によって割り当てられたアカウントを使用します

## <a name="configure-your-ide"></a>IDE を構成する

Visual Studio や Visual Studio Code などの一般的なツールには、IDE から直接 Azure を操作できる拡張機能が用意されています。

* Azure を使用する .NET 開発用に [Visual Studio を構成する](./configure-visual-studio.md)
* Azure を使用する .NET 開発用に [Visual Studio Code を構成する](./configure-vs-code.md)

## <a name="install-the-azure-cli"></a>Azure CLI のインストール

Azure portal を使用するだけでなく、Azure CLI をインストールして Azure リソースを作成および管理することもできます。

* [Windows での Azure CLI のインストール](/cli/azure/install-azure-cli-windows?tabs=azure-cli)
* [macOS での Azure CLI のインストール](/cli/azure/install-azure-cli-macos)
* [Linux 用の Azure CLI をインストールする](/cli/azure/install-azure-cli-linux)

## <a name="install-additional-tools-and-utilities"></a>その他のツールとユーティリティをインストールする

これらのその他のツールは、Azure を操作するときの生産性を高めるように設計されています。

* PowerShell スクリプトを使用して Azure リソースを作成および管理する予定の場合は、[Azure PowerShell をインストールします](/powershell/azure/install-az-ps)
* BLOB、キュー、テーブル、CosmosDB を含む Azure ストレージ リソースのデータをアップロード、ダウンロード、および管理するには、[Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) をインストールします。
* Azure SQL を操作する場合は、[Azure Data Studio をインストールします](/sql/azure-data-studio/download-azure-data-studio)

## <a name="bookmark-the-following-sites"></a>フォロー中のサイトをブックマークする

これらのサイトは、Azure の開発を行うときに頻繁に使用します。  クイック リファレンス用にブックマークします。

* Azure Portal - [https://portal.azure.com/](https://portal.azure.com/)
* Azure Cloud Shell - [https://shell.azure.com/](https://shell.azure.com/)

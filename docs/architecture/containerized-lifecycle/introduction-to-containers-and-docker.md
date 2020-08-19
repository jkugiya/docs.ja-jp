---
title: コンテナーと Docker の概要
description: Docker を使用することの主な利点を概説します。
ms.date: 04/15/2020
ms.openlocfilehash: 79b4752ef4d2f0aa6199414aea5cf4ef357c86d3
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915931"
---
# <a name="introduction-to-containers-and-docker"></a>コンテナーと Docker の概要

*コンテナリゼーションは、ソフトウェア開発のアプローチであり、アプリケーションまたはサービス、その依存関係、その構成 (デプロイ マニフェスト ファイルとして抽象化) がコンテナー イメージとしてパッケージ化されます。次に、コンテナー化アプリケーションをユニットとしてテストし、ホスト オペレーティング システム (OS) にコンテナー イメージ インスタンスとして展開することができます。*

輸送用のコンテナーが、内部の貨物に関係なく商品を船舶、列車、またはトラックによって輸送できるのと同様に、ソフトウェア コンテナーは、別のコードと依存関係を含めることができるソフトウェア デプロイの標準的なユニットとして機能します。 ソフトウェアをこのようにコンテナー化することで、開発者や IT プロフェッショナルは、ほとんどまたはまったく変更せずに環境全体にソフトウェアを展開できます。

コンテナーは、共有 OS 上で個々のアプリケーションも分離します。 コンテナー化アプリケーションは、さらに、OS (Linux または Windows) で実行されているコンテナー ホスト上で実行されます。 したがって、コンテナーは、仮想マシン (VM) のイメージよりも占有領域が大幅に小さくなります。

各コンテナーは、図 1-1 に示すように、Web アプリケーションまたはサービスの全体を実行することができます。 この例では、Docker ホストはコンテナー ホストであり、App1、App2、Svc1、Svc2 はコンテナー化されたアプリケーションまたはサービスです。

![VM またはサーバーで実行されている 4 つのコンテナーを示す図。](./media/introduction-to-containers-and-docker/multiple-containers-single-host.png)

**(図 1-1)** 。 コンテナー ホストで実行されている複数のコンテナー

コンテナリゼーションから得られるもう 1 つの利点はスケーラビリティです。 短期的なタスク用の新しいコンテナーを作成することでに簡単にスケール アウトできます。 アプリケーションの観点から、イメージのインスタンス化 (コンテナーの作成) は、サービスまたは Web アプリのようなプロセスのインスタンス化に似ています。 ただし、信頼性のために、同じイメージの複数のインスタンスを複数のホスト サーバーで実行するときには通常、各コンテナー (イメージのインスタンス) を異なるフォールト ドメイン内の別のホスト サーバーまたは VM で実行します。

つまり、コンテナーには、アプリケーション ライフサイクル ワークフロー全体にわたり、分離、移植性、機敏性、スケーラビリティ、コントロールの利点があります。 最も重要な利点は、開発と運用間で提供される環境の分離です。

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](what-is-docker.md)
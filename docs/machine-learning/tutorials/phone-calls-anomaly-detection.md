---
title: 'チュートリアル: 通話の異常を検出する'
description: 時系列データの異常検出アプリケーションを構築する方法について学習します。 このチュートリアルでは、Visual Studio 2019 の C# を使って .NET Core コンソール アプリケーションを作成します。
ms.date: 12/04/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 52ce0a60c91ef7a82f7ef1a0709701302b9e11d9
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874772"
---
# <a name="tutorial-detect-anomalies-in-time-series-with-mlnet"></a>チュートリアル: ML.NET で時系列の異常を検出する

時系列データの異常検出アプリケーションを構築する方法について学習します。 このチュートリアルでは、Visual Studio 2019 の C# を使って .NET Core コンソール アプリケーションを作成します。

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
>
> * データを読み込む
> * 時系列の期間を検出する
> * 定期的な時系列の異常を検出する

このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/PhoneCallsAnomalyDetection) リポジトリで確認できます。

## <a name="prerequisites"></a>必須コンポーネント

* [Visual Studio 2019 バージョン 16.7.8 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)が ".NET Core クロスプラットフォーム開発" ワークロードと共にインストールされている。

* [phone-calls.csv データセット](https://github.com/dotnet/machinelearning-samples/blob/main/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv)。

## <a name="create-a-console-application"></a>コンソール アプリケーションの作成

1. "PhoneCallsAnomalyDetection" という **C# .NET Core コンソール アプリケーション** を作成します。

2. データ セット ファイルを保存するために、プロジェクトに *Data* という名前のディレクトリを作成します。

3. **Microsoft.ML NuGet パッケージ** をインストールします。

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。 [パッケージ ソース] として [nuget.org] を選択します。[参照] タブを選択し、「**Microsoft.ML**」を検索し、 **[インストール]** ボタンを選択します。 **[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。 **Microsoft.ML.TimeSeries** についてもこれらの手順を繰り返します。

4. *Program.cs* の先頭に次の `using` ステートメントを追加します。

    [!code-csharp[AddUsings](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>データをダウンロードする

1. データセットをダウンロードし、以前に作成した *Data* フォルダーに保存します。

    [*phone-calls.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/main/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv) を右クリックし、[名前を付けてリンク (または対象) を保存] を選択します

     \*.csv ファイルを *Data* フォルダーに保存したことを確認します。または他の場所に保存した後に、\*.csv ファイルを *Data* フォルダーに移動します。

2. ソリューション エクスプローラーで、\*.csv ファイルを右クリックし、 **[プロパティ]** を選択します。 **[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。

次の表は、\*.csv ファイルのデータのプレビューです。

| timestamp  | value |
|--------|--------------|
| 2018/9/3  | 36.69670857  |
| 2018/9/4  | 35.74160571  |
| .....  | .....  |
| 2018/10/3  | 34.49893429  |
| ...    | ....   |

このファイルは時系列を表します。 ファイルの各行はデータ ポイントです。 各デー タポイントには、1 日の通話数を表す 2 つの属性 (つまり、`timestamp` と `value`) があります。 通話数は非秘密度に変換されます。

### <a name="create-classes-and-define-paths"></a>クラスを作成してパスを定義する

次に、入力クラスと予測クラスのデータ構造を定義します。

プロジェクトに新しいクラスを追加します。

1. **ソリューション エクスプローラー** で、プロジェクトを右クリックして、 **[追加]、[新しいアイテム]** の順に選びます。

2. **[新しい項目の追加]** ダイアログ ボックスで、 **[クラス]** を選択し、 **[名前]** フィールドを *PhoneCallsData.cs* に変更します。 次に **[追加]** を選択します。

   コード エディターで *PhoneCallsData.cs* ファイルが開きます。

3. 次の `using` ステートメントを *PhoneCallsData.cs* の先頭に追加します。

   ```csharp
   using Microsoft.ML.Data;
   ```

4. 既存のクラス定義を削除し、`PhoneCallsData` と `PhoneCallsPrediction` の 2 つのクラスを含む次のコードを *PhoneCallsData.cs* ファイルに追加します。

    [!code-csharp[DeclareTypes](./snippets/phone-calls-anomaly-detection/csharp/PhoneCallsData.cs#DeclareTypes "Declare data record types")]

    `PhoneCallsData` は入力データ クラスを指定します。 [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) 属性は、データセット内のどの列 (列インデックス) を読み込むかを指定します。 これには、データ ファイル内の同じ属性に対応する `timestamp` と `value` の 2 つの属性があります。

    `PhoneCallsPrediction` では予測データ クラスを指定します。 SR-CNN 検出の場合、予測は指定された[検出モード](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode)によって異なります。 このサンプルでは、`AnomalyAndMargin` モードを選択します。 出力には 7 つの列が含まれています。 ほとんどの場合、`IsAnomaly`、`ExpectedValue`、`UpperBoundary`、`LowerBoundary` の情報で十分です。 これらを見れば、ポイントが異常であるかどうか、そのポイントの予期される値およびそのポイントの下限/上限領域がわかります。

5. `Main` メソッドのすぐ上にある行に次のコードを追加して、データ ファイルへのパスを指定します。

    [!code-csharp[Declare global variables](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a>Main で変数を初期化する

1. `Main` メソッドの `Console.WriteLine("Hello World!")` の行は、`mlContext` 変数を宣言して初期化する次のコードに置き換えます。

    [!code-csharp[CreateMLContext](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    [MLContext クラス](xref:Microsoft.ML.MLContext)は、すべての ML.NET 操作の開始点で、`mlContext` を初期化することで、モデル作成ワークフローのオブジェクト間で共有できる新しい ML.NET 環境が作成されます。 これは Entity Framework における `DBContext` と概念的には同じです。

### <a name="load-the-data"></a>データを読み込む

ML.NET 内のデータは、[IDataView クラス](xref:Microsoft.ML.IDataView)として表されます。 `IDataView` は、表形式のデータ (数値とテキスト) を表すための柔軟で効率的な方法です。 データはテキスト ファイルから、または他のソース (SQL データベースやログ ファイルなど) から `IDataView` オブジェクトに読み込むことができます。

1. `Main` メソッドの次の行として次のコードを追加します。

    [!code-csharp[LoadData](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) は、データ スキーマを定義し、ファイルを読み取ります。 データ パス変数を取得して、`IDataView` を返します。

## <a name="time-series-anomaly-detection"></a>時系列の異常検出

時系列の異常検出は、時系列データの異常値 (指定された入力の時系列上で、動作が予期されたものではない点、つまり、"おかしい" 点) を検出するプロセスです。 これらの異常は通常、問題領域の対象のいくつかのイベントを示しています。つまり、ユーザー アカウントに対するサイバー攻撃、停電、サーバー上での RPS のバースト、メモリ リークなどです。

時系列の異常を検出するには、まずその系列の期間を確認する必要があります。 その後、時系列を `Y = T + S + R` として複数のコンポーネントに分解できます。ここで、`Y` は元の系列、`T` は傾向コンポーネント、`S` は季節コンポーネント、`R` は系列の残りのコンポーネントです。 この手順は[分解](https://en.wikipedia.org/wiki/Decomposition_of_time_series)と呼ばれます。 最後に、異常を見つけるために残りのコンポーネントに対して検出が行われます。 ML.NET では、SR-CNN アルゴリズムは、時系列の異常を検出するための Spectral Residual (SR) および Convolutional Neural Network (CNN) に基づく高度な新しいアルゴリズムです。 このアルゴリズムの詳細については、「[Time-Series Anomaly Detection Service at Microsoft](https://arxiv.org/pdf/1906.03821.pdf)」(Microsoft の時系列異常検出サービス) を参照してください。

このチュートリアルで、2 つの関数を使用してこれらの手順を完了できることがわかります。

## <a name="detect-period"></a>検出期間

最初の手順では、`DetectSeasonality` 関数を呼び出して、系列の期間を確認します。

### <a name="create-the-detectperiod-method"></a>DetectPeriod メソッドを作成する

1. 次のコードを使用して、`Main` メソッドのすぐ下に `DetectPeriod` メソッドを作成します。

    ```csharp
    static void DetectPeriod(MLContext mlContext, IDataView phoneCalls)
    {

    }
    ```

2. 期間を検出するには、<xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality%2A> 関数を使用します。 それを次のコードを使用して `DetectPeriod` メソッドに追加します。

    [!code-csharp[DetectSeasonality](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectSeasonality)]

3. `DetectPeriod` メソッドの次のコード行として以下を追加し、期間の値を表示します。

    [!code-csharp[DisplayPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayPeriod)]

4. 次の `DetectPeriod` メソッドに対する呼び出しを `Main` メソッドに追加します。

    [!code-csharp[CallDetectPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectPeriod)]

### <a name="period-detection-results"></a>期間の検出結果

アプリケーションを実行します。 結果は以下のようになるはずです。

```console
Period of the series is: 7.
```

## <a name="detect-anomaly"></a>異常を検出する

この手順では、<xref:Microsoft.ML.TimeSeriesCatalog.DetectEntireAnomalyBySrCnn%2A> メソッドを使用して異常を見つけます。

### <a name="create-the-detectanomaly-method"></a>DetectAnomaly メソッドを作成する

1. 次のコードを使用して、`DetectPeriod` メソッドのすぐ下に `DetectAnomaly` メソッドを作成します。

    ```csharp
    static void DetectAnomaly(MLContext mlContext, IDataView phoneCalls, int period)
    {

    }
    ```

2. 次のコードを使用して、`DetectAnomaly` メソッドに <xref:Microsoft.ML.TimeSeries.SrCnnEntireAnomalyDetectorOptions> を設定します。

    [!code-csharp[SetupSrCnnParameters](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#SetupSrCnnParameters)]

3. `DetectAnomaly` メソッドに次のコード行を追加することで、SR-CNN アルゴリズムで異常を検出します。

    [!code-csharp[DetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectAnomaly)]

4. 次のコードで [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) メソッドを使用して、表示をより簡単にするために出力データ ビューを厳密に型指定された `IEnumerable` に変換します。

    [!code-csharp[CreateEnumerableForResult](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateEnumerableForResult)]

5. `DetectAnomaly` メソッドの次の行として次のコードを使用して、表示ヘッダーを作成します。

    [!code-csharp[DisplayHeader](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayHeader)]

    変化点の検出結果には、次の情報が表示されます。

    * `Index` は各点のインデックスです。
    * `Anomaly` は、各点が異常として検出されたかどうかを示すインジケーターです。
    * `ExpectedValue` は各点の推定値です。
    * `LowerBoundary` は、各点を異常でないと見なせる最小値です。
    * `UpperBoundary` は、各点を異常でないと見なせる最大値です。

6. 次のコードを使用して `predictions` `IEnumerable` を反復処理し、結果を表示します。

    [!code-csharp[DisplayAnomalyDetectionResults](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayAnomalyDetectionResults)]

7. 次の `DetectAnomaly` メソッドに対する呼び出しを `Main` メソッドに追加します。

    [!code-csharp[CallDetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectAnomaly)]

## <a name="anomaly-detection-results"></a>異常検出の結果

アプリケーションを実行します。 結果は以下のようになるはずです。 処理中にメッセージが表示されます。 警告または処理メッセージが表示されることがあります。 わかりやすくするために、一部のメッセージは次の結果から削除してあります。

```console
Detect period of the series
Period of the series is: 7.
Detect anomaly points in the series
Index   Data    Anomaly AnomalyScore    Mag     ExpectedValue   BoundaryUnit    UpperBoundary   LowerBoundary
0,0,36.841787256739266,41.14206982401966,32.541504689458876
1,0,35.67303618137362,39.97331874865401,31.372753614093227
2,0,34.710132999891826,39.029491313022824,30.390774686760828
3,0,33.44765248883495,37.786086547816545,29.10921842985335
4,0,28.937110922276364,33.25646923540736,24.61775260914537
5,0,5.143895892785781,9.444178460066171,0.843613325505391
6,0,5.163325228419392,9.463607795699783,0.8630426611390014
7,0,36.76414836240396,41.06443092968435,32.46386579512357
8,0,35.77908590657007,40.07936847385046,31.478803339289676
9,0,34.547259536635245,38.847542103915636,30.246976969354854
10,0,33.55193524820608,37.871293561337076,29.23257693507508
11,0,29.091800129624648,33.392082696905035,24.79151756234426
12,0,5.154836630338823,9.455119197619213,0.8545540630584334
13,0,5.234332502492464,9.534615069772855,0.934049935212073
14,0,36.54992549471526,40.85020806199565,32.24964292743487
15,0,35.79526470980883,40.095547277089224,31.494982142528443
16,0,34.34099013096804,38.64127269824843,30.040707563687647
17,0,33.61201516582131,37.9122977331017,29.31173259854092
18,0,29.223563320561812,33.5238458878422,24.923280753281425
19,0,5.170512168851533,9.470794736131923,0.8702296015711433
20,0,5.2614938889462834,9.561776456226674,0.9612113216658926
21,0,36.37103858487317,40.67132115215356,32.07075601759278
22,0,35.813544599026855,40.113827166307246,31.513262031746464
23,0,34.05600492733225,38.356287494612644,29.755722360051863
24,0,33.65828319077884,37.95856575805923,29.358000623498448
25,0,29.381125690882463,33.681408258162854,25.080843123602072
26,0,5.261543539820418,9.561826107100808,0.9612609725400283
27,0,5.4873712582971805,9.787653825577571,1.1870886910167897
28,1,36.504694001629254,40.804976568909645,32.20441143434886  <-- alert is on, detected anomaly
...
```

おめでとうございます! これで、定期的な系列の期間と異常を検出するための機械学習モデルが正常に構築されました。

このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/PhoneCallsAnomalyDetection) リポジトリで確認できます。

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
>
> * データを読み込む
> * 時系列データの期間を検出する
> * 時系列データの異常を検出する

## <a name="next-steps"></a>次の手順

Machine Learning サンプルの GitHub リポジトリを確認し、Power Consumption Anomaly Detection サンプルを調べてください。
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples GitHub リポジトリ](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)

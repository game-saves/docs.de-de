---
title: Einzelvorhersage mit PredictionEngine – ML.NET
description: Lernen Sie, wie Sie mit ML.NET-PredictionEngine Einzelvorhersagen treffen.
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 328067816be37c9490ae71974e3f6da4ae079f25
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092032"
---
# <a name="use-the-predictionengine-to-make-one-prediction-at-a-time---mlnet"></a>Einzelvorhersage mit PredictionEngine – ML.NET 

Da jedes ML.NET-Modell ein Transformator ist, verwenden Sie `model.Transform`, um das Modell auf `DataView` anzuwenden und Vorhersagen zu treffen. 

Ein eher typischer Fall ist jedoch, wenn kein „Dataset“ vorliegt, für das Sie eine Vorhersage treffen möchten, aber Sie stattdessen jeweils ein Beispiel erhalten. Beispielsweise führen Sie das Modell im Rahmen Ihrer ASP.NET-Website aus und müssen eine Vorhersage für eine eingehende HTTP-Anforderung treffen.

Die `PredictionEngine` führt jeweils ein Beispiel über die Vorhersagepipeline aus.

So sieht das vollständige Beispiel mithilfe eines vorgefertigten Iris-Datasetmodells aus:

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// First, we define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(
    columns: new TextLoader.Column[]
    {
        // The four features of the Iris dataset will be grouped together as one Features column.
        new TextLoader.Column("SepalLength",DataKind.R4,0),
        new TextLoader.Column("SepalWidth",DataKind.R4,1),
        new TextLoader.Column("PetalLength",DataKind.R4,2),
        new TextLoader.Column("PetalWidth",DataKind.R4,3),
        // Label: kind of iris.
        new TextLoader.Column("Label",DataKind.TX,4)
    },
    separatorChar: ',',
    hasHeader: true
);

// Retrieve the training data.
var trainData = reader.Read(irisDataPath);

// Build the training pipeline.
var pipeline =
    // Concatenate all the features together into one column 'Features'.
    mlContext.Transforms.Concatenate("Features", "SepalLength", "SepalWidth", "PetalLength", "PetalWidth")
    // Note that the label is text, so it needs to be converted to key.
    .Append(mlContext.Transforms.Categorical.MapValueToKey("Label"), TransformerScope.TrainTest)
    // Use the multi-class SDCA model to predict the label using features.
    .Append(mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent())
    // Apply the inverse conversion from 'PredictedLabel' column back to string value.
    .Append(mlContext.Transforms.Conversion.MapKeyToValue(("Data", "PredictedLabel")));

// Train the model.
var model = pipeline.Fit(trainData);
```

Um das [Schemaverständnis](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md) für die Vorhersage zu verwenden, definieren Sie wie folgt ein Paar von Klassen:

```csharp
private class IrisInput
{
    // Unfortunately, we still need the dummy 'Label' column to be present.
    [ColumnName("Label")]
    public string IgnoredLabel { get; set; }
    public float SepalLength { get; set; }
    public float SepalWidth { get; set; }
    public float PetalLength { get; set; }
    public float PetalWidth { get; set; }
}

private class IrisPrediction
{
    [ColumnName("Data")]
    public string PredictedClass { get; set; }
}
```

Der Vorhersagecode sieht nun wie folgt aus:

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Use the model for one-time prediction.
// Make the prediction function object. Note that, on average, this call takes around 200x longer
// than one prediction, so you might want to cache and reuse the prediction engine, instead of
// creating one per prediction.
var predictionEngine = model.CreatePredictionEngine<IrisInput, IrisPrediction>(mlContext);

// Obtain the prediction. Remember that 'Predict' is not reentrant. If you want to use multiple threads
// for simultaneous prediction, make sure each thread is using its own PredictionEngine.
var prediction = predictionEngine.Predict(new IrisInput
{
    SepalLength = 4.1f,
    SepalWidth = 0.1f,
    PetalLength = 3.2f,
    PetalWidth = 1.4f
});
```

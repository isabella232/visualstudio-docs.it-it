---
title: Creazione SharePoint pacchetti della soluzione | Microsoft Docs
description: Creare e personalizzare pacchetti di distribuzione per SharePoint soluzioni usando Progettazione pacchetti. Esplorare gli strumenti di creazione pacchetti, le opzioni di progettazione e la struttura di cartelle.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: f89bb6344ce7be130f0dc4e7d430327cc139175fa4298539855d5b37ec65f01c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425544"
---
# <a name="create-sharepoint-solution-packages"></a>Creare SharePoint pacchetti della soluzione
  Con Progettazione pacchetti è possibile creare e personalizzare i pacchetti di distribuzione. Ad esempio, è possibile aggiungere SharePoint di progetto e funzionalità, reimpostare il server IIS, impostare ambiti di attivazione delle funzionalità e identificare le dipendenze delle funzionalità. La finestra di progettazione genera anche un manifesto, un file XML che descrive ogni pacchetto.

## <a name="packaging-tools"></a>Strumenti per la creazione di pacchetti
 È possibile usare Progettazione **pacchetti per** personalizzare il pacchetto e generare il manifesto. È possibile includere SharePoint di progetto, configurare se il server Web deve essere reimpostato e impostare il tipo di server di distribuzione. Per altre informazioni, [vedere Procedura: Aggiungere e rimuovere funzionalità ed](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)elementi in un pacchetto tramite Progettazione pacchetti.

 In alternativa, è possibile usare **Packaging Explorer** per modificare le funzionalità e gli elementi nel file del pacchetto ( con *estensione wsp*). Per altre informazioni, vedere Procedura: Aggiungere e rimuovere funzionalità ed elementi [in un pacchetto tramite Packaging Explorer.](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)

 È possibile usare Visual Studio e MSBuild creare file di pacchetto ( con estensione *wsp*) per distribuire la SharePoint soluzione. Questo processo genera i file manifesto necessari per SharePoint distribuzione. Per altre informazioni, [vedere Procedura: Creare un pacchetto SharePoint soluzione usando MSBuild attività](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Opzioni di Progettazione pacchetti
 Nella tabella seguente vengono illustrate le proprietà che è possibile personalizzare in SharePoint pacchetti con Progettazione **pacchetti.**

|Proprietà di Progettazione pacchetti|Descrizione dell'impostazione predefinita|
|-------------------------------|------------------------------------|
|Nome|Obbligatorio. Il nome predefinito del pacchetto è impostato su *ProjectName.*|
|Reimpostare WebServer|facoltativo. Selezionare se si vuole riavviare il server Web dopo l'installazione del file con estensione *wsp* nel server SharePoint server.|
|Tipo di server di distribuzione|facoltativo. Rappresenta il tipo di server che ospita il pacchetto. Se non impostata, il valore predefinito sarà WebFrontEnd.<br /><br /> ApplicationServer: descrive un server che ospita i servizi.<br /><br /> WebFrontEnd: descrive un server che ospita siti Web.|
|Elementi nella soluzione|Tutti SharePoint elementi di progetto e funzionalità che possono essere aggiunti al pacchetto.|
|Elementi nel pacchetto|facoltativo. Tutti SharePoint elementi e funzionalità che si desidera distribuire nel pacchetto.|

## <a name="configure-the-packaging-process"></a>Configurare il processo di creazione del pacchetto
 Dopo aver sviluppato le soluzioni SharePoint in Visual Studio, è possibile personalizzare il modo in cui vengono creati i pacchetti dei progetti.

 La tabella seguente illustra le due MSBuild che è possibile usare per personalizzare la modalità di creazione del file con estensione *wsp.*

|Destinazione|Descrizione|
|------------|-----------------|
|BeforeLayout|Destinazione che esegue attività immediatamente prima che i file siano copiati in una directory intermedia. È possibile modificare i file prima di creare un file di pacchetto (*con estensione wsp*).|
|AfterLayout|Destinazione che esegue le attività immediatamente dopo la copia dei file in una directory intermedia.|

 Per altre informazioni, [vedere Procedura: Personalizzare un pacchetto SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)soluzione usando MSBuild destinazioni .

## <a name="packaging-architecture"></a>Architettura dei pacchetti
 I passaggi seguenti si verificano quando si crea un pacchetto SharePoint (*.wsp*) in Visual Studio.

1. Le funzionalità e i pacchetti vengono convalidati per assicurarsi che la struttura fisica e semantica del pacchetto sia corretta.

2. Le funzionalità, gli elementi di progetto e i file di pacchetto nel pacchetto vengono enumerati. I file manifesto per i pacchetti e le funzionalità vengono trasformati in modo da includere tutte le informazioni necessarie per la distribuzione e l'attivazione. I token vengono sostituiti con il valore completo.

3. Viene eseguita la destinazione MSBuild beforeLayout personalizzabile. È possibile creare questo passaggio per apportare modifiche personalizzate al pacchetto prima di creare il file con estensione *wsp.*

4. I file enumerati vengono copiati in una directory intermedia.

5. Viene eseguita la destinazione MSBuild afterlayout personalizzabile. È possibile creare questo passaggio per apportare modifiche personalizzate al pacchetto prima di creare il file con estensione *wsp.*

6. I file nella directory intermedia vengono aggiunti al file *con estensione wsp.*

## <a name="package-folder-structure"></a>Struttura delle cartelle del pacchetto
 Quando si crea un pacchetto SharePoint progetto, viene creato *automaticamente* un file con estensione wsp nella *cartella \\ \<BuildConfiguration> SolutionFolder\bin.* Ad esempio, se la soluzione si trova in *C:\Visual Studio 2013\Projects\ListDefinition1* e la configurazione della build è impostata su Release, il file con estensione *wsp* si trova in *C:\Visual Studio 2013\Projects\ListDefinition1\bin\Release.*

## <a name="see-also"></a>Vedi anche
- [Procedura: Personalizzare un pacchetto SharePoint soluzione](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Procedura: Aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [Procedura: Creare un pacchetto SharePoint soluzione usando MSBuild attività](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Procedura: Creare un pacchetto SharePoint soluzione usando MSBuild attività](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Procedura: Personalizzare un pacchetto SharePoint soluzione usando MSBuild destinazione](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)

---
title: Creazione di pacchetti della soluzione SharePoint | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b250be3b61cdfc524f049f952f0cf7e65f1c295a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "74876064"
---
# <a name="create-sharepoint-solution-packages"></a>Creare pacchetti della soluzione SharePoint
  Con progettazione pacchetti è possibile creare e personalizzare i pacchetti di distribuzione. Ad esempio, è possibile aggiungere elementi e funzionalità di progetto SharePoint, reimpostare il server IIS, impostare gli ambiti di attivazione della funzionalità e identificare le dipendenze delle funzionalità. La finestra di progettazione genera inoltre un manifesto, un file XML che descrive ogni pacchetto.

## <a name="packaging-tools"></a>Strumenti per la creazione di pacchetti
 È possibile utilizzare **Progettazione pacchetti** per personalizzare il pacchetto e generare il manifesto. È possibile includere gli elementi del progetto SharePoint, configurare se il server Web deve essere reimpostato e impostare il tipo di server di distribuzione. Per ulteriori informazioni, vedere [procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

 In alternativa, è possibile usare **Esplora pacchetti** per modificare le funzionalità e gli elementi nel file del pacchetto (con*estensione wsp*). Per altre informazioni, vedere [procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto con Esplora pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

 È possibile utilizzare Visual Studio e MSBuild per creare file di pacchetto (con*estensione wsp*) per distribuire la soluzione SharePoint. Questo processo genera i file manifesto necessari per la distribuzione di SharePoint. Per altre informazioni, vedere [procedura: creare un pacchetto della soluzione SharePoint usando le attività di MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Opzioni di progettazione pacchetti
 Nella tabella seguente vengono illustrate le proprietà che è possibile personalizzare nei pacchetti di SharePoint con **Progettazione pacchetti**.

|Proprietà progettazione pacchetti|Descrizione dell'impostazione predefinita|
|-------------------------------|------------------------------------|
|Nome|Obbligatorio. Il nome predefinito del pacchetto è impostato su *NomeProgetto*.|
|Reimposta server Web|facoltativo. Selezionare se si desidera riavviare il server Web dopo l'installazione del file con *estensione wsp* nel server SharePoint.|
|Tipo di server di distribuzione|facoltativo. Rappresenta il tipo di server che ospita il pacchetto. Se non è impostato, il valore predefinito è WebFrontEnd.<br /><br /> ApplicationServer: descrive un server che ospita i servizi.<br /><br /> WebFrontEnd: descrive un server che ospita siti Web.|
|Elementi nella soluzione|Tutte le funzionalità e gli elementi del progetto SharePoint che è possibile aggiungere al pacchetto.|
|Elementi nel pacchetto|facoltativo. Tutti gli elementi e le funzionalità di SharePoint che si desidera distribuire nel pacchetto.|

## <a name="configure-the-packaging-process"></a>Configurare il processo di creazione del pacchetto
 Dopo aver sviluppato le soluzioni SharePoint in Visual Studio, è possibile personalizzare il modo in cui vengono creati i pacchetti dei progetti.

 La tabella seguente illustra le due destinazioni di MSBuild che è possibile usare per personalizzare la modalità di creazione del file con *estensione wsp* .

|Destinazione|Descrizione|
|------------|-----------------|
|BeforeLayout|Destinazione che esegue le attività immediatamente prima che i file vengano copiati in una directory intermedia. È possibile modificare i file prima di creare un file di pacchetto (con*estensione wsp*).|
|AfterLayout|Destinazione che esegue le attività immediatamente dopo la copia dei file in una directory intermedia.|

 Per ulteriori informazioni, [procedura: personalizzare un pacchetto della soluzione SharePoint tramite destinazioni MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).

## <a name="packaging-architecture"></a>Architettura di creazione pacchetti
 I passaggi seguenti si verificano quando si crea un pacchetto di SharePoint (con*estensione wsp*) in Visual Studio.

1. Le funzionalità e i pacchetti vengono convalidati per assicurarsi che la struttura fisica e semantica del pacchetto sia corretta.

2. Le funzionalità, gli elementi del progetto e i file di pacchetto nel pacchetto vengono enumerati. I file manifesto per i pacchetti e le funzionalità sono trasformati in modo da includere tutte le informazioni necessarie per la distribuzione e l'attivazione. I token vengono sostituiti con il valore completo.

3. Viene eseguita la destinazione di MSBuild BeforeLayout personalizzabile. È possibile creare questo passaggio per apportare modifiche personalizzate al pacchetto prima di creare il file con estensione *WSP* .

4. I file enumerati vengono copiati in una directory intermedia.

5. Viene eseguita la destinazione di MSBuild AfterLayout personalizzabile. È possibile creare questo passaggio per apportare modifiche personalizzate al pacchetto prima di creare il file con estensione *WSP* .

6. I file nella directory intermedia vengono aggiunti al file con estensione *WSP* .

## <a name="package-folder-structure"></a>Struttura delle cartelle del pacchetto
 Quando si crea il pacchetto del progetto SharePoint, viene creato un file con *estensione wsp* nella *cartella \\ \<BuildConfiguration> SolutionFolder\bin* Ad esempio, se la soluzione si trova in *C:\Visual Studio 2013 \ Projects\ListDefinition1* e la configurazione della build è impostata su Release, il file con *estensione wsp* si trova in *C:\Visual Studio 2013 \ Projects\ListDefinition1\bin\Release*.

## <a name="see-also"></a>Vedere anche
- [Procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [Procedura: creare un pacchetto della soluzione SharePoint tramite le attività MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Procedura: creare un pacchetto della soluzione SharePoint tramite le attività MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Procedura: personalizzare un pacchetto della soluzione SharePoint tramite destinazioni MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)

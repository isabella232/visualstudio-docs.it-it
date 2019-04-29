---
title: Creazione di pacchetti e distribuzione delle soluzioni SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c187865518c9556d63d9e5e632ec5c658fc3e0f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953504"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Il pacchetto e distribuire soluzioni di SharePoint
  In genere, una soluzione di SharePoint viene distribuita in un server SharePoint tramite file di pacchetto (con estensione wsp). È possibile usare Visual Studio per organizzare gli elementi di progetto SharePoint in funzionalità e creare un pacchetto per distribuire le funzionalità di SharePoint.

 In questo argomento vengono fornite le seguenti informazioni:

- [Creare funzionalità e pacchetti](#create-features-and-packages)

- [Funzionalità e supporto dello strumento di creazione di pacchetti](#feature-and-packaging-tool-support)

- [Distribuzione delle soluzioni SharePoint](#deploy-sharepoint-solutions)

- [Distribuire i file di soluzioni SharePoint](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>Creare funzionalità e pacchetti
 È possibile usare Visual Studio per raggruppare gli elementi di SharePoint correlati in una *funzionalità*. Ad esempio, una funzionalità per una definizione di elenco contatti può includere l'istanza di elenco e la definizione di elenco. È possibile combinare questi due elementi in una singola funzionalità per garantire una distribuzione. Per altre informazioni sulle funzionalità, vedere [blocco predefinito: Funzionalità](http://go.microsoft.com/fwlink/?LinkID=169183).

 Successivamente, è possibile creare un pacchetto della soluzione SharePoint (*wsp*) per aggregare più caratteristiche, sito definizioni, assembly e altri file in un singolo pacchetto, che archivia i file in un formato necessario per distribuire i file in SharePoint il server. Per altre informazioni, vedere [blocco predefinito: Soluzioni](http://go.microsoft.com/fwlink/?LinkID=169186).

## <a name="feature-and-packaging-tool-support"></a>Funzionalità e supporto dello strumento di creazione di pacchetti
 È possibile usare gli strumenti di sviluppo di SharePoint in Visual Studio a organizzare rapidamente i file di SharePoint in funzionalità e pacchetti di soluzioni per semplificare la distribuzione. È possibile usare gli strumenti seguenti per configurare il pacchetto di funzionalità e soluzioni.

- Progettazione di funzionalità e pacchetto.

- Esplora pacchetti, una finestra degli strumenti.

- Esplora soluzioni.

### <a name="feature-designer-and-package-designer"></a>Progettazione di funzionalità e pacchetto
 È possibile creare funzionalità imposta ambiti di e contrassegnare altre funzionalità come dipendenze utilizzando la finestra di progettazione di funzionalità. La finestra di progettazione visualizza anche il file XML finale che descrive ogni funzionalità. Per altre informazioni, vedere [funzionalità di SharePoint creare](../sharepoint/creating-sharepoint-features.md).

 Applicare la funzionalità a un sito Web specifico o un gruppo di siti Web mediante l'impostazione relativa *ambito* nella finestra di progettazione di funzionalità. Se una funzionalità viene attivata per un singolo sito Web, la funzionalità funziona solo nel sito Web specifico. Se una funzionalità viene attivata per una raccolta siti, gli elementi nella funzionalità si applicano alla raccolta di interi siti. Per altre informazioni, vedere [ambito elemento](http://go.microsoft.com/fwlink/?LinkID=169189).

 Se la funzionalità si basa su altre funzionalità, è possibile impostare una *dipendenza di attivazione delle funzionalità* per contrassegnare le funzionalità dipendenti prima di rendere disponibile la funzionalità. Una dipendenza di attivazione funzionalità controlla se le funzionalità dipendenti già attivate in quell'ambito. Per altre informazioni, vedere [dipendenze di attivazione e ambito](http://go.microsoft.com/fwlink/?LinkID=169190).

 Nella finestra di progettazione del pacchetto, è possibile raggruppare gli elementi di SharePoint in un unico pacchetto della soluzione e configurare se si desidera reimpostare il server Web durante la distribuzione. Per impostare il tipo di server di distribuzione, usare il **proprietà** finestra. La finestra di progettazione genera anche il file XML che descrive il contenuto del pacchetto. Per altre informazioni, vedere [pacchetti della soluzione SharePoint crea](../sharepoint/creating-sharepoint-solution-packages.md).

 Durante la distribuzione viene arrestato il servizio Internet Information Services (IIS) per copiare i file della soluzione per il server SharePoint. Tramite Progettazione pacchetti in Visual Studio, è possibile selezionare se il server Web deve essere riavviato. Per configurare se la soluzione viene distribuita in un server Web front-end o un server applicazioni, usare il **proprietà** finestra. Per altre informazioni, vedere [elemento Solution (soluzioni)](http://go.microsoft.com/fwlink/?LinkID=169191).

### <a name="packaging-explorer"></a>Esplora pacchetti
 Per completare la progettazione di funzionalità e pacchetto, è possibile usare Esplora pacchetti per raggruppare i file di SharePoint in funzionalità e i pacchetti. Inoltre, è possibile visualizzare la visualizzazione gerarchica del progetto SharePoint pacchetti, funzionalità, gli elementi e i file. Esplora pacchetti è una finestra degli strumenti che è possibile usare per completare le attività seguenti:

- Aprire elementi di progetto SharePoint e file.

- Trascinare e rilasciare gli elementi di progetto SharePoint da una delle funzionalità a un'altra.

- Trascinare e rilasciare gli elementi di progetto SharePoint e le funzionalità da un pacchetto a un altro.

- Aggiungere una nuova funzionalità a un pacchetto.

- Aprire una finestra di progettazione di funzionalità o un pacchetto.

- Convalidare le funzionalità e pacchetti.

  Gli strumenti di sviluppo di SharePoint in Visual Studio hanno regole di convalida per garantire che il pacchetto della soluzione è formattato correttamente. Inoltre, le regole verificano che il *wsp* file della soluzione può essere correttamente distribuito e attivato in un server SharePoint. Per altre informazioni sullo schema XML per le funzionalità, vedere [schemi per funzionalità](http://go.microsoft.com/fwlink/?LinkID=169192).

  È possibile aggiungere funzionalità personalizzate e regole di convalida del pacchetto per il sistema di progetto SharePoint. Per altre informazioni, vedere [Procedura: Creare funzionalità personalizzate e un pacchetto le regole di convalida per le soluzioni SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

  Per altre informazioni su Esplora pacchetti, vedere [come: Aggiungere e rimuovere funzionalità ed elementi in un pacchetto usando Esplora pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

### <a name="solution-explorer"></a>Esplora soluzioni
 È possibile usare Esplora soluzioni per esplorare e aprire i file del progetto SharePoint. Usare il menu di scelta rapida in Esplora soluzioni per aggiungere le funzionalità, i ricevitori di eventi e le risorse di funzionalità. Inoltre, è possibile aprire le finestre di progettazione di funzionalità e i progettisti di pacchetti per configurare le funzionalità e pacchetti per la distribuzione.

## <a name="deploy-sharepoint-solutions"></a>Distribuzione delle soluzioni SharePoint
 Dopo aver personalizzato la funzionalità e pacchetto in Visual Studio, è possibile creare un *wsp* file per la distribuzione nei server SharePoint. È possibile usare Visual Studio per eseguire il debug e testare il. *wsp* solo nel server SharePoint nel computer di sviluppo. Per altre informazioni su come distribuire le soluzioni di SharePoint a un server SharePoint remoto, vedere [distribuzione di una soluzione](http://go.microsoft.com/fwlink/?LinkID=169194).

 È anche possibile personalizzare i passaggi di distribuzione nel computer di sviluppo. Per altre informazioni, vedere [distribuire, pubblicare e aggiornare i pacchetti della soluzione SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

## <a name="deploy-files-in-sharepoint-solutions"></a>Distribuire i file di soluzioni SharePoint
 In genere, quando si aggiunge un elemento del progetto SharePoint alla soluzione di SharePoint, tutti i necessari file sono inclusi. File che possono essere compilati (file di codice) sono compilati nell'assembly di output della soluzione. Tuttavia, inoltre è possibile aggiungere i file non compilabile, ad esempio, *. XML*, *txt*, o file di risorse, a un progetto SharePoint. Questi file non sono inclusi automaticamente nella soluzione. Per garantire che vengono inclusi, aggiungere i file in una cartella mappata o a un elemento di progetto SharePoint.

 I file aggiunti a cartelle mappate vengono copiati automaticamente a hive di SharePoint quando si distribuisce la soluzione. Vengono distribuiti i file aggiunti a un elemento del progetto SharePoint nel percorso specificato nel **percorso di distribuzione** base alle proprietà per ogni file, che viene impostato parzialmente il **tipo di distribuzione** proprietà. Per impostazione predefinita, il **tipo di distribuzione** valore della proprietà **NoDeployment**, il che significa che il file non viene distribuito con la soluzione. È necessario impostare un altro valore per la proprietà da includere il file nel pacchetto.

 Ad esempio, per aggiungere un *XML* file a un progetto SharePoint, eseguire una di queste azioni:

- Aggiungere una cartella mappata di SharePoint "Layout" al progetto. Verrà creato nella **Esplora soluzioni** una cartella denominata **layout** che contiene una sottocartella del progetto. Aggiungere il *XML* file nella sottocartella di nuovo. Per impostazione predefinita, il file viene distribuito nel file System di SharePoint in *... \Template\Layouts.\\\<nome cartella >*. Per informazioni su come aggiungere cartelle mappate, vedere [procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md).

- Aggiungere il *. XML* file nella cartella di un elemento di progetto SharePoint e quindi modificare il **tipo di distribuzione** proprietà del *. XML* file da **NoDeployment**  a un altro, ad esempio impostando **RootFile** oppure **ElementFile**. Appropriato **tipo di distribuzione** impostazione varia a seconda del file e il progetto. Per altre informazioni sul **tipo di distribuzione** le impostazioni delle proprietà, vedere [soluzioni SharePoint sviluppare](../sharepoint/developing-sharepoint-solutions.md).

  Se un file aggiunto non è applicabile ad alcun progetto specifico della soluzione, è possibile aggiungere un progetto SharePoint vuoto per la soluzione e quindi aggiungervi gli altri file. In alternativa per la distribuzione di file in SharePoint, in particolare per il database del contenuto, è possibile aggiungere un modulo al progetto e quindi aggiungere i file del modulo. Per altre informazioni, vedere [usare i moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Vedere anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)

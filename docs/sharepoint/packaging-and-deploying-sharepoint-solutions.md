---
title: Creazione di pacchetti e distribuzione SharePoint soluzioni | Microsoft Docs
description: Creare pacchetti e SharePoint soluzioni distribuite in un server SharePoint usando un file del pacchetto della soluzione (con estensione wsp).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 2384d98c2f0f2872bb7aba0ce505264ce531da8e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135882"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Creare pacchetti e distribuire SharePoint soluzioni
  In genere, una SharePoint viene distribuita in un server SharePoint usando un file del pacchetto della soluzione (con estensione wsp). È possibile usare Visual Studio per organizzare SharePoint Project elementi in funzionalità e per creare un pacchetto per distribuire le SharePoint funzionalità.

 Questo argomento contiene informazioni sui seguenti aspetti:

- [Creare funzionalità e pacchetti](#create-features-and-packages)

- [Supporto di funzionalità e strumenti di creazione pacchetti](#feature-and-packaging-tool-support)

- [Distribuire SharePoint soluzioni](#deploy-sharepoint-solutions)

- [Distribuire file in SharePoint soluzioni](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>Creare funzionalità e pacchetti
 È possibile usare Visual Studio per raggruppare SharePoint elementi correlati in una *funzionalità*. Ad esempio, una funzionalità per una definizione di elenco Contatti può includere l'istanza di elenco e la definizione dell'elenco. È possibile combinare questi due elementi in un'unica funzionalità a scopo di distribuzione. Per altre informazioni sulle funzionalità, vedere [Blocco predefinito: funzionalità](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)).

 Successivamente, è possibile creare un pacchetto della soluzione SharePoint ( con estensione *wsp*) per aggregare più funzionalità, definizioni di sito, assembly e altri file in un unico pacchetto, in cui i file vengono archiviati in un formato richiesto da SharePoint per distribuire i file nel server. Per altre informazioni, vedere [Blocco predefinito: Soluzioni](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)).

## <a name="feature-and-packaging-tool-support"></a>Supporto di funzionalità e strumenti di creazione pacchetti
 È possibile usare gli strumenti SharePoint di sviluppo in Visual Studio per organizzare rapidamente i file SharePoint in funzionalità e pacchetti di soluzioni per una distribuzione più semplice. È possibile usare gli strumenti seguenti per configurare la funzionalità e il pacchetto della soluzione.

- Progettazione funzionalità e Progettazione pacchetti.

- Packaging Explorer, una finestra degli strumenti.

- Esplora soluzioni.

### <a name="feature-designer-and-package-designer"></a>Progettazione funzionalità e Progettazione pacchetti
 È possibile creare funzionalità, impostare ambiti e contrassegnare altre funzionalità come dipendenze usando Progettazione funzionalità. La finestra di progettazione visualizza anche il file XML finale che descrive ogni funzionalità. Per altre informazioni, vedere [Creare SharePoint funzionalità .](../sharepoint/creating-sharepoint-features.md)

 Applicare la funzionalità a un sito Web o a un gruppo specifico di siti Web impostandone *l'ambito* in Progettazione funzionalità. Se una funzionalità viene attivata per un singolo sito Web, la funzionalità funziona solo in quel particolare sito Web. Se una funzionalità viene attivata per una raccolta siti, gli elementi della funzionalità si applicano all'intera raccolta siti. Per altre informazioni, vedere [Ambito degli elementi](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14)).

 Se la funzionalità si basa su altre  funzionalità, è possibile impostare una dipendenza di attivazione della funzionalità per contrassegnare le funzionalità dipendenti prima di rendere disponibile la funzionalità. Una dipendenza di attivazione delle funzionalità controlla se le funzionalità dipendenti sono già attivate in tale ambito. Per altre informazioni, vedere [Dipendenze di attivazione e Ambito](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14)).

 In Progettazione pacchetti è possibile raggruppare SharePoint elementi in un singolo pacchetto della soluzione e specificare se reimpostare il server Web durante la distribuzione. Per impostare il tipo di server di distribuzione, usare la **finestra** Proprietà. La finestra di progettazione genera anche il file XML che descrive il contenuto del pacchetto. Per altre informazioni, vedere [Creare SharePoint pacchetti della soluzione](../sharepoint/creating-sharepoint-solution-packages.md).

 Durante la distribuzione, il Internet Information Services (IIS) viene arrestato per copiare i file della soluzione nel server SharePoint. Usando Progettazione pacchetti in Visual Studio, è possibile scegliere se riavviare il server Web. Per configurare se la soluzione viene distribuita in un server Web front-end o in un server applicazioni, usare la **finestra** Proprietà. Per altre informazioni, vedere [Elemento Solution (Solution)](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14)).

### <a name="packaging-explorer"></a>Esplora pacchetti
 Per integrare Progettazione funzionalità e Progettazione pacchetti, è possibile usare Esplora pacchetti per raggruppare SharePoint file in funzionalità e pacchetti. È anche possibile visualizzare la visualizzazione gerarchica del pacchetto, delle funzionalità, SharePoint di progetto e dei file. Packaging Explorer è una finestra degli strumenti che è possibile usare per completare le attività seguenti:

- Aprire SharePoint file e elementi del progetto.

- Trascinare e rilasciare SharePoint di progetto da una funzionalità a un'altra.

- Trascinare e rilasciare SharePoint di progetto e funzionalità da un pacchetto a un altro.

- Aggiungere una nuova funzionalità a un pacchetto.

- Aprire una finestra di progettazione di funzionalità o pacchetti.

- Convalidare funzionalità e pacchetti.

  Gli SharePoint di sviluppo in Visual Studio regole di convalida per garantire che il pacchetto della soluzione sia formattato correttamente. Inoltre, le regole verificano che il file di soluzione con estensione *wsp* possa essere distribuito e attivato correttamente in un server SharePoint. Per altre informazioni sullo schema XML per le funzionalità, vedere [Schemi di funzionalità](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)).

  È possibile aggiungere regole di convalida personalizzate per funzionalità e pacchetti al SharePoint di progetto. Per altre informazioni, vedere [Procedura: Creare regole di](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)convalida dei pacchetti e funzionalità personalizzate per SharePoint soluzioni .

  Per altre informazioni su Packaging Explorer, vedere Procedura: Aggiungere e rimuovere funzionalità ed elementi a un pacchetto [tramite Packaging Explorer.](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)

### <a name="solution-explorer"></a>Esplora soluzioni
 È possibile usare Esplora soluzioni per esplorare e aprire i file del SharePoint progetto. Usare il menu di scelta rapida Esplora soluzioni per aggiungere funzionalità, ricevitori di eventi di funzionalità e risorse funzionalità. È anche possibile aprire Progettazione funzionalità e Progettazione pacchetti per configurare le funzionalità e i pacchetti per la distribuzione.

## <a name="deploy-sharepoint-solutions"></a>Distribuire SharePoint soluzioni
 Dopo aver personalizzato le funzionalità e il pacchetto in Visual Studio, è possibile creare un file con estensione *wsp* da distribuire nei SharePoint server. È possibile usare Visual Studio per eseguire il debug e il test di . *wsp* solo nel SharePoint server nel computer di sviluppo. Per altre informazioni su come distribuire le soluzioni SharePoint in un server SharePoint remoto, vedere [Distribuzione di una soluzione](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14)).

 È anche possibile personalizzare i passaggi di distribuzione nel computer di sviluppo. Per altre informazioni, vedere [Distribuire, pubblicare e aggiornare SharePoint pacchetti della soluzione](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

## <a name="deploy-files-in-sharepoint-solutions"></a>Distribuire file in SharePoint soluzioni
 In genere, quando si aggiunge un SharePoint progetto alla soluzione SharePoint, vengono inclusi tutti i file necessari. I file che possono essere compilati (file di codice) vengono compilati nell'assembly di output della soluzione. Tuttavia, potrebbe anche essere necessario aggiungere file non compilabili, ad esempio.xml *,* *.txt* o file di risorse, a un SharePoint progetto. Questi file non vengono automaticamente in pacchetto nella soluzione. Per assicurarsi che siano in pacchetto, aggiungere i file a una cartella mappata o a un SharePoint di progetto.

 I file aggiunti alle cartelle mappate vengono copiati automaticamente nell SharePoint hive quando viene distribuita la soluzione. I file aggiunti a un SharePoint di progetto vengono distribuiti  nel percorso specificato nella proprietà Percorso distribuzione per ogni file, che viene impostato parzialmente in base alla **proprietà Tipo di** distribuzione. Per impostazione predefinita, **il valore della** proprietà Tipo di distribuzione è **NoDeployment**, il che significa che il file non viene distribuito con la soluzione. È necessario impostare un altro valore per la proprietà per includere il file nel pacchetto.

 Ad esempio, per aggiungere un *file.xml* a un progetto SharePoint, eseguire una delle azioni seguenti:

- Aggiungere una SharePoint "Layout" mappata al progetto. In questo modo **Esplora soluzioni** una cartella denominata **Layouts** con una sottocartella per il progetto. Aggiungere il *.xml* file alla nuova sottocartella. Per impostazione predefinita, il file viene distribuito nel SharePoint file system in *. \TEMPLATE\LAYOUTS \\ \<Folder Name>*. Per informazioni su come aggiungere cartelle mappate, vedere [Procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md).

- Aggiungere il file *.xml* alla cartella di un elemento di progetto  SharePoint e quindi modificare la proprietà Tipo di distribuzione del file.xmlda **NoDeployment** *a* un'altra impostazione, ad esempio **RootFile** **o ElementFile**. **L'impostazione del tipo di** distribuzione appropriata dipende dal file e dal progetto. Per altre informazioni sulle impostazioni **delle proprietà Tipo di** distribuzione, vedere Sviluppare SharePoint [soluzioni](../sharepoint/developing-sharepoint-solutions.md).

  Se un file aggiunto non si applica ad alcun progetto specifico nella soluzione, è possibile aggiungere un SharePoint Project vuoto alla soluzione e quindi aggiungervi i file aggiuntivi. Un'altra alternativa per la distribuzione di file SharePoint, in particolare nel database del contenuto, consiste nell'aggiungere un modulo al progetto e quindi aggiungere i file al modulo. Per altre informazioni, vedere [Usare moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Vedi anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)

---
title: Creazione di pacchetti e distribuzione di soluzioni SharePoint | Microsoft Docs
description: Creare un pacchetto e distribuire le soluzioni SharePoint, che vengono distribuite in un server SharePoint tramite un file di pacchetto di soluzione (con estensione wsp).
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd06a5be3c9e7ceea38bdb4560f8b6262175bd45
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305077"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Creare pacchetti e distribuire soluzioni SharePoint
  In genere, una soluzione SharePoint viene distribuita in un server SharePoint tramite un file di pacchetto di soluzione (con estensione wsp). È possibile utilizzare Visual Studio per organizzare gli elementi del progetto SharePoint in funzionalità e creare un pacchetto per distribuire le funzionalità di SharePoint.

 Questo argomento contiene informazioni sui seguenti aspetti:

- [Creazione di funzionalità e pacchetti](#create-features-and-packages)

- [Supporto degli strumenti per funzionalità e pacchetti](#feature-and-packaging-tool-support)

- [Distribuire soluzioni SharePoint](#deploy-sharepoint-solutions)

- [Distribuire file in soluzioni SharePoint](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>Creazione di funzionalità e pacchetti
 È possibile utilizzare Visual Studio per raggruppare gli elementi di SharePoint correlati in una *funzionalità* di. Una funzionalità per la definizione di un elenco contatti, ad esempio, può includere l'istanza dell'elenco e la definizione dell'elenco. È possibile combinare questi due elementi in un'unica funzionalità per scopi di distribuzione. Per ulteriori informazioni sulle funzionalità di, vedere [Building Block: features](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)).

 Successivamente, è possibile creare un pacchetto della soluzione SharePoint (con *estensione wsp*) per aggregare più funzionalità, definizioni del sito, assembly e altri file in un unico pacchetto, che archivia i file in un formato necessario per SharePoint per distribuire i file nel server. Per altre informazioni, vedere [Building Block: Solutions](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)).

## <a name="feature-and-packaging-tool-support"></a>Supporto degli strumenti per funzionalità e pacchetti
 È possibile usare gli strumenti di sviluppo di SharePoint in Visual Studio per organizzare rapidamente i file di SharePoint in funzionalità e pacchetti di soluzioni per semplificare la distribuzione. Per configurare la funzionalità e il pacchetto della soluzione, è possibile usare gli strumenti seguenti.

- Progettazione funzionalità e progettazione pacchetti.

- Esplora pacchetti, una finestra degli strumenti.

- Esplora soluzioni.

### <a name="feature-designer-and-package-designer"></a>Progettazione funzionalità e progettazione pacchetti
 È possibile creare funzionalità, impostare gli ambiti e contrassegnare altre funzionalità come dipendenze usando la finestra di progettazione della funzionalità. Nella finestra di progettazione viene inoltre visualizzato il file XML finale che descrive ogni funzionalità. Per ulteriori informazioni, vedere [creare funzionalità di SharePoint](../sharepoint/creating-sharepoint-features.md).

 Applicare la funzionalità a un sito Web o a un gruppo di siti Web specifico impostando il relativo *ambito* nella finestra di progettazione della funzionalità. Se una funzionalità viene attivata per un singolo sito Web, la funzionalità funziona solo in quel particolare sito Web. Se una funzionalità viene attivata per una raccolta siti, gli elementi della funzionalità si applicano all'intera raccolta siti. Per altre informazioni, vedere [ambito dell'elemento](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14)).

 Se la funzionalità si basa su altre funzionalità, è possibile impostare una *dipendenza di attivazione della funzionalità* per contrassegnare le funzionalità dipendenti prima di rendere disponibile la funzionalità. Una dipendenza di attivazione della funzionalità controlla se le funzionalità dipendenti sono già attivate in tale ambito. Per ulteriori informazioni, vedere [dipendenze di attivazione e ambito](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14)).

 In Progettazione pacchetti è possibile raggruppare gli elementi di SharePoint in un unico pacchetto della soluzione e configurare se ripristinare il server Web durante la distribuzione. Per impostare il tipo di server di distribuzione, utilizzare la finestra **Proprietà** . La finestra di progettazione genera inoltre il file XML che descrive il contenuto del pacchetto. Per ulteriori informazioni, vedere [creare pacchetti della soluzione SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).

 Durante la distribuzione, il servizio Internet Information Services (IIS) viene arrestato per copiare i file della soluzione nel server SharePoint. Utilizzando Progettazione pacchetti in Visual Studio, è possibile specificare se il server Web deve essere riavviato. Per configurare se la soluzione viene distribuita in un server Web front-end o in un server applicazioni, utilizzare la finestra **Proprietà** . Per altre informazioni, vedere [elemento Solution (soluzione)](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14)).

### <a name="packaging-explorer"></a>Esplora pacchetti
 Per integrare progettazione funzionalità e progettazione pacchetti, è possibile utilizzare Esplora pacchetti per raggruppare i file di SharePoint in funzionalità e pacchetti di. Inoltre, è possibile visualizzare la visualizzazione gerarchica del pacchetto, delle funzionalità, degli elementi del progetto SharePoint e dei file. Packaging Explorer è una finestra degli strumenti che è possibile utilizzare per completare le attività seguenti:

- Aprire gli elementi e i file del progetto SharePoint.

- Trascinare gli elementi del progetto SharePoint da una funzionalità a un'altra.

- Trascinare e rilasciare gli elementi e le funzionalità del progetto SharePoint da un pacchetto a un altro.

- Consente di aggiungere una nuova funzionalità a un pacchetto.

- Aprire una funzionalità o progettazione pacchetti.

- Convalidare le funzionalità e i pacchetti.

  Gli strumenti di sviluppo di SharePoint in Visual Studio presentano regole di convalida che consentono di garantire che il formato del pacchetto della soluzione sia corretto. Inoltre, le regole verificano che il file della soluzione con *estensione wsp* possa essere distribuito e attivato correttamente in un server SharePoint. Per ulteriori informazioni sull'XML Schema per le funzionalità di, vedere [schemi di funzionalità](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)).

  È possibile aggiungere regole personalizzate per la convalida di funzionalità e pacchetti al sistema del progetto SharePoint. Per altre informazioni, vedere [procedura: creare regole personalizzate per la convalida di funzionalità e pacchetti per le soluzioni SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

  Per altre informazioni su packaging Explorer, vedere [procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto con Esplora pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

### <a name="solution-explorer"></a>Esplora soluzioni
 È possibile utilizzare Esplora soluzioni per spostarsi e aprire i file del progetto SharePoint. Utilizzare il menu di scelta rapida in Esplora soluzioni per aggiungere funzionalità, ricevitori di eventi di funzionalità e risorse della funzionalità. Inoltre, è possibile aprire Progettazione funzionalità e progettazione pacchetti per configurare le funzionalità e i pacchetti per la distribuzione.

## <a name="deploy-sharepoint-solutions"></a>Distribuire soluzioni SharePoint
 Dopo aver personalizzato le funzionalità e il pacchetto in Visual Studio, è possibile creare un file con estensione *WSP* per la distribuzione nei server SharePoint. È possibile usare Visual Studio per eseguire il debug e il test di. *WSP* solo sul server SharePoint nel computer di sviluppo. Per ulteriori informazioni su come distribuire le soluzioni SharePoint in un server SharePoint remoto, vedere [distribuzione di una soluzione](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14)).

 È inoltre possibile personalizzare i passaggi di distribuzione nel computer di sviluppo. Per altre informazioni, vedere [distribuire, pubblicare e aggiornare i pacchetti della soluzione SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

## <a name="deploy-files-in-sharepoint-solutions"></a>Distribuire file in soluzioni SharePoint
 In genere, quando si aggiunge un elemento di progetto SharePoint alla soluzione di SharePoint, vengono inclusi tutti i file necessari. I file che possono essere compilati (file di codice) sono incorporati nell'assembly di output della soluzione. Tuttavia, potrebbe essere necessario aggiungere anche file non compilabili, ad esempio file con *estensione XML*, *txt* o di risorse, a un progetto SharePoint. Questi file non vengono automaticamente inclusi nella soluzione. Per assicurarsi che siano inclusi in un pacchetto, aggiungere i file a una cartella mappata o a un elemento del progetto SharePoint.

 I file aggiunti alle cartelle mappate vengono copiati automaticamente nell'hive di SharePoint quando viene distribuita la soluzione. I file aggiunti a un elemento del progetto SharePoint vengono distribuiti nel percorso specificato nella proprietà **percorso di distribuzione** per ogni file, che è parzialmente impostato in base alla proprietà **tipo di distribuzione** . Per impostazione predefinita, il valore della proprietà del **tipo di distribuzione** è **NoDeployment**, il che significa che il file non viene distribuito con la soluzione. È necessario impostare un altro valore per la proprietà in modo da includere il file nel pacchetto.

 Per aggiungere ad esempio un file *XML* a un progetto SharePoint, eseguire una delle operazioni seguenti:

- Aggiungere una cartella mappata "Layouts" di SharePoint al progetto. In **Esplora soluzioni** una cartella denominata **Layouts** che include una sottocartella per il progetto. Aggiungere il file con *estensione XML* alla nuova sottocartella. Per impostazione predefinita, il file viene distribuito nel file system di SharePoint in *. \\\TEMPLATE\LAYOUTS \<Folder Name>*. Per informazioni su come aggiungere cartelle mappate, vedere [procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md).

- Aggiungere il *file XML* alla cartella di un elemento del progetto SharePoint, quindi modificare la proprietà del **tipo di distribuzione** del file *con estensione XML* da **NoDeployment** a un'altra impostazione, ad esempio **RootFile** o **ElementFile**. L'impostazione del **tipo di distribuzione** appropriato dipende dal file e dal progetto. Per ulteriori informazioni sulle impostazioni delle proprietà del **tipo di distribuzione** , vedere [sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).

  Se un file aggiunto non è applicabile a un progetto specifico nella soluzione, è possibile aggiungere un progetto SharePoint vuoto alla soluzione e quindi aggiungervi i file aggiuntivi. Un'altra alternativa per la distribuzione di file in SharePoint, in particolare per il database del contenuto, consiste nell'aggiungere un modulo al progetto e quindi aggiungere i file al modulo. Per altre informazioni, vedere [usare i moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Vedere anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)

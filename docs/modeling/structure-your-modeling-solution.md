---
title: Strutturare la soluzione di modellazione
description: Informazioni su uno schema di modellazione per dividere l'applicazione in parti diverse che corrispondono ai livelli in un diagramma a livelli complessivo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 4fa1a9136d4972897231a33fe477514769b9330e38fd9fad46bac196624c5278
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428738"
---
# <a name="structure-your-modeling-solution"></a>Strutturare la soluzione di modellazione

Per usare efficacemente i modelli in un progetto di sviluppo, è necessario che i membri del team siano in grado di usare contemporaneamente modelli di parti diverse del progetto. Questo argomento suggerisce uno schema per suddividere l'applicazione in più parti, che corrispondono ai livelli di un diagramma su livelli generale.

Per iniziare rapidamente un progetto o un sottoprogetto, è utile avere un modello di progetto basato sulla struttura del progetto scelta. Questo argomento descrive come creare e usare tale modello.

Questo argomento presuppone che si lavori su un progetto abbastanza grande per richiedere la collaborazione di più membri del team ed eventualmente di più team. Il codice e i modelli del progetto sono archiviati in un sistema di controllo del codice sorgente quale [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Almeno alcuni membri del team usano Visual Studio per sviluppare i modelli, mentre altri membri possono visualizzarli con altre versioni di Visual Studio.

Per visualizzare le versioni di Visual Studio ogni strumento e funzionalità di modellazione, vedere Supporto delle versioni per gli strumenti di architettura [e modellazione](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="solution-structure"></a>Struttura della soluzione

In un progetto di medie o grandi dimensioni, la struttura del team riflette la struttura dell'applicazione. Ogni team usa una soluzione di Visual Studio.

### <a name="to-divide-an-application-into-layers"></a>Per suddividere un'applicazione in livelli

1. Basare la struttura delle soluzioni sulla struttura dell'applicazione, ad esempio applicazione Web, applicazione di servizio o applicazione desktop. Un'ampia gamma di architetture comuni è illustrata in [Application Archetypes (Archetipi di applicazione) nella Guida all'architettura delle applicazioni Microsoft](/previous-versions/msp-n-p/ee658107(v=pandp.10)).

2. Creare una Visual Studio soluzione, che verrà chiamata soluzione Architettura. Questa soluzione verrà usata per creare la progettazione complessiva del sistema. Conterrà modelli ma non il codice.

   Aggiungere un diagramma delle dipendenze a questa soluzione. Nel diagramma delle dipendenze disegnare l'architettura scelta per l'applicazione. Ad esempio, il diagramma potrebbe mostrare i seguenti livelli con le reciproche dipendenze: presentazione, logica di business e dati.

4. Creare una soluzione Visual Studio per ogni livello nel diagramma delle dipendenze architettura.

   Queste soluzioni verranno usate per sviluppare il codice dei livelli.

5. Creare modelli che rappresentano le progettazioni dei livelli e i concetti comuni a tutti i livelli. Disporre i modelli in modo che si possano visualizzare tutti dalla soluzione Architecture e che da ogni livello sia possibile visualizzare i relativi modelli.

   È possibile ottenere questo risultato con una delle procedure seguenti. La prima consente di creare un progetto di modello separato per ogni livello, mentre la seconda permette di creare un unico progetto di modello condiviso tra i livelli.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Usare un progetto di modellazione separato per ogni livello

1. Creare un progetto di modello nella soluzione di ogni livello.

   Questo modello conterrà diagrammi che descrivono i requisiti e la progettazione di tale livello. Può anche contenere diagrammi delle dipendenze che mostrano i livelli annidati.

   A questo punto è disponibile un modello per ogni livello, oltre a un modello per l'architettura dell'applicazione. Ogni modello è contenuto in una soluzione separata. In questo modo, i membri del team possono lavorare contemporaneamente sugli stessi livelli.

2. Aggiungere alla soluzione Architecture il progetto di modellazione della soluzione di ogni livello. A questo scopo, aprire la soluzione Architecture. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione, scegliere Aggiungi e quindi fare clic su **Project**. Passare al progetto di modellazione (con estensione modelproj) in una soluzione del livello.

   Ogni modello è ora visibile in due soluzioni: la relativa soluzione principale e la soluzione Architecture.

3. Al progetto di modellazione di ogni livello aggiungere un diagramma delle dipendenze. Iniziare con una copia del diagramma delle dipendenze architettura. È possibile eliminare parti che non sono dipendenze del diagramma delle dipendenze.

   È anche possibile aggiungere diagrammi delle dipendenze che rappresentano la struttura dettagliata di questo livello.

   Questi diagrammi vengono usati per convalidare il codice sviluppato nel livello.

4. Nella soluzione Architecture modificare i requisiti e i modelli di progettazione di tutti i livelli tramite Visual Studio.

   Nella soluzione di ogni livello sviluppare il codice relativo al livello specifico, facendo riferimento al modello. Se si ritiene sufficiente eseguire lo sviluppo senza usare lo stesso computer per aggiornare il modello, è possibile leggere il modello e sviluppare codice usando versioni di Visual Studio che non consentono di creare modelli. È anche possibile generare codice dal modello in queste versioni.

   Questo metodo assicura che non ci saranno interferenze da parte degli sviluppatori che modificano contemporaneamente i modelli di livello.

   Tuttavia, poiché i modelli sono separati, è difficile fare riferimento a concetti comuni. Ogni modello deve disporre di una copia distinta degli elementi degli altri livelli e dell'architettura dai quali dipende. Il diagramma delle dipendenze in ogni livello deve essere mantenuto sincronizzato con il diagramma delle dipendenze architettura. È difficile mantenere la sincronizzazione quando questi elementi sono soggetti a modifica, anche se è possibile sviluppare appositi strumenti a questo scopo.

#### <a name="use-a-separate-package-for-each-layer"></a>Usare un pacchetto separato per ogni livello

1. Aggiungere il progetto di modello Architecture alla soluzione di ogni livello. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione, scegliere Aggiungi **e** quindi fare clic su **Project**. A questo punto, è possibile accedere da qualsiasi soluzione al singolo progetto di modello, ossia al progetto Architecture e al progetto di sviluppo per ogni livello.

2. Nel modello condiviso creare un pacchetto per ogni livello: **in** Esplora soluzioni selezionare il progetto di modellazione. In **Esplora modelli UML fare** clic con il pulsante destro del mouse sul nodo radice del modello, scegliere **Aggiungi** e quindi fare clic su **Pacchetto**.

   Ogni pacchetto conterrà diagrammi che descrivono i requisiti e la progettazione del livello corrispondente.

3. Se necessario, aggiungere diagrammi di dipendenza locali per la struttura interna di ogni livello.

   Questo metodo consente agli elementi di progettazione di ogni livello di fare riferimento direttamente agli elementi degli altri livelli e dell'architettura comune da cui dipendono.

   Anche se è possibile che operazioni simultanee su pacchetti diversi causino alcuni conflitti, questi risulteranno abbastanza facili da gestire, in quanto i pacchetti vengono archiviati in file separati.

## <a name="create-architecture-templates"></a>Creare modelli di architettura

In pratica, non si creano tutte le soluzioni Visual Studio contemporaneamente, ma le si aggiunge con l'avanzamento del progetto. Probabilmente si userà anche la stessa struttura della soluzione nei progetti futuri. Per velocizzare la creazione di nuove soluzioni, è possibile creare un modello di soluzione o di progetto. È possibile acquisire il modello in un'estensione VSIX ( Visual Studio Integration Extension) per facilitarne la distribuzione e l'installazione in altri computer.

Ad esempio, se si usano spesso soluzioni con livelli presentazione, aziendale e dati, è possibile configurare un modello per creare nuove soluzioni con la medesima struttura.

### <a name="to-create-a-solution-template"></a>Per creare un modello di soluzione

1. [Scaricare e installare l'Esportazione guidata modelli](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ExportTemplateWizard).

2. Creare la struttura della soluzione da usare come punto di partenza per i progetti futuri.

3. Scegliere **Esporta modello come VSIX** dal menu **File**.

   Verrà **visualizzata l'Esportazione guidata modello come VSIX.**

4. Seguendo le istruzioni della procedura guidata, selezionare i progetti da includere nel modello, fornire un nome e una descrizione per il modello e specificare un percorso di output.

## <a name="watch-a-video"></a>Guardare un video

[Organizzare e gestire i modelli](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>Vedi anche

- [Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)

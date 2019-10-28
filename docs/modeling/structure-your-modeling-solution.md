---
title: Strutturare la soluzione di modellazione
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fecf0d146c1116e6ec6376ffd9ad929cc9179d1c
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985214"
---
# <a name="structure-your-modeling-solution"></a>Strutturare la soluzione di modellazione

Per usare efficacemente i modelli in un progetto di sviluppo, è necessario che i membri del team siano in grado di usare contemporaneamente modelli di parti diverse del progetto. Questo argomento suggerisce uno schema per suddividere l'applicazione in più parti, che corrispondono ai livelli di un diagramma su livelli generale.

Per iniziare rapidamente un progetto o un sottoprogetto, è utile avere un modello di progetto basato sulla struttura del progetto scelta. Questo argomento descrive come creare e usare tale modello.

Questo argomento presuppone che si lavori su un progetto abbastanza grande per richiedere la collaborazione di più membri del team ed eventualmente di più team. Il codice e i modelli del progetto sono archiviati in un sistema di controllo del codice sorgente quale [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Almeno alcuni membri del team usano Visual Studio per sviluppare i modelli, mentre altri membri possono visualizzarli con altre versioni di Visual Studio.

Per individuare le versioni di Visual Studio che supportano ogni strumento e funzionalità di modellazione, vedere [supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Struttura della soluzione

In un progetto di medie o grandi dimensioni, la struttura del team riflette la struttura dell'applicazione. Ogni team usa una soluzione di Visual Studio.

### <a name="to-divide-an-application-into-layers"></a>Per suddividere un'applicazione in livelli

1. Basare la struttura delle soluzioni sulla struttura dell'applicazione, ad esempio applicazione Web, applicazione di servizio o applicazione desktop. Un'ampia gamma di architetture comuni è illustrata in [archetipi delle applicazioni nella Guida all'architettura delle applicazioni Microsoft](/previous-versions/msp-n-p/ee658107(v=pandp.10)).

2. Creare una soluzione di Visual Studio che chiameremo la soluzione Architecture. Questa soluzione verrà usata per creare la progettazione complessiva del sistema. Conterrà modelli ma non il codice.

   Aggiungere un diagramma delle dipendenze alla soluzione. Nel diagramma delle dipendenze, creare l'architettura scelta per l'applicazione. Ad esempio, il diagramma potrebbe mostrare i seguenti livelli con le reciproche dipendenze: presentazione, logica di business e dati.

4. Creare una soluzione Visual Studio separata per ogni livello nel diagramma delle dipendenze dell'architettura.

   Queste soluzioni verranno usate per sviluppare il codice dei livelli.

5. Creare modelli che rappresentano le progettazioni dei livelli e i concetti comuni a tutti i livelli. Disporre i modelli in modo che si possano visualizzare tutti dalla soluzione Architecture e che da ogni livello sia possibile visualizzare i relativi modelli.

   È possibile ottenere questo risultato con una delle procedure seguenti. La prima consente di creare un progetto di modello separato per ogni livello, mentre la seconda permette di creare un unico progetto di modello condiviso tra i livelli.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Usare un progetto di modello separato per ogni livello

1. Creare un progetto di modello nella soluzione di ogni livello.

   Questo modello conterrà i diagrammi che descrivono i requisiti e la progettazione del livello. Può inoltre contenere diagrammi di dipendenza che mostrano livelli annidati.

   A questo punto è disponibile un modello per ogni livello, oltre a un modello per l'architettura dell'applicazione. Ogni modello è contenuto in una soluzione separata. In questo modo, i membri del team possono lavorare contemporaneamente sugli stessi livelli.

2. Aggiungere alla soluzione Architecture il progetto di modellazione della soluzione di ogni livello. A questo scopo, aprire la soluzione Architecture. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo della soluzione, scegliere Aggiungi, quindi fare clic su **progetto esistente**. Passare al progetto di modellazione (con estensione modelproj) in una soluzione del livello.

   Ogni modello è ora visibile in due soluzioni: la relativa soluzione principale e la soluzione Architecture.

3. Aggiungere un diagramma delle dipendenze al progetto di modello di ogni livello. Iniziare con una copia del diagramma delle dipendenze dell'architettura. È possibile eliminare parti che non sono dipendenze del diagramma delle dipendenze.

   È anche possibile aggiungere diagrammi di dipendenza che rappresentano la struttura dettagliata di questo livello.

   Questi diagrammi vengono usati per convalidare il codice sviluppato nel livello.

4. Nella soluzione Architecture modificare i requisiti e i modelli di progettazione di tutti i livelli tramite Visual Studio.

   Nella soluzione di ogni livello sviluppare il codice relativo al livello specifico, facendo riferimento al modello. Se si ritiene sufficiente eseguire lo sviluppo senza usare lo stesso computer per aggiornare il modello, è possibile leggere il modello e sviluppare codice usando versioni di Visual Studio che non consentono di creare modelli. È anche possibile generare codice dal modello in queste versioni.

   Questo metodo assicura che non ci saranno interferenze da parte degli sviluppatori che modificano contemporaneamente i modelli di livello.

   Tuttavia, poiché i modelli sono separati, è difficile fare riferimento a concetti comuni. Ogni modello deve disporre di una copia distinta degli elementi degli altri livelli e dell'architettura dai quali dipende. Il diagramma delle dipendenze in ogni livello deve essere mantenuto sincronizzato con il diagramma delle dipendenze dell'architettura. È difficile mantenere la sincronizzazione quando questi elementi sono soggetti a modifica, anche se è possibile sviluppare appositi strumenti a questo scopo.

#### <a name="use-a-separate-package-for-each-layer"></a>Usare un pacchetto separato per ogni livello

1. Aggiungere il progetto di modello Architecture alla soluzione di ogni livello. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo della soluzione, scegliere **Aggiungi**, quindi fare clic su **progetto esistente**. A questo punto, è possibile accedere da qualsiasi soluzione al singolo progetto di modello, ossia al progetto Architecture e al progetto di sviluppo per ogni livello.

2. Nel modello condiviso creare un pacchetto per ogni livello: in **Esplora soluzioni**selezionare il progetto di modello. In **Esplora modelli UML**fare clic con il pulsante destro del mouse sul nodo radice del modello, scegliere **Aggiungi**, quindi fare clic su **pacchetto**.

   Ogni pacchetto conterrà i diagrammi che descrivono i requisiti e la progettazione del livello corrispondente.

3. Se necessario, aggiungere diagrammi di dipendenza locali per la struttura interna di ogni livello.

   Questo metodo consente agli elementi di progettazione di ogni livello di fare riferimento direttamente agli elementi degli altri livelli e dell'architettura comune da cui dipendono.

   Anche se è possibile che operazioni simultanee su pacchetti diversi causino alcuni conflitti, questi risulteranno abbastanza facili da gestire, in quanto i pacchetti vengono archiviati in file separati.

## <a name="create-architecture-templates"></a>Creare modelli di architettura

In pratica, non è possibile creare contemporaneamente tutte le soluzioni di Visual Studio, ma aggiungerle durante l'avanzamento del progetto. Probabilmente si userà anche la stessa struttura della soluzione nei progetti futuri. Per velocizzare la creazione di nuove soluzioni, è possibile creare un modello di soluzione o di progetto. È possibile acquisire il modello in un'estensione VSIX ( Visual Studio Integration Extension) per facilitarne la distribuzione e l'installazione in altri computer.

Ad esempio, se si usano spesso soluzioni con livelli presentazione, aziendale e dati, è possibile configurare un modello per creare nuove soluzioni con la medesima struttura.

### <a name="to-create-a-solution-template"></a>Per creare un modello di soluzione

1. [Scaricare e installare l'esportazione guidata modelli](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ExportTemplateWizard).

2. Creare la struttura della soluzione da usare come punto di partenza per i progetti futuri.

3. Scegliere **Esporta modello come VSIX** dal menu **File**.

   Si apre la **procedura guidata Esporta modello come VSIX** .

4. Seguendo le istruzioni della procedura guidata, selezionare i progetti da includere nel modello, fornire un nome e una descrizione per il modello e specificare un percorso di output.

## <a name="watch-a-video"></a>Guarda un video

[Organizzare e gestire i modelli](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>Vedere anche

- [Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)
- [Documentazione Visual Studio Architecture Tooling Guidance](../modeling/visual-studio-architecture-tooling-guidance.md)

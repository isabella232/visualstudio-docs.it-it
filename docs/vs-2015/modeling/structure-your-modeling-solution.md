---
title: Strutturare la soluzione di modellazione | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 995192b372b9c1909ad3a7f164474cfaf63f07bc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784455"
---
# <a name="structure-your-modeling-solution"></a>Strutturare la soluzione di modellazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per usare efficacemente i modelli in un progetto di sviluppo, è necessario che i membri del team siano in grado di usare contemporaneamente modelli di parti diverse del progetto. Questo argomento suggerisce uno schema per suddividere l'applicazione in più parti, che corrispondono ai livelli di un diagramma su livelli generale.  
  
 Per iniziare rapidamente un progetto o un sottoprogetto, è utile avere un modello di progetto basato sulla struttura del progetto scelta. Questo argomento descrive come creare e usare tale modello.  
  
 Questo argomento presuppone che si lavori su un progetto abbastanza grande per richiedere la collaborazione di più membri del team ed eventualmente di più team. Il codice e i modelli del progetto sono archiviati in un sistema di controllo del codice sorgente quale [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]. Almeno alcuni membri del team usano Visual Studio per sviluppare i modelli, mentre altri membri possono visualizzarli con altre versioni di Visual Studio.  
  
 Per informazioni sulle versioni di Visual Studio supportano ogni strumento e funzionalità di modellazione, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="solution-structure"></a>Struttura della soluzione  
 In un progetto di medie o grandi dimensioni, la struttura del team riflette la struttura dell'applicazione. Ogni team usa una soluzione di Visual Studio.  
  
#### <a name="to-divide-an-application-into-layers"></a>Per suddividere un'applicazione in livelli  
  
1. Basare la struttura delle soluzioni sulla struttura dell'applicazione, ad esempio applicazione Web, applicazione di servizio o applicazione desktop. Viene illustrata un'ampia gamma di architetture comuni in [archetipi nella Guida all'architettura dell'applicazione di Microsoft](http://go.microsoft.com/fwlink/?LinkId=196681).  
  
2. Creare una soluzione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], che verrà denominata soluzione Architecture. Questa soluzione verrà usata per creare la progettazione complessiva del sistema. Conterrà modelli ma non il codice.  
  
    Aggiungere un diagramma livello alla soluzione. Nel diagramma livello tracciare l'architettura scelta per l'applicazione. Ad esempio, il diagramma potrebbe mostrare i seguenti livelli con le reciproche dipendenze: presentazione, logica di business e dati.  
  
    È possibile creare il diagramma livello e una nuova soluzione di Visual Studio nello stesso momento usando il **nuovo diagramma livello o UML** comando le **architettura** menu.  
  
3. Aggiungere al modello Architecture i diagrammi UML che rappresentano i concetti aziendali più importanti e i casi di utilizzo ai quali viene fatto riferimento nella progettazione di tutti i livelli.  
  
4. Creare una soluzione di Visual Studio separata per ogni livello del diagramma livello Architecture.  
  
    Queste soluzioni verranno usate per sviluppare il codice dei livelli.  
  
5. Creare i modelli UML che rappresenteranno le progettazioni dei livelli e i concetti comuni a tutti i livelli. Disporre i modelli in modo che si possano visualizzare tutti dalla soluzione Architecture e che da ogni livello sia possibile visualizzare i relativi modelli.  
  
    È possibile ottenere questo risultato con una delle procedure seguenti. La prima consente di creare un progetto di modello separato per ogni livello, mentre la seconda permette di creare un unico progetto di modello condiviso tra i livelli.  
  
   ###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Per usare un progetto di modello separato per ogni livello  
  
   1. Creare un progetto di modello nella soluzione di ogni livello.  
  
       Questo modello conterrà i diagrammi UML che descrivono i requisiti e la progettazione dello livello in questione. Può anche contenere diagrammi livello che mostrano i livelli annidati.  
  
       A questo punto è disponibile un modello per ogni livello, oltre a un modello per l'architettura dell'applicazione. Ogni modello è contenuto in una soluzione separata. In questo modo, i membri del team possono lavorare contemporaneamente sugli stessi livelli.  
  
   2. Aggiungere alla soluzione Architecture il progetto di modellazione della soluzione di ogni livello. A questo scopo, aprire la soluzione Architecture. In Esplora soluzioni, fare clic sul nodo della soluzione, scegliere Aggiungi e quindi fare clic su **progetto esistente**. Passare al progetto di modellazione (con estensione modelproj) in una soluzione del livello.  
  
       Ogni modello è ora visibile in due soluzioni: la relativa soluzione principale e la soluzione Architecture.  
  
   3. Aggiungere un diagramma livello al progetto di modello di ogni livello. Iniziare con una copia del diagramma livello Architecture. È possibile eliminare le parti che non sono dipendenze del diagramma livello.  
  
       È anche possibile aggiungere diagrammi livello che rappresentano la struttura dettagliata del livello specifico.  
  
       Questi diagrammi vengono usati per convalidare il codice sviluppato nel livello.  
  
   4. Nella soluzione Architecture modificare i requisiti e i modelli di progettazione di tutti i livelli tramite Visual Studio.  
  
       Nella soluzione di ogni livello sviluppare il codice relativo al livello specifico, facendo riferimento al modello. Se si ritiene sufficiente eseguire lo sviluppo senza usare lo stesso computer per aggiornare il modello, è possibile leggere il modello e sviluppare codice usando versioni di Visual Studio che non consentono di creare modelli. È anche possibile generare codice dal modello in queste versioni.  
  
      Questo metodo assicura che non ci saranno interferenze da parte degli sviluppatori che modificano contemporaneamente i modelli di livello.  
  
      Tuttavia, poiché i modelli sono separati, è difficile fare riferimento a concetti comuni. Ogni modello deve disporre di una copia distinta degli elementi degli altri livelli e dell'architettura dai quali dipende. Il diagramma livello di ogni livello deve essere costantemente sincronizzato con il diagramma livello Architecture. È difficile mantenere la sincronizzazione quando questi elementi sono soggetti a modifica, anche se è possibile sviluppare appositi strumenti a questo scopo.  
  
   ###### <a name="to-use-a-separate-package-for-each-layer"></a>Per usare un pacchetto separato per ogni livello  
  
   1. Aggiungere il progetto di modello Architecture alla soluzione di ogni livello. In Esplora soluzioni, fare clic sul nodo della soluzione, scegliere **Add**, quindi fare clic su **progetto esistente**. A questo punto, è possibile accedere da qualsiasi soluzione al singolo progetto di modello, ossia al progetto Architecture e al progetto di sviluppo per ogni livello.  
  
   2. Nel modello UML condiviso creare un pacchetto per ogni livello. In Esplora soluzioni selezionare il progetto di modello. In Esplora modelli UML, fare clic sul nodo radice del modello, scegliere **Add**, quindi fare clic su **pacchetto**.  
  
       Ogni pacchetto conterrà i diagrammi UML che descrivono i requisiti e la progettazione del livello corrispondente.  
  
   3. Se necessario, aggiungere diagrammi livello locali per la struttura interna di ogni livello.  
  
      Questo metodo consente agli elementi di progettazione di ogni livello di fare riferimento direttamente agli elementi degli altri livelli e dell'architettura comune da cui dipendono.  
  
      Anche se è possibile che operazioni simultanee su pacchetti diversi causino alcuni conflitti, questi risulteranno abbastanza facili da gestire, in quanto i pacchetti vengono archiviati in file separati. La difficoltà principale si verifica quando si elimina un elemento a cui viene fatto riferimento in un pacchetto dipendente. Per altre informazioni, vedere [gestire modelli e diagrammi nel controllo della versione](../modeling/manage-models-and-diagrams-under-version-control.md).  
  
## <a name="creating-architecture-templates"></a>Creazione di modelli dell'architettura  
 Nella pratica, non si creeranno tutte le soluzioni di Visual Studio contemporaneamente, ma se ne aggiungeranno di nuove man mano che il progetto procede. Probabilmente si userà anche la stessa struttura della soluzione nei progetti successivi.  Per velocizzare la creazione di nuove soluzioni, è possibile creare un modello di soluzione o di progetto. È possibile acquisire il modello in un'estensione VSIX ( Visual Studio Integration Extension) per facilitarne la distribuzione e l'installazione in altri computer.  
  
 Ad esempio, se si usano spesso soluzioni con livelli presentazione, aziendale e dati, è possibile configurare un modello per creare nuove soluzioni con la medesima struttura.  
  
#### <a name="to-create-a-solution-template"></a>Per creare un modello di soluzione  
  
1.  [Scaricare e installare l'esportazione guidata modelli](http://go.microsoft.com/fwlink/?LinkId=196686), se non è stato già fatto.  
  
2.  Creare la struttura della soluzione da usare come punto di partenza per i progetti futuri.  
  
3.  Scegliere **Esporta modello come VSIX** dal menu **File**. Il **Esporta modello come VSIX guidata** apre.  
  
4.  Seguendo le istruzioni della procedura guidata, selezionare i progetti da includere nel modello, fornire un nome e una descrizione per il modello e specificare un percorso di output.  
  
> [!NOTE]
>  Il materiale contenuto in questo argomento è tratto e adattato dalla documentazione Visual Studio Architecture Tooling Guidance, redatta dai membri del gruppo Visual Studio ALM Rangers, una collaborazione tra Most Valued Professional (MVP), Microsoft Services e i team e i writer del prodotto Visual Studio. [Fare clic qui per scaricare il pacchetto completo di indicazioni.](http://go.microsoft.com/fwlink/?LinkID=191984)  
  
## <a name="related-materials"></a>Materiali correlati  
 [Organizzare e gestire i modelli](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-9-Organizing-and-Managing-Your-Models/) - video a cura di Clint Edmondson.  
  
 [Visual Studio Architecture Tooling Guidance](../modeling/visual-studio-architecture-tooling-guidance.md) : indicazioni aggiuntive sulla gestione dei modelli in un team  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire modelli e diagrammi nel controllo della versione](../modeling/manage-models-and-diagrams-under-version-control.md)   
 [Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)




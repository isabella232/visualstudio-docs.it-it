---
title: Finestra di dialogo Progetti e soluzioni, Opzioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 245b453a3020e79b924cb8058ff392bd59673402
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662128"
---
# <a name="projects-and-solutions-options-dialog-box"></a>Progetti e soluzioni, Opzioni (finestra di dialogo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Imposta il percorso predefinito delle cartelle di progetto [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e determina il comportamento predefinito della finestra **Output**, dell'**Elenco attività** e di **Esplora soluzioni** durante lo sviluppo e la compilazione dei progetti. Per accedere a questa finestra di dialogo, fare clic su **Strumenti/Opzioni**, espandere **Progetti e soluzioni** e fare clic su **Generale**.

> [!NOTE]
> Le opzioni disponibili nelle finestre di dialogo e i nomi e i percorsi dei comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida a seconda dell'edizione o delle impostazioni attive. Questo argomento della Guida è stato creato tenendo presente le **Impostazioni generali per lo sviluppo**. Per visualizzare o modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti**. Per altre informazioni, vedere [personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Impostazioni
 **Percorso progetti** Imposta il percorso predefinito in cui vengono creati i nuovi progetti e le cartelle e le directory della soluzione. Anche diverse finestre di dialogo usano il percorso impostato in questa opzione come punto di partenza della cartella. Ad esempio, la finestra di dialogo Apri progetto usa questo percorso per il collegamento Progetti.

 **Percorso modelli di progetto utente** Imposta il percorso predefinito usato dalla finestra di dialogo **nuovo progetto** per creare l'elenco di **modelli personali**. Per altre informazioni, vedere [procedura: individuare e organizzare modelli](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

 **Percorso modelli di elemento utente** Imposta il percorso predefinito usato dalla finestra di dialogo **Aggiungi nuovo elemento** per creare l'elenco di **modelli personali**. Per altre informazioni, vedere [procedura: individuare e organizzare modelli](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

 **Mostra sempre elenco errori se la compilazione termina con errori** Apre la finestra di **Elenco errori** al completamento della compilazione, solo se non è stato possibile compilare un progetto. Vengono visualizzati gli errori che si sono verificati durante il processo di compilazione. Quando questa opzione è deselezionata, gli errori si verificano ugualmente, ma la finestra non verrà aperta una volta completata la compilazione. Questa opzione è attivata per impostazione predefinita.

 **Rileva elemento attivo nel Esplora soluzioni** Quando questa opzione è selezionata, **Esplora soluzioni** viene aperto automaticamente e l'elemento attivo viene selezionato. L'elemento selezionato cambia quando si lavora con diversi file in un progetto o soluzione oppure componenti diversi in una finestra di progettazione. Quando questa opzione è deselezionata, la selezione in **Esplora soluzioni** non viene modificata automaticamente. Questa opzione è attivata per impostazione predefinita.

 **Mostra configurazioni di compilazione avanzate** Se selezionata, le opzioni di configurazione della compilazione vengono visualizzate nella finestra di dialogo **pagine delle proprietà del progetto** e nella finestra di dialogo Pagine delle proprietà della **soluzione** . Se deselezionata, le opzioni di configurazione di compilazione non vengono visualizzate nella finestra di dialogo **Pagine delle proprietà** del progetto e nella finestra di dialogo **Pagine delle proprietà** della soluzione per i progetti [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] e [!INCLUDE[csprcs](../../includes/csprcs-md.md)] che contengono una sola configurazione oppure le due configurazioni debug e rilascio. Se un progetto ha una configurazione definita dall'utente, verranno visualizzate le opzioni di configurazione di compilazione.

 Se è deselezionata, i comandi del menu **Compila**, ad esempio **Compila soluzione**, **Ricompila soluzione** e **Pulisci soluzione**, vengono eseguiti nella configurazione Rilascio e i comandi dal menu **Debug**, ad esempio **Avvia il debug** e **Avvia senza eseguire debug**, vengono eseguiti nella configurazione Debug.

 **Mostra sempre soluzione** Quando questa opzione è selezionata, la soluzione e tutti i comandi che agiscono sulle soluzioni vengono sempre visualizzati nell'IDE. Se deselezionata, tutti i progetti vengono creati come progetti autonomi e la soluzione non viene visualizzata in Esplora soluzioni o i comandi che agiscono sulle soluzioni non vengono visualizzati nell'IDE se la soluzione contiene un solo progetto.

 **Salva nuovi progetti al momento della creazione** Quando questa opzione è selezionata, è possibile specificare un percorso per il progetto nella finestra di dialogo **nuovo progetto** . Se deselezionata, tutti i nuovi progetti vengono creati come progetti temporanei. Quando si lavora con i progetti temporanei, è possibile creare ed effettuare prove con un progetto senza dover specificare un percorso sul disco.

 **Avvisa utente quando il percorso del progetto non è attendibile** Se si tenta di creare un nuovo progetto o di aprire un progetto esistente in una posizione non completamente attendibile (ad esempio, in un percorso UNC o un percorso HTTP), viene visualizzato un messaggio. Usare questa opzione per specificare se il messaggio viene visualizzato ogni volta che si prova a creare o ad aprire un progetto in una posizione non completamente attendibile.

 **Mostra finestra di output all'avvio della compilazione** Visualizza automaticamente il Finestra di output nell'IDE all'inizio delle compilazioni di soluzioni. Per altre informazioni, vedere [Procedura: Controllare la finestra di output](https://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858). Questa opzione è attivata per impostazione predefinita.

 **Richiedi ridenominazione simbolica quando i file vengono rinominati** Quando questa opzione è selezionata, viene visualizzata una finestra di messaggio in cui viene chiesto se [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rinominare anche tutti i riferimenti nel progetto all'elemento di codice.

## <a name="see-also"></a>Vedere anche
 [Finestra di dialogo Opzioni, progetti e soluzioni, compila ed Esegui](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)

---
title: Installare e gestire contenuto locale | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer 2.0]
- updating local content [Help Viewer 2.0]
- Help Viewer 2.0, content installation source
- Help Viewer 2.0, updating local content
- Help Viewer 2.0, changing content installation source
- installing local content [Help Viewer 2.0]
- content installation source [Help Viewer 2.0]
- downloading content [Help Viewer 2.0]
- removing local content [Help Viewer 2.0]
- Help Viewer 2.0, removing local content
- Help Viewer 2.0, installing local content
- Help Viewer 2.0, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7b8a67a9105314ad73076d3a8b12d51c23f83097
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832732"
---
# <a name="install-and-manage-local-content"></a>Installare e gestire il contenuto locale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usare Microsoft Help Viewer per aggiungere, rimuovere, aggiornare e spostare il contenuto della Guida installato nel computer a seconda delle esigenze di sviluppo del software.  
  
 Per gestire il contenuto nel computer locale, è necessario accedere con un account che disponga di autorizzazioni amministrative. Inoltre, si potrebbe non essere in grado di gestire il contenuto locale se si lavora in un ambiente aziendale poiché gli amministratori di sistema potrebbero prendere tali decisioni per l'organizzazione. Per altre informazioni, vedere la [Guida dell'amministratore di Help Viewer](../ide/help-viewer-administrator-guide.md).  
  
## <a name="changing-the-content-installation-source"></a>Modifica dell'origine di installazione del contenuto  
 Per impostazione predefinita, Help Viewer installa il contenuto tramite un servizio online Microsoft come origine. Non è in genere necessario modificare l'origine del contenuto a meno che non si utilizzi un ambiente aziendale per cui un amministratore di sistema abbia già installato il contenuto in un'altra posizione.  
  
#### <a name="to-change-the-content-installation-source"></a>Per modificare l'origine di installazione del contenuto  
  
1.  Nella scheda **Gestisci contenuto** scegliere il pulsante di opzione **Disco**.  
  
    > [!NOTE]
    >  L'opzione **Disco** non sarà disponibile se l'amministratore ha impedito di modificare l'origine di installazione del contenuto. Per altre informazioni, vedere la [Guida dell'amministratore di Help Viewer](../ide/help-viewer-administrator-guide.md).  
  
2.  Effettuare uno dei passaggi indicati di seguito.  
  
    -   Immettere il percorso di un file con estensione msha o l'URL di un endpoint del servizio.  
  
    -   Scegliere il pulsante Sfoglia (**…**) per trovare un file con estensione MSHA.  
  
    -   Nell'elenco scegliere la voce che è stata usata più di recente.  
  
## <a name="download-and-install-content-locally"></a>Scaricare e installare il contenuto localmente  
 È possibile visualizzare gli argomenti senza una connessione Internet se si scarica e installa il contenuto nel computer locale.  
  
> [!IMPORTANT]
>  Per installare il contenuto, è necessario accedere con un account che disponga di autorizzazioni amministrative.  
  
 Se l'IDE di Visual Studio è impostato su una lingua diversa dall'inglese, è possibile installare il contenuto in inglese o il contenuto localizzato oppure entrambi i contenuti. Non verrà tuttavia visualizzato alcun contenuto se si installa solo la versione inglese e la casella di controllo **Includi contenuto in inglese in tutte le schede di navigazione e nelle richieste F1** nella finestra di dialogo **Opzioni visualizzatore** è deselezionata.  
  
#### <a name="to-download-and-install-content"></a>Per scaricare e installare il contenuto  
  
1.  Scegliere la scheda **Gestisci contenuto**.  
  
2.  Nell'elenco del contenuto scegliere il collegamento **Aggiungi** accanto al libro o ai libri da scaricare e installare.  
  
     Il libro viene aggiunto all'elenco **Modifiche in sospeso** e le dimensioni stimate del libro o dei libri specificati vengono visualizzate al di sotto dell'elenco. Poiché alcuni argomenti sono presenti in più libri, le dimensioni complessive del download di più libri potrebbe essere inferiore alla somma delle dimensioni di ogni singolo libro specificato.  
  
3.  Scegliere il pulsante **Aggiorna**.  
  
     Il libro o i libri specificati vengono installati con tutti gli aggiornamenti dei libri già presenti nel computer. I tempi di installazione variano, ma è possibile visualizzare lo stato di avanzamento nella barra di stato.  
  
## <a name="removing-local-content"></a>Rimozione del contenuto locale  
 È possibile risparmiare spazio su disco rimuovendo il contenuto non desiderato dal computer.  
  
> [!IMPORTANT]
>  Per rimuovere il contenuto è necessario disporre di autorizzazioni amministrative.  
  
 Non verrà visualizzato nessun contenuto se l'IDE di Visual Studio viene impostato su una lingua diversa dall'inglese, se si rimuove il contenuto localizzato e se la casella di controllo **Includi contenuto in inglese in tutte le schede di navigazione e nelle richieste F1** nella finestra di dialogo **Opzioni visualizzatore** è deselezionata.  
  
#### <a name="to-remove-content"></a>Per rimuovere il contenuto  
  
1.  Scegliere la scheda **Gestisci contenuto**.  
  
2.  Nell'elenco del contenuto scegliere il collegamento **Rimuovi** accanto al libro o ai libri da rimuovere.  
  
     Il libro viene aggiunto all'elenco **Modifiche in sospeso**.  
  
3.  Scegliere il pulsante **Aggiorna**.  
  
     Il libro o i libri specificati vengono rimossi dal computer.  
  
## <a name="updating-local-content"></a>Aggiornamento del contenuto locale  
 Nella barra di stato viene indicato quando sono disponibili aggiornamenti del contenuto installato.  
  
> [!IMPORTANT]
>  Se si vuole che Help Viewer controlli automaticamente la disponibilità di aggiornamenti online, è necessario aprire la finestra di dialogo **Opzioni visualizzatore** e selezionare la casella di controllo **Connetti per verificare la disponibilità di aggiornamenti**.  
  
#### <a name="to-update-local-content"></a>Per aggiornare il contenuto locale  
  
- Nell'angolo inferiore destro della barra di stato scegliere il collegamento **Fare clic qui per scaricare ora**.  
  
  I tempi di aggiornamento possono variare ma è possibile visualizzare lo stato di avanzamento dell'aggiornamento nella barra di stato.  
  
## <a name="moving-local-content"></a>Spostamento del contenuto locale  
 È possibile risparmiare spazio su disco spostando il contenuto installato dal computer locale in una condivisione di rete o in un'altra partizione nel computer locale.  
  
> [!IMPORTANT]
>  Per spostare il contenuto, è necessario accedere con un account che disponga di autorizzazioni amministrative.  
  
#### <a name="to-move-local-content"></a>Per spostare il contenuto locale  
  
1.  Nella scheda **Gestisci contenuto** scegliere il pulsante **Sposta** che si trova sotto **Percorso archivio locale**.  
  
     Verrà visualizzata la finestra di dialogo **Sposta contenuto**.  
  
2.  Nella casella di testo **A** immettere un percorso diverso per il contenuto e quindi scegliere **OK**.  
  
3.  Scegliere **Chiudi** dopo che il contenuto è stato spostato.  
  
## <a name="see-also"></a>Vedere anche  
 [Microsoft Help Viewer](../ide/microsoft-help-viewer.md)




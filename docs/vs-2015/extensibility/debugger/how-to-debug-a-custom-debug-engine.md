---
title: 'Procedura: Eseguire il debug di un motore di Debug personalizzato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5292d2cde8a75a239f7a905d8cf5d80b09a8f61e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954541"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Procedura: Eseguire il debug di un motore di Debug personalizzato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un tipo di progetto avvia il motore di debug (DE) dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> (metodo). Ciò significa che viene avviata la Germania sotto il controllo dell'istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] controllo del tipo di progetto. Tuttavia, tale istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] non è possibile eseguire il debug di DE. Di seguito sono i passaggi per consentire il debug di DE personalizzato.  
  
> [!NOTE]
>  :     Nella procedura "Debug di un motore di Debug di Custom", è necessario attendere il DE avviare prima di collegare ad esso. Se si inserisce una finestra di messaggio verso l'inizio del DE che viene visualizzato quando viene avviata la Germania, è possibile collegare a questo punto e quindi deselezionare la casella di messaggio per continuare. In questo modo, è possibile intercettare tutti gli eventi DE.  
  
> [!WARNING]
>  È necessario che il debug remoto installato prima di provare le procedure seguenti. Visualizzare [debug remoto](../../debugger/remote-debugging.md) per informazioni dettagliate.  
  
### <a name="debugging-a-custom-debug-engine"></a>Debug di un motore di Debug personalizzato  
  
1.  Avviare msvsmon.exe, Remote Debugging Monitor.  
  
2.  Dal **strumenti** dal menu msvsmon.exe, selezionare **opzioni** per aprire il **opzioni** nella finestra di dialogo.  
  
3.  Selezionare l'opzione "Nessuna autenticazione" e fare clic su **OK**.  
  
4.  Avviare un'istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e aprire il progetto DE personalizzato.  
  
5.  Avviare una seconda istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e aprire un progetto personalizzato che consente di avviare il DE (per lo sviluppo, si tratta in genere nell'hive del Registro di sistema sperimentale impostato quando viene installato VSIP).  
  
6.  In questa seconda istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], caricare un file di origine da un progetto personalizzato e avviare il programma da sottoporre a debug. Attendere qualche minuto per consentire il DE al caricamento o attendere fino a quando non viene raggiunto un punto di interruzione.  
  
7.  La prima istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (con il progetto DE), selezionare **Connetti a processo** dal **Debug** menu.  
  
8.  Nel **Connetti a processo** della finestra di dialogo Modifica il **trasporto** al **remoto (solo nativo senza autenticazione)**.  
  
9. Modifica il **qualificatore** sul nome del computer (Nota: è presente una cronologia delle voci, pertanto è necessario digitare il nome una sola volta).  
  
10. Nel **processi disponibili** , selezionare l'istanza del DE che sia in esecuzione e fare clic sui **Attach** pulsante.  
  
11. Dopo che i simboli sono caricati nel DE, posizionare punti di interruzione nel codice DE.  
  
12. Ogni volta che si arresta e quindi riavviarla il processo di debug, ripetere i passaggi da 6 a 10.  
  
### <a name="debugging-a-custom-project-type"></a>Debug di un tipo di progetto personalizzati  
  
1.  Avviare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in hive del Registro di sistema normale e carica il progetto digitare progetto (si tratta, l'origine per il tipo di progetto, non un'istanza del tipo di progetto).  
  
2.  Aprire le proprietà del progetto e passare al **Debug** pagina. Per il **comando**, digitare il percorso per il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (per impostazione predefinita, si tratta *[disco]* \Programmi\Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 8\Common7\IDE\devenv.exe).  
  
3.  Per il **argomenti del comando**, tipo `/rootsuffix exp` per hive del Registro di sistema sperimentale (creato durante l'installazione di VSIP).  
  
4.  Fai clic su **OK** per accettare le modifiche.  
  
5.  Avviare il tipo di progetto premendo F5. Verrà avviata una seconda istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
6.  A questo punto, è possibile inserire i punti di interruzione nel codice di origine del tipo di progetto.  
  
7.  Nella seconda istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], caricare o creare una nuova istanza del tipo di progetto. Durante il caricamento o la creazione, è possibile raggiungere i punti di interruzione.  
  
8.  Eseguire il debug del tipo di progetto.  
  
9. Se si sceglie per il debug del processo di avvio un CRI, è possibile eseguire i passaggi nella procedura "Il debug di un motore di Debug di personalizzata" per collegare il DE dopo che viene avviata. Si otterrà le tre istanze di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in esecuzione: una per l'origine di tipo di progetto, l'altra per il tipo di progetto creata un'istanza e un terzo collegati per la Germania.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)

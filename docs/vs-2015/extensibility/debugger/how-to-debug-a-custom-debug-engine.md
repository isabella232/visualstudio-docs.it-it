---
title: 'Procedura: eseguire il debug di un motore di debug personalizzato | Microsoft Docs'
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
ms.openlocfilehash: b7e710cec4536a5a1327580e56c60cb23ca36f4c
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2020
ms.locfileid: "90839559"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Procedura: Eseguire il debug di un motore di debug personalizzato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un tipo di progetto avvia il motore di debug (DE) dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metodo. Ciò significa che la DE viene avviata sotto il controllo dell'istanza di che [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Controlla il tipo di progetto. Tuttavia, l'istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] non è in grado di eseguire il debug di de. Di seguito sono riportati i passaggi necessari per eseguire il debug del DE personalizzato.  
  
> [!NOTE]
> : Nella procedura "debug di un motore di debug personalizzato" è necessario attendere l'avvio di DE prima che sia possibile connettersi a esso. Se si inserisce una finestra di messaggio in prossimità dell'inizio del DE visualizzato all'avvio di DE, è possibile connettersi a tale punto, quindi deselezionare la finestra di messaggio per continuare. In questo modo, è possibile intercettare tutti gli eventi DE.  
  
> [!WARNING]
> Prima di eseguire le procedure riportate di seguito, è necessario che sia installato il debug remoto. Per informazioni dettagliate, vedere [debug remoto](../../debugger/remote-debugging.md) .  
  
### <a name="debugging-a-custom-debug-engine"></a>Debug di un motore di debug personalizzato  
  
1. Avviare msvsmon.exe, Remote Debug Monitor.  
  
2. Scegliere **Opzioni** dal menu **strumenti** in msvsmon.exe per aprire la finestra di dialogo **Opzioni** .  
  
3. Selezionare l'opzione "Nessuna autenticazione" e fare clic su **OK**.  
  
4. Avviare un'istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e aprire il progetto personalizzato di.  
  
5. Avviare una seconda istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e aprire il progetto personalizzato che avvia il de (per lo sviluppo, si tratta in genere dell'hive del registro di sistema sperimentale configurato al momento dell'installazione di VSIP).  
  
6. In questa seconda istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , caricare un file di origine dal progetto personalizzato e avviare il programma di cui eseguire il debug. Attendere alcuni istanti per consentire il caricamento del DE o attendere il raggiungimento di un punto di interruzione.  
  
7. Nella prima istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (con il progetto de) selezionare **Connetti a processo** dal menu **debug** .  
  
8. Nella finestra di dialogo **Connetti a processo** modificare il **trasporto** in **remoto (solo nativo senza autenticazione)**.  
  
9. Modificare il **qualificatore** con il nome del computer (Nota: è presente una cronologia delle voci, quindi è necessario digitare questo nome una sola volta).  
  
10. Nell'elenco **processi disponibili** selezionare l'istanza del de che esegue e fare clic sul pulsante **Connetti** .  
  
11. Dopo che i simboli sono stati caricati nel DE, inserire i punti di interruzione nel codice DE.  
  
12. Ogni volta che si arresta e quindi si riavvia il processo di debug, ripetere i passaggi da 6 a 10.  
  
### <a name="debugging-a-custom-project-type"></a>Debug di un tipo di progetto personalizzato  
  
1. Avviare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] il normale hive del registro di sistema e caricare il progetto del tipo di progetto, ovvero l'origine del tipo di progetto, non la creazione di un'istanza del tipo di progetto.  
  
2. Aprire le proprietà del progetto e passare alla pagina **debug** . Per il **comando**, digitare il percorso dell' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (per impostazione predefinita, è *[unità]* \Programmi\Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 8\Common7\IDE\devenv.exe).  
  
3. Per gli **argomenti del comando**, digitare `/rootsuffix exp` per l'hive del registro di sistema sperimentale, creato al momento dell'installazione di VSIP.  
  
4. Fai clic su **OK** per accettare le modifiche.  
  
5. Avviare il tipo di progetto premendo F5. Verrà avviata una seconda istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
6. A questo punto, è possibile inserire punti di interruzione nel codice sorgente del tipo di progetto.  
  
7. Nella seconda istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , caricare o creare una nuova istanza del tipo di progetto. Durante il caricamento o la creazione, è possibile che vengano raggiunti i punti di interruzione.  
  
8. Eseguire il debug del tipo di progetto.  
  
9. Se si sceglie di eseguire il debug del processo di avvio di un DE, è possibile eseguire i passaggi descritti nella procedura "debug di un motore di debug personalizzato" per connettersi al DE dopo l'avvio. In questo modo si otterranno tre istanze di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in esecuzione: una per l'origine del tipo di progetto, una seconda per il tipo di progetto di cui è stata creata un'istanza e una terza collegata alla de.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)

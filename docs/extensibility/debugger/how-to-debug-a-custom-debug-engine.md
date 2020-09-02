---
title: 'Procedura: eseguire il debug di un motore di debug personalizzato | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a65e69655c4e8699bd267f1835ec0c49603014d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903310"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Procedura: eseguire il debug di un motore di debug personalizzato
Un tipo di progetto avvia il motore di debug (DE) dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metodo. Ciò significa che la DE viene avviata sotto il controllo dell'istanza di che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Controlla il tipo di progetto. Tuttavia, l'istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non è in grado di eseguire il debug di de. Di seguito sono riportati i passaggi che consentono di eseguire il debug della DE personalizzata.

> [!NOTE]
> : Nella procedura "debug di un motore di debug personalizzato" è necessario attendere l'avvio di DE prima che sia possibile connettersi a esso. Se si inserisce una finestra di messaggio in prossimità dell'inizio del DE visualizzato all'avvio di DE, è possibile connettersi a tale punto, quindi deselezionare la finestra di messaggio per continuare. In questo modo, è possibile intercettare tutti gli eventi DE.

> [!WARNING]
> Prima di eseguire le procedure riportate di seguito, è necessario che sia installato il debug remoto. Per informazioni dettagliate, vedere [debug remoto](../../debugger/remote-debugging.md) .

## <a name="debug-a-custom-debug-engine"></a>Eseguire il debug di un motore di debug personalizzato

1. Avviare *msvsmon.exe*, Remote Debug Monitor.

2. Scegliere **Opzioni** dal menu **strumenti** in *msvsmon.exe*per aprire la finestra di dialogo **Opzioni** .

3. Selezionare l'opzione "Nessuna autenticazione" e fare clic su **OK**.

4. Avviare un'istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e aprire il progetto personalizzato di.

5. Avviare una seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e aprire il progetto personalizzato che avvia il de (per lo sviluppo, si tratta in genere dell'hive del registro di sistema sperimentale configurato al momento dell'installazione di VSIP).

6. In questa seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , caricare un file di origine dal progetto personalizzato e avviare il programma di cui eseguire il debug. Attendere alcuni istanti per consentire il caricamento del DE o attendere il raggiungimento di un punto di interruzione.

7. Nella prima istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (con il progetto de) selezionare **Connetti a processo** dal menu **debug** .

8. Nella finestra di dialogo **Connetti a processo** modificare il **trasporto** in **remoto (solo nativo senza autenticazione)**.

9. Modificare il **qualificatore** con il nome del computer (Nota: è presente una cronologia delle voci, quindi è necessario digitare questo nome una sola volta).

10. Nell'elenco **processi disponibili** selezionare l'istanza del de che esegue e fare clic sul pulsante **Connetti** .

11. Dopo che i simboli sono stati caricati nel DE, inserire i punti di interruzione nel codice DE.

12. Ogni volta che si arresta e quindi si riavvia il processo di debug, ripetere i passaggi da 6 a 10.

## <a name="debug-a-custom-project-type"></a>Eseguire il debug di un tipo di progetto personalizzato

1. Avviare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il normale hive del registro di sistema e caricare il progetto del tipo di progetto, ovvero l'origine del tipo di progetto, non la creazione di un'istanza del tipo di progetto.

2. Aprire le proprietà del progetto e passare alla pagina **debug** . Per il **comando**, digitare il percorso dell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (per impostazione predefinita, è *[unità]* \Programmi\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).

3. Per gli **argomenti del comando**, digitare `/rootsuffix exp` per l'hive del registro di sistema sperimentale, creato al momento dell'installazione di VSIP.

4. Fai clic su **OK** per accettare le modifiche.

5. Avviare il tipo di progetto premendo **F5**. Viene avviata una seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

6. A questo punto, è possibile inserire punti di interruzione nel codice sorgente del tipo di progetto.

7. Nella seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , caricare o creare una nuova istanza del tipo di progetto. Durante il caricamento o la creazione, è possibile che vengano raggiunti i punti di interruzione.

8. Eseguire il debug del tipo di progetto.

9. Se si sceglie di eseguire il debug del processo di avvio di un DE, è possibile eseguire i passaggi descritti nella procedura "debug di un motore di debug personalizzato" per connettersi al DE dopo l'avvio. In questo modo sono presenti tre istanze di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in esecuzione: una per l'origine del tipo di progetto, una seconda per il tipo di progetto di cui è stata creata un'istanza e una terza collegata alla de.

## <a name="see-also"></a>Vedere anche
- [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)

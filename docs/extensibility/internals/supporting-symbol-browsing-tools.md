---
title: Supporto degli strumenti per l'esplorazione di simboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca171fa75adda3deef5b941852fc3e6c648c84c6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723078"
---
# <a name="supporting-symbol-browsing-tools"></a>Supporto degli strumenti di esplorazione dei simboli
Gli strumenti **Visualizzatore oggetti**, **Visualizzazione classi**, **Visualizzatore chiamate** e **Trova simbolo** forniscono funzionalità di esplorazione dei simboli in Visual Studio. Questi strumenti visualizzano visualizzazioni ad albero gerarchico dei simboli e mostrano le relazioni tra i simboli nell'albero. I simboli possono rappresentare gli spazi dei nomi, gli oggetti, le classi, i membri della classe e altri elementi del linguaggio contenuti in diversi componenti. I componenti includono i progetti di Visual Studio, i componenti di .NET Framework esterni e le librerie di tipo (tlb). Per altre informazioni, vedere [Viewing the Structure of Code](../../ide/viewing-the-structure-of-code.md) (Visualizzazione della struttura del codice).

## <a name="symbol-browsing-libraries"></a>Librerie di esplorazione simboli
 In qualità di implementatore di linguaggi, è possibile estendere le funzionalità di esplorazione dei simboli di Visual Studio creando librerie che tengono traccia dei simboli nei componenti e forniscono gli elenchi di simboli al gestore oggetti di Visual Studio tramite un set di interfacce. Una libreria è descritta dall'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>. Il gestore oggetti di Visual Studio risponde alle richieste di nuovi dati dagli strumenti di esplorazione dei simboli ottenendo i dati dalle librerie e organizzando il relativo. Successivamente, compila o aggiorna gli strumenti con i dati richiesti. Per ottenere un riferimento al gestore oggetti di Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> passare l'ID del servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> al metodo `GetService`.

 Ogni libreria deve eseguire la registrazione con il gestore oggetti di Visual Studio, che raccoglie le informazioni su tutte le librerie. Per registrare una raccolta, chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>. A seconda dello strumento che avvia la richiesta, il gestore oggetti di Visual Studio trova la libreria appropriata e richiede i dati. I dati vengono trasmessi tra le librerie e il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestione oggetti negli elenchi di simboli descritti dall'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>.

 @No__t_0 Object Manager è responsabile dell'aggiornamento periodico degli strumenti di esplorazione dei simboli in modo da riflettere i dati più recenti contenuti nelle librerie.

 Il diagramma seguente contiene un esempio di elementi principali del processo di richiesta/scambio di dati tra una libreria e il gestore oggetti di Visual Studio. Le interfacce nel diagramma fanno parte di un'applicazione di codice gestito.

 ![Flusso di dati tra una libreria e gestione oggetti](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Per fornire gli elenchi di simboli al gestore oggetti di Visual Studio, è necessario prima registrare la libreria con gestione oggetti di Visual Studio chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>. Una volta registrata la libreria, il gestore oggetti di Visual Studio richiede alcune informazioni sulle funzionalità della libreria. Ad esempio, richiede i flag della libreria e le categorie supportate chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> metodi. A un certo punto, quando uno degli strumenti richiede dati da questa libreria, il gestore di oggetti richiede l'elenco di simboli di primo livello chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>. In risposta, la libreria produce un elenco di simboli e lo espone al gestore oggetti di Visual Studio tramite l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>. Il gestore di oggetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina il numero di elementi presenti nell'elenco chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>. Tutte le richieste seguenti sono correlate a un determinato elemento dell'elenco e forniscono il numero di indice dell'elemento in ogni richiesta. Il gestore oggetti di Visual Studio continua a raccogliere le informazioni sul tipo, l'accessibilità e altre proprietà dell'elemento chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>.

 Determina il nome dell'elemento chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> e richiede le informazioni sull'icona chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>. L'icona viene visualizzata a sinistra del nome dell'elemento e rappresenta il tipo dell'elemento, l'accessibilità e altre proprietà.

 Il gestore di oggetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiama il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> per determinare se un determinato elemento dell'elenco è espandibile e contiene elementi figlio. Se l'interfaccia utente invia una richiesta per espandere un elemento, il gestore di oggetti richiede l'elenco di simboli figlio chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>. Il processo continua con parti diverse dell'albero compilato su richiesta.

> [!NOTE]
> Per implementare un provider di simboli di codice nativo, usare le interfacce <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>.

## <a name="see-also"></a>Vedere anche
- [Procedura: Registrare una libreria con il gestore degli oggetti](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Procedura: Esporre gli elenchi dei simboli forniti dalla libreria al gestore degli oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Procedura: Identificare i simboli in una libreria](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
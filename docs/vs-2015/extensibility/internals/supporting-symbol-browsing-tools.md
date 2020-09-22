---
title: Supporto degli strumenti per l'esplorazione di simboli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
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
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b85e8bf500364587af4c3891d7d39f069af9953
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839876"
---
# <a name="supporting-symbol-browsing-tools"></a>Supporto degli strumenti di esplorazione dei simboli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gli strumenti **Visualizzatore oggetti**, **Visualizzazione classi**, **Visualizzatore chiamate** e **Trova simbolo** forniscono funzionalità di esplorazione dei simboli in Visual Studio. Questi strumenti visualizzano visualizzazioni ad albero gerarchico dei simboli e mostrano le relazioni tra i simboli nell'albero. I simboli possono rappresentare gli spazi dei nomi, gli oggetti, le classi, i membri della classe e altri elementi del linguaggio contenuti in diversi componenti. I componenti includono i progetti di Visual Studio, i [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] componenti esterni e le librerie di tipo (tlb). Per ulteriori informazioni, vedere [visualizzazione della struttura del codice](../../ide/viewing-the-structure-of-code.md).  
  
## <a name="symbol-browsing-libraries"></a>Librerie di esplorazione simboli  
 In qualità di implementatore di linguaggi, è possibile estendere le funzionalità di esplorazione dei simboli di Visual Studio creando librerie che tengono traccia dei simboli nei componenti e forniscono gli elenchi di simboli al gestore oggetti di Visual Studio tramite un set di interfacce. Una libreria è descritta dall' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> interfaccia. Il gestore oggetti di Visual Studio risponde alle richieste di nuovi dati dagli strumenti di esplorazione dei simboli ottenendo i dati dalle librerie e organizzando il relativo. Successivamente, compila o aggiorna gli strumenti con i dati richiesti. Per ottenere un riferimento al gestore oggetti di Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> , passare l' <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> ID del servizio al `GetService` metodo.  
  
 Ogni libreria deve eseguire la registrazione con il gestore oggetti di Visual Studio, che raccoglie le informazioni su tutte le librerie. Per registrare una raccolta, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodo. A seconda dello strumento che avvia la richiesta, il gestore oggetti di Visual Studio trova la libreria appropriata e richiede i dati. I dati vengono trasmessi tra le librerie e [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Gestione oggetti negli elenchi di simboli descritti dall' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaccia.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Gestione oggetti è responsabile dell'aggiornamento periodico degli strumenti di esplorazione dei simboli in modo da riflettere i dati più recenti contenuti nelle librerie.  
  
 Il diagramma seguente contiene un esempio di elementi principali del processo di richiesta/scambio di dati tra una libreria e il gestore oggetti di Visual Studio. Le interfacce nel diagramma fanno parte di un'applicazione di codice gestito.  
  
 ![Flusso dei dati tra una libreria e il gestore oggetti](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Per fornire gli elenchi di simboli al gestore oggetti di Visual Studio, è necessario prima registrare la libreria con gestione oggetti di Visual Studio chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodo. Una volta registrata la libreria, il gestore oggetti di Visual Studio richiede alcune informazioni sulle funzionalità della libreria. Ad esempio, richiede i flag della libreria e le categorie supportate chiamando i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> metodi e. A un certo punto, quando uno degli strumenti richiede dati da questa libreria, il gestore di oggetti richiede l'elenco di simboli di primo livello chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> metodo. In risposta, la libreria produce un elenco di simboli e lo espone al gestore oggetti di Visual Studio tramite l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaccia. Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gestore di oggetti determina il numero di elementi presenti nell'elenco chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> metodo. Tutte le richieste seguenti sono correlate a un determinato elemento dell'elenco e forniscono il numero di indice dell'elemento in ogni richiesta. Il gestore oggetti di Visual Studio continua a raccogliere le informazioni sul tipo, l'accessibilità e altre proprietà dell'elemento chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> metodo.  
  
 Determina il nome dell'elemento chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> metodo e richiede le informazioni sull'icona chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> metodo. L'icona viene visualizzata a sinistra del nome dell'elemento e rappresenta il tipo dell'elemento, l'accessibilità e altre proprietà.  
  
 Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gestore di oggetti chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> metodo per determinare se un determinato elemento dell'elenco è espandibile e presenta elementi figlio. Se l'interfaccia utente invia una richiesta per espandere un elemento, il gestore di oggetti richiede l'elenco di simboli figlio chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> metodo. Il processo continua con parti diverse dell'albero compilato su richiesta.  
  
> [!NOTE]
> Per implementare un provider di simboli di codice nativo, usare le <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfacce e.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: registrare una libreria con gestione oggetti](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Procedura: esporre elenchi di simboli forniti dalla libreria al gestore oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Procedura: Identificare i simboli in una libreria](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)

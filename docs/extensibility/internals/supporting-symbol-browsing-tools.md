---
title: Supporto di Symbol-Browsing Tools | Microsoft Docs
description: Visual Studio funzionalità di esplorazione dei simboli in Visual Studio. Informazioni su come estendere queste funzionalità con librerie per i simboli nei componenti.
ms.custom: SEO-VS-2020
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9b8383158773e088b1bfd2e5c955ff224c6800ad
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626051"
---
# <a name="supporting-symbol-browsing-tools"></a>Supporto degli strumenti di esplorazione dei simboli
**Gli strumenti Visualizzatore** **oggetti, Visualizzazione classi**, **Visualizzatore chiamate** **e** Risultati ricerca simbolo offrono funzionalità di esplorazione dei simboli Visual Studio. Questi strumenti visualizzano le visualizzazioni albero gerarchiche dei simboli e mostrano le relazioni tra i simboli nell'albero. I simboli possono rappresentare spazi dei nomi, oggetti, classi, membri di classe e altri elementi del linguaggio contenuti in vari componenti. I componenti includono Visual Studio, componenti .NET Framework esterni e librerie di tipo (con estensione tlb). Per altre informazioni, vedere [Visualizzazione della struttura del codice](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Symbol-Browsing librerie
 In quanto implementatore del linguaggio, è possibile estendere le funzionalità di esplorazione dei simboli di Visual Studio creando librerie che tiene traccia dei simboli nei componenti e forniscono gli elenchi di simboli al gestore oggetti Visual Studio tramite un set di interfacce. Una libreria viene descritta <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> dall'interfaccia . Il Visual Studio di oggetti risponde alle richieste di nuovi dati dagli strumenti di esplorazione dei simboli ottenendo i dati dalle librerie e organizzando i dati. Successivamente popola o aggiorna gli strumenti con i dati richiesti. Per ottenere un riferimento al gestore Visual Studio oggetti <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> , passare <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> l'ID servizio al metodo `GetService` .

 Ogni libreria deve registrarsi con Visual Studio object manager, che raccoglie le informazioni su tutte le librerie. Per registrare una libreria, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodo . A seconda dello strumento che avvia la richiesta, il gestore Visual Studio oggetti trova la libreria appropriata e richiede i dati. I dati si spostano tra le librerie e il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestore oggetti in elenchi di simboli descritti dall'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> .

 Il gestore di oggetti è responsabile dell'aggiornamento periodico degli strumenti di esplorazione dei simboli per riflettere i dati più [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aggiornati contenuti nelle librerie.

 Il diagramma seguente contiene un esempio di elementi chiave del processo di scambio di richieste/dati tra una libreria e Visual Studio object manager. Le interfacce nel diagramma fanno parte di un'applicazione di codice gestito.

 ![Flusso dei dati tra una libreria e il gestore oggetti](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Per fornire gli elenchi di simboli al gestore Visual Studio oggetti, è necessario prima registrare la libreria con il gestore Visual Studio oggetti chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodo . Dopo la registrazione della libreria, Visual Studio gestione oggetti richiede determinate informazioni sulle funzionalità della libreria. Ad esempio, richiede i flag di libreria e le categorie supportate chiamando i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> metodi e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> . A un certo punto, quando uno degli strumenti richiede i dati da questa libreria, il gestore oggetti richiede l'elenco di primo livello dei simboli chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> metodo . In risposta, la libreria produce un elenco di simboli ed espone l'elenco Visual Studio gestione oggetti tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> l'interfaccia . Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestore oggetti determina il numero di elementi presenti nell'elenco chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> . Tutte le richieste seguenti sono correlate a un determinato elemento nell'elenco e forniscono il numero di indice dell'elemento in ogni richiesta. Il Visual Studio di oggetti procede alla raccolta delle informazioni sul tipo, sull'accessibilità e su altre proprietà dell'elemento chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> metodo .

 Determina il nome dell'elemento chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> metodo e richiede le informazioni sull'icona chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> . L'icona viene visualizzata a sinistra del nome dell'elemento e illustra il tipo di elemento, l'accessibilità e altre proprietà.

 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestore oggetti chiama il metodo per determinare se un determinato elemento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> dell'elenco è espandibile e dispone di elementi figlio. Se l'interfaccia utente invia una richiesta per espandere un elemento, il gestore oggetti richiede l'elenco figlio di simboli chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> metodo . Il processo continua con parti diverse dell'albero in fase di compilazione su richiesta.

> [!NOTE]
> Per implementare un provider di simboli di codice nativo, usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> le <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfacce e .

## <a name="see-also"></a>Vedi anche
- [Procedura: Registrare una libreria con il gestore degli oggetti](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Procedura: Esporre gli elenchi dei simboli forniti dalla libreria al gestore degli oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Procedura: Identificare i simboli in una libreria](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)

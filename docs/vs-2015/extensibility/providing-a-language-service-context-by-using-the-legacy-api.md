---
title: Fornire un contesto del servizio di linguaggio tramite l'API legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4471b71b612008ba7d0733c92286415cd3c3f6b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193854"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Specifica del contesto del servizio di linguaggio tramite l'API legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sono disponibili due opzioni per un servizio di linguaggio per fornire il contesto utente mediante l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principale: specificare il contesto del marcatore di testo o fornire tutto il contesto utente. Le differenze tra ciascuna di esse sono descritte qui.  
  
 Per altre informazioni su come fornire il contesto a un servizio di linguaggio connesso al proprio editor, vedere [procedura: fornire il contesto per gli editor](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Specificare il contesto del marcatore di testo per l'editor  
 Per fornire il contesto per gli errori del compilatore indicati dai marcatori di testo nell' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principale, implementare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaccia. In questo scenario, il servizio di linguaggio fornisce il contesto solo quando il cursore si trova su un marcatore di testo. Ciò consente all'editor di fornire la parola chiave sul cursore alla finestra **Guida dinamica** senza attributi.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Specificare tutto il contesto utente per l'editor  
 Se si sta creando un servizio di linguaggio e si usa l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principale, è possibile implementare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaccia per fornire il contesto per il servizio di linguaggio.  
  
 Per l'implementazione di `IVsLanguageContextProvider` , un contenitore di contesti (raccolta) viene associato all'editor, che è responsabile dell'aggiornamento dell'elenco di contesti. Quando la finestra **Guida dinamica** chiama l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> interfaccia in questo contenitore di contesti in fase di inattività, l'elenco di contesti esegue una query nell'editor per un aggiornamento. L'editor notifica quindi al servizio di linguaggio che deve aggiornare l'editor e passa un puntatore all'elenco di contesti. Questa operazione viene eseguita chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> metodo dall'editor al servizio di linguaggio. Utilizzando il puntatore all'elenco di contesti, il servizio di linguaggio ora può aggiungere e rimuovere gli attributi e le parole chiave. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Esistono due modi diversi per implementare `IVsLanguageContextProvider` :  
  
- Specificare una parola chiave per il contenitore del contesto  
  
   Quando l'editor viene chiamato per aggiornare l'elenco dei contesti, passare le parole chiave e gli attributi appropriati e quindi restituire `S_OK` . Questo valore restituito indica all'editor di conservare la parola chiave e il contesto dell'attributo, anziché fornire la parola chiave sul cursore all'elenco di contesti.  
  
- Ottenere la parola chiave dalla parola chiave nel cursore  
  
   Quando l'editor viene chiamato per aggiornare l'elenco dei contesti, passare gli attributi appropriati e quindi restituire `E_FAIL` . Questo valore restituito indica all'editor di conservare gli attributi nell'elenco dei contesti, ma di aggiornare l'elenco di contesti con la parola chiave sul cursore.  
  
  Nel diagramma seguente viene illustrato il modo in cui viene fornito il contesto per un servizio di linguaggio che implementa `IVsLanguageContextProvider` .  
  
  ![Grafica LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  Contesto per un servizio di linguaggio  
  
  Come si può notare nel diagramma, all' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor di testo principale è associato un contenitore del contesto. Questo contenitore di contesto punta a tre contenitori di sottocontesto distinti: servizio di linguaggio, editor predefinito e marcatore di testo. Il servizio di linguaggio e i sacchetti del sottocontesto del marcatore di testo contengono gli attributi e le parole chiave per il servizio di linguaggio se l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaccia è implementata e gli indicatori di testo se l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaccia viene implementata. Se non si implementa alcuna di queste interfacce, l'editor fornisce il contesto per la parola chiave in corrispondenza del cursore nel contenitore del sottocontesto dell'editor predefinito.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Linee guida del contesto per editor e finestre di progettazione  
 Le finestre di progettazione e gli editor devono specificare una parola chiave generale per l'editor o la finestra di progettazione. Questa operazione viene eseguita in modo che un argomento della Guida generico, ma appropriato, venga visualizzato per la finestra di progettazione o l'editor quando un utente preme F1. Un editor deve, oltre a questo, fornire la parola chiave Current al cursore o fornire un termine chiave in base alla selezione corrente. Questa operazione viene eseguita per garantire che un argomento della Guida relativo all'elemento di testo o dell'interfaccia utente a cui punta o selezionato venga visualizzato quando l'utente preme F1. Una finestra di progettazione fornisce il contesto per un elemento selezionato in una finestra di progettazione, ad esempio un pulsante in un form. Gli editor e le finestre di progettazione devono inoltre connettersi a un servizio di linguaggio come descritto in [legacy Language Service Essentials](../extensibility/internals/legacy-language-service-essentials.md).

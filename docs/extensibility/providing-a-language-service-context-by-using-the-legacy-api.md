---
title: Fornire un contesto del servizio linguaggio con l'API Legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66e8da821657dc1aefd8563f3826891cb75e1792
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704631"
---
# <a name="provide-a-language-service-context-by-using-the-legacy-api"></a>Fornire un contesto del servizio linguaggio con l'API legacy
Sono disponibili due opzioni per un servizio di linguaggio fornire contesto utente utilizzando il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale: fornire il contesto di marcatore di testo o forniscono tutto il contesto utente. Di seguito vengono illustrate le differenze tra ogni.

 Per altre informazioni sulla capacità di fornire contesto a un servizio di linguaggio che è connesso a un editor personalizzato, vedere [come: Fornire il contesto per gli editor](../extensibility/how-to-provide-context-for-editors.md).

## <a name="provide-text-marker-context-to-the-editor"></a>Fornire il contesto di marcatore di testo nell'editor
 Per fornire il contesto per gli errori del compilatore indicati da marcatori di testo nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor di base, implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaccia. In questo scenario, il servizio di linguaggio fornisce il contesto solo quando il cursore si trova su un marcatore di testo. In questo modo l'editor fornire la parola chiave in corrispondenza del cursore per la **Guida dinamica** finestra senza attributi.

## <a name="provide-all-user-context-to-the-editor"></a>Forniscono tutto il contesto utente per l'editor
 Se si sta creando un servizio di linguaggio e Usa il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] funzionalità di base dell'editor, quindi è possibile implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaccia per fornire il contesto per il servizio di linguaggio.

 Per l'implementazione di `IVsLanguageContextProvider`, un contenitore di contesto (raccolta) è collegato all'editor, che è responsabile dell'aggiornamento dei contesti. Quando la **Guida dinamica** chiamate finestra il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> interfaccia su questo contenitore di contesto in fase di inattività, il contenitore di contesto esegue una query dell'editor per un aggiornamento. L'editor di notifica quindi al servizio di linguaggio che deve aggiornare l'editor e passa un puntatore al contenitore del contesto. Questa operazione viene eseguita chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> metodo dall'editor per il servizio di linguaggio. Usando il puntatore al contenitore del contesto, il servizio di linguaggio possa ora aggiungere e rimuovere gli attributi e parole chiave. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.

 Esistono due modi diversi per implementare `IVsLanguageContextProvider`:

- Fornire una parola chiave al contenitore del contesto

   Quando l'editor viene chiamato per aggiornare il contenitore di contesto, passare gli attributi e parole chiave appropriate e quindi restituire `S_OK`. Questo valore restituito indica l'editor per mantenere il contesto (parola chiave) e attributi piuttosto che specificare la parola chiave in corrispondenza del cursore al contenitore del contesto.

- Ottenere la parola chiave dalla parola chiave in corrispondenza del cursore

   Quando l'editor viene chiamato per aggiornare il contenitore di contesto, passare gli attributi appropriati e quindi restituire `E_FAIL`. Questo valore restituito indica l'editor per mantenere gli attributi nel contenitore di contesto, ma aggiornare il contenitore di contesto con la parola chiave in corrispondenza del cursore.

  Il diagramma seguente illustra come contesto viene fornito per un servizio di linguaggio che implementa `IVsLanguageContextProvider`.

  ![Immagine di LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2") contesto per un servizio di linguaggio

  Come si può notare nel diagramma, il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor di testo principale dispone di un contenitore di contesto associato a esso. Questo elenco di contesti punta a tre elenchi di sottocontesti separato: servizio di linguaggio editor predefinito e marcatore di testo. I linguaggio del servizio e il testo marcatore elenchi di sottocontesti contengono gli attributi e parole chiave per il servizio di linguaggio, se il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaccia viene implementata e marcatori di testo se il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaccia è implementata. Se non si implementa una di queste interfacce, l'editor fornisce contesto per la parola chiave in corrispondenza del cursore nell'elenco di sottocontesti editor predefinito.

## <a name="context-guidelines-for-editors-and-designers"></a>Linee guida rapida per gli editor e finestre di progettazione
 Editor e finestre di progettazione deve fornire una parola chiave generale per l'editor o finestra di progettazione. Questa operazione viene eseguita in modo che un argomento generico, ma appropriato, verrà visualizzato per l'editor o finestra di progettazione quando l'utente preme **F1**. Un editor deve, inoltre, la parola chiave corrente in corrispondenza del cursore o forniscano un termine chiave in base alla selezione corrente. Questa operazione viene eseguita per garantire che un argomento della Guida per l'elemento dell'interfaccia utente o il testo puntato o selezionato viene visualizzato quando l'utente preme **F1**. Una finestra di progettazione fornisce contesto per un elemento selezionato in una finestra di progettazione, ad esempio un pulsante in un form. Gli editor e finestre di progettazione deve connettersi anche a un servizio di linguaggio come descritto nel [nozioni fondamentali sui servizi di linguaggio Legacy](../extensibility/internals/legacy-language-service-essentials.md).
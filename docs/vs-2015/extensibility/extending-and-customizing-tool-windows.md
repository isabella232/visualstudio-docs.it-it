---
title: Estensione e personalizzazione di Windows lo strumento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b232fa1275bce453e3b32cea6a5ff37fdd501c6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969521"
---
# <a name="extending-and-customizing-tool-windows"></a>Estensione e personalizzazione delle finestre degli strumenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio offre diversi tipi di windows, ad esempio finestre degli strumenti, finestre dei documenti e finestre di dialogo. Altre finestre, ad esempio la finestra Proprietà, la finestra di Output e la finestra Elenco attività, sono tipi di finestre degli strumenti.  
  
## <a name="tool-windows"></a>Finestre degli strumenti  
 Finestre degli strumenti di Visual Studio sono finestre in genere di sola lettura che non sono basati su file. In questo differiscono dalle finestre dei documenti, che visualizzano file in modalità di lettura/scrittura. La **casella degli strumenti**e le finestre **Esplora soluzioni**, **Proprietà** e **Web browser** sono tutte esempi di finestre degli strumenti.  
  
 Per scoprire come creare una semplice finestra degli strumenti, vedere [aggiunta di una finestra degli strumenti](../extensibility/adding-a-tool-window.md).  
  
 Per registrare una finestra degli strumenti con Visual Studio, vedere [la registrazione di una finestra degli strumenti](../extensibility/registering-a-tool-window.md).  
  
 Le finestre degli strumenti sono a istanza singola per impostazione predefinita, ovvero è possibile aprire una sola istanza di una finestra degli strumenti per volta. Una volta aperta, una finestra degli strumenti a istanza singola resta aperta fino a quando non viene chiuso l'IDE. Quando si chiude una finestra degli strumenti a istanza singola, cambia solo la sua visibilità. È anche possibile creare finestre degli strumenti a più istanze, in modo da permettere l'apertura di più istanze della finestra contemporaneamente. Visualizzare [creazione di una finestra degli strumenti a più istanze](../extensibility/creating-a-multi-instance-tool-window.md) per altre informazioni.  
  
 Finestre degli strumenti possono essere *dinamica*, vale a dire che sono visibili ogni volta che si applica il contesto dell'interfaccia utente correlato. L'uso della visibilità automatica può ridurre il disordine delle finestre nell'IDE. Per altre informazioni, vedere [aprendo una finestra degli strumenti dinamica](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Le finestre degli strumenti possono essere ancorate, mobili o a schede nella cornice del documento. La cornice della finestra degli strumenti viene fornita dall'IDE ed è usata per controllare le dimensioni, la posizione, lo stato di ancoraggio e altre proprietà persistenti. Il riquadro della finestra degli strumenti visualizza il contenuto. Le dimensioni e la posizione predefinite vengono applicate solo alla prima apertura della finestra degli strumenti. Successivamente, lo stato della finestra viene salvato in modo permanente.  
  
 I riquadri della finestra degli strumenti possono ospitare controlli utente WPF e supportare le barre degli strumenti. È possibile eseguire l'override della proprietà <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> per restituire l'handle del controllo ospitato.  
  
 È possibile aggiungere più funzionalità diverse alle finestre degli strumenti. Ad esempio, è possibile aggiungere una barra degli strumenti: [Aggiunta di una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md) o un menu di scelta rapida: [Aggiunta di un Menu di scelta rapida in una finestra degli strumenti](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). È possibile aggiungere un controllo di ricerca che consente di cercare gli elementi all'interno la finestra degli strumenti: [Aggiunta di ricerca a una finestra degli strumenti](../extensibility/adding-search-to-a-tool-window.md).  
  
 È possibile sottoscrivere gli eventi di finestra degli strumenti: [Sottoscrizione a un evento](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Estensione Windows strumento esistente  
 È possibile aggiungere informazioni sulla finestra degli strumenti a una nuova **opzioni** pagina e una nuova impostazione sul **delle proprietà** pagina, scrivere il **elenco attività** e **Output**  windows. Per altre informazioni, vedere [estendendo le proprietà, elenco attività, Output e opzioni di Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) e [estendendo le proprietà, elenco attività, Output e opzioni Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Finestre di dialogo modali  
 In un'estensione di Visual Studio è necessario creare finestre di dialogo modali per derivazione da <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, che consente di controllare queste e il resto dell'interfaccia utente. Per altre informazioni, vedere . [Creazione e gestione delle finestre di dialogo modali](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md)

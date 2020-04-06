---
title: Estensione e personalizzazione delle finestre degli strumenti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76c094ec73a69baa46a5e8313dd26febd57e5887
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711813"
---
# <a name="extend-and-customize-tool-windows"></a>Estendere e personalizzare le finestre degli strumenti
Visual Studio fornisce diversi tipi di finestre, ad esempio finestre degli strumenti, finestre di documento e finestre di dialogo. Altre finestre, ad esempio la finestra **Proprietà,** la finestra **Output** e la finestra **Elenco attività,** sono tipi di finestre degli strumenti.

## <a name="tool-windows"></a>Finestre degli strumenti
 Finestre degli strumenti di Visual Studio sono in genere finestre di sola lettura che non sono basate su file. In questo differiscono dalle finestre dei documenti, che visualizzano file in modalità di lettura/scrittura. La **casella degli strumenti**e le finestre **Esplora soluzioni**, **Proprietà** e **Web browser** sono tutte esempi di finestre degli strumenti.

 Per informazioni su come creare una semplice finestra degli strumenti, vedere [Aggiungere una finestra degli strumenti](../extensibility/adding-a-tool-window.md).

 Per registrare una finestra degli strumenti con Visual Studio, vedere [Registrare una finestra degli strumenti](../extensibility/registering-a-tool-window.md).

 Le finestre degli strumenti sono a istanza singola per impostazione predefinita, ovvero è possibile aprire una sola istanza di una finestra degli strumenti per volta. Una volta aperta, una finestra degli strumenti a istanza singola resta aperta fino a quando non viene chiuso l'IDE. Quando si chiude una finestra degli strumenti a istanza singola, cambia solo la visibilità. È anche possibile creare finestre degli strumenti a più istanze, in modo da permettere l'apertura di più istanze della finestra contemporaneamente. Per ulteriori informazioni, vedere Creazione di una finestra degli strumenti a [più istanze.](../extensibility/creating-a-multi-instance-tool-window.md)

 Le finestre degli strumenti possono essere *dinamiche,* ovvero sono visibili ogni volta che si applica il contesto dell'interfaccia utente correlato. L'uso della visibilità automatica può ridurre il disordine delle finestre nell'IDE. Per ulteriori informazioni, consultate Aprire una finestra degli strumenti [dinamica.](../extensibility/opening-a-dynamic-tool-window.md)

 Le finestre degli strumenti possono essere ancorate, mobili o a schede nella cornice del documento. La cornice della finestra degli strumenti viene fornita dall'IDE ed è usata per controllare le dimensioni, la posizione, lo stato di ancoraggio e altre proprietà persistenti. Il riquadro della finestra degli strumenti visualizza il contenuto. Le dimensioni e la posizione predefinite vengono applicate solo alla prima apertura della finestra degli strumenti. Successivamente, lo stato della finestra viene salvato in modo permanente.

 I riquadri della finestra degli strumenti possono ospitare controlli utente WPF e supportare le barre degli strumenti. È possibile eseguire l'override della proprietà <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> per restituire l'handle del controllo ospitato.

 È possibile aggiungere molte funzionalità diverse alle finestre degli strumenti. Ad esempio, è possibile aggiungere una barra degli strumenti: [Aggiungere una barra degli strumenti a una finestra degli](../extensibility/adding-a-toolbar-to-a-tool-window.md) strumenti o a un menu di scelta rapida: Aggiungere un menu di scelta rapida in una finestra degli [strumenti](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). È possibile aggiungere un controllo di ricerca che consente di cercare gli elementi all'interno della finestra degli strumenti: [Aggiungi ricerca a una finestra degli strumenti](../extensibility/adding-search-to-a-tool-window.md).

 È possibile sottoscrivere gli eventi della finestra degli strumenti: [Sottoscrivere un evento](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Estendere le finestre degli strumenti esistenti
 È possibile aggiungere informazioni sulla finestra degli strumenti a una nuova pagina **Opzioni** e una nuova impostazione nella pagina **Proprietà,** scrivere nelle finestre **Elenco attività** e **Output.** Per ulteriori informazioni, consultate [Estendere le finestre Proprietà, Elenco attività, Output e Opzioni.](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)

## <a name="modal-dialog-boxes"></a>Finestre di dialogo modali
 In un'estensione di Visual Studio è necessario <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>creare finestre di dialogo modali derivandole da , che consente di controllare loro e il resto dell'interfaccia utente. Per ulteriori informazioni, consultate Creare e gestire finestre di [dialogo modali.](../extensibility/creating-and-managing-modal-dialog-boxes.md)

## <a name="see-also"></a>Vedere anche
- [Creare un'estensione con una finestra degli strumentiCreate an extension with a tool window](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Estendere i progetti](../extensibility/extending-projects.md)
- [Estendere le soluzioni](../extensibility/extending-solutions.md)

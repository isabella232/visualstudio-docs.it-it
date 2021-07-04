---
title: Informazioni sulla finestra Esplora soluzioni strumenti
description: Informazioni su come usare la finestra Esplora soluzioni strumenti di Visual Studio per creare & gestire file, progetti e soluzioni.
ms.date: 06/29/2021
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
helpviewer_keywords:
- solution explorer [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fbbae8b974a7e88abffd9a12eb253dfea6c7165b
ms.sourcegitcommit: 8fb1500acb7e6314fbb6b78eada78ef5d61d39bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2021
ms.locfileid: "113280489"
---
# <a name="how-to-use-solution-explorer"></a>Come usare le Esplora soluzioni

È possibile usare la finestra Esplora soluzioni strumenti per creare & le soluzioni e i progetti e per visualizzare & interagire con il codice. Questo articolo illustra in dettaglio le opzioni dell'interfaccia utente che consentono di eseguire questa operazione.

> [!NOTE]
> Questo argomento si applica solo a Visual Studio in Windows.

## <a name="solution-explorer-tool-window"></a>Esplora soluzioni degli strumenti

Per iniziare, si esaminerà la finestra degli strumenti Esplora soluzioni [nell'IDE di Visual Studio](../get-started/visual-studio-ide.md), con una soluzione console C# aperta con due progetti.

[![Finestra Esplora soluzioni strumenti in Visual Studio.](media/solution-explorer-tool-window.png)](media/solution-explorer-tool-window.png#lightbox)

La finestra degli strumenti contiene gli elementi dell'interfaccia utente seguenti:

- **Barra dei menu**, in cui è possibile controllare la modalità di visualizzazione dei file
- **Barra di ricerca**, in cui è possibile cercare file e tipi di file specifici
- **Finestra principale**, in cui è possibile visualizzare e gestire file, progetti & soluzioni
- **Nodo della** soluzione, in cui è possibile gestire le soluzioni
- **Project nodo**, in cui è possibile gestire i progetti
- **Nodo Dipendenze**, in cui è possibile gestire la soluzione & dipendenze del progetto
- **Nodo programma**, in cui è possibile visualizzare, modificare e gestire il programma o l'applicazione (app)
- **[Scheda modifiche Git,](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window)** in cui è possibile usare Git & GitHub all'interno Visual Studio collaborare ai progetti con il team

> [!TIP]
> Se la finestra degli strumenti Esplora soluzioni non è visualizzata, è possibile aprirla dalla barra dei menu di Visual Studio usando Visualizza Esplora soluzioni o premendo  >   **CTRL** + **ALT** + **L.**

## <a name="solution-explorer-menu-bar"></a>Esplora soluzioni barra dei menu

Per continuare, si esamini la barra dei menu Esplora soluzioni più in dettaglio.

![Barra Esplora soluzioni dei menu Visual Studio.](media/solution-explorer-menu-bar.png)

La barra dei menu contiene gli elementi dell'interfaccia utente seguenti, da sinistra a destra:

- **Pulsante** Indietro, per alternare i risultati della ricerca
- **Pulsante** Avanti, per alternare i risultati della ricerca
- **Pulsante** Home, per tornare alla visualizzazione predefinita
- **Pulsante** Cambia per passare da una soluzione all'altra e da una visualizzazione disponibile all'altra
- **Pulsante Filtro modifiche** in sospeso & menu a discesa per visualizzare i file aperti o i file con modifiche in sospeso
- **Pulsante Sincronizza con documento** attivo per individuare un file dall'editor di codice
- **Pulsante** Aggiorna, che viene visualizzato solo quando si seleziona una dipendenza, ad esempio una funzione o un pacchetto
- **Pulsante Comprimi** tutto per comprimere la visualizzazione file nella finestra principale
- **Pulsante Mostra tutti i** file per visualizzare tutti i file, inclusi [i progetti scaricati](filtered-solutions.md#toggle-unloaded-project-visibility)
- **Pulsante** Proprietà per visualizzare e modificare le impostazioni per file e componenti specifici
- **Pulsante Anteprima elementi** selezionati per visualizzare un file o un componente selezionato nell'editor di codice

### <a name="solution-explorer-right-click-context-menu"></a>Esplora soluzioni menu di scelta rapida

In Esplora soluzioni sono disponibili diverse proprietà di file con cui è possibile interagire usando il menu di scelta rapida. Per altre informazioni sulle opzioni del menu di scelta rapida, vedere la [pagina Gestisci proprietà di progetti e](managing-project-and-solution-properties.md) soluzioni.

## <a name="see-also"></a>Vedere anche

- [Che cosa sono le soluzioni e i progetti Visual Studio?](solutions-and-projects-in-visual-studio.md)
- [Personalizzare il layout delle finestre in Visual Studio](customizing-window-layouts-in-visual-studio.md)

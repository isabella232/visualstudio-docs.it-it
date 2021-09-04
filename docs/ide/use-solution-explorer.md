---
title: Informazioni sulla finestra Esplora soluzioni strumenti
description: Informazioni su come usare la finestra Esplora soluzioni strumenti in Visual Studio per creare & file, progetti e soluzioni.
ms.date: 09/02/2021
ms.topic: conceptual
ms.custom: contperf-fy22q1
f1_keywords:
- vs.addnewitem
helpviewer_keywords:
- solution explorer [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6fa982d290abcc852c93369003abeed0e6363291
ms.sourcegitcommit: f71a0db01bd4f24521cee5da926b9db3571ddecd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2021
ms.locfileid: "123459135"
---
# <a name="how-to-use-solution-explorer"></a>Come usare Esplora soluzioni

È possibile usare la finestra Esplora soluzioni strumenti per creare & le soluzioni e i progetti e per visualizzare & interagire con il codice. Questo articolo descrive in dettaglio le opzioni dell'interfaccia utente che consentono di eseguire questa operazione.

> [!NOTE]
> Questo argomento si applica solo a Visual Studio in Windows.

## <a name="solution-explorer-tool-window"></a>Esplora soluzioni degli strumenti

Per iniziare, si esaminerà la finestra degli strumenti Esplora soluzioni [nell'IDE di Visual Studio](../get-started/visual-studio-ide.md), con una soluzione console C# aperta con due progetti.

[![Screenshot con annotazioni della finestra Esplora soluzioni strumenti in Visual Studio.](media/solution-explorer-tool-window.png)](media/solution-explorer-tool-window.png#lightbox)

La finestra degli strumenti contiene gli elementi dell'interfaccia utente seguenti:

- **Barra dei menu**, in cui è possibile controllare l'visualizzazione dei file
- **Barra di ricerca**, in cui è possibile cercare file e tipi di file specifici
- **Finestra principale**, in cui è possibile visualizzare e gestire file, progetti, & soluzioni
- **Nodo della** soluzione, in cui è possibile gestire le soluzioni
- **Project nodo**, in cui è possibile gestire i progetti
- **Nodo Dipendenze**, in cui è possibile gestire la soluzione & dipendenze del progetto
- **Nodo programma**, in cui è possibile visualizzare, modificare e gestire il programma o l'applicazione (app)
- **[Scheda Modifiche git](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window)**, in cui è possibile usare Git & GitHub all'interno Visual Studio per collaborare ai progetti con il team

> [!TIP]
> Se la finestra degli strumenti Esplora soluzioni non è visualizzata, è possibile aprirla dalla barra dei menu di Visual Studio usando Visualizza Esplora soluzioni oppure premendo  >   **CTRL** + **ALT** + **L**.

## <a name="solution-explorer-menu-bar"></a>Esplora soluzioni barra dei menu

Per continuare, diamo un'occhiata più da vicino alla barra Esplora soluzioni menu.

![Screenshot con annotazioni della barra Esplora soluzioni menu in Visual Studio.](media/solution-explorer-menu-bar.png)

La barra dei menu contiene gli elementi dell'interfaccia utente seguenti, da sinistra a destra:

- **Pulsante** Indietro per alternare i risultati della ricerca
- **Pulsante** Avanti, per alternare i risultati della ricerca
- **Pulsante** Home per tornare alla visualizzazione predefinita
- **Pulsante** Cambia per passare da una soluzione all'altra e da una visualizzazione disponibile all'altra
- **Pulsante Filtro modifiche** in sospeso & menu a discesa, per visualizzare file aperti o file con modifiche in sospeso
- **Pulsante Sincronizza con documento** attivo per individuare un file dall'editor di codice
- **Pulsante** Aggiorna, che viene visualizzato solo quando si seleziona una dipendenza, ad esempio una funzione o un pacchetto
- **Pulsante Comprimi** tutto per comprimere la visualizzazione file nella finestra principale
- **Pulsante Mostra tutti i** file per visualizzare tutti i file, inclusi [i progetti scaricati](filtered-solutions.md#toggle-unloaded-project-visibility)
- **Pulsante** Proprietà per visualizzare e modificare le impostazioni per file e componenti specifici
- **Pulsante Anteprima elementi** selezionati per visualizzare un file o un componente selezionato nell'editor di codice

## <a name="solution-explorer-context-menu"></a>Esplora soluzioni menu di scelta rapida

In Esplora soluzioni sono disponibili diverse opzioni con cui è possibile interagire usando il menu di scelta rapida. Lo screenshot seguente per un'app C# mostra le opzioni del menu di scelta rapida visualizzate quando si fa clic con il pulsante destro del mouse sul **nodo Soluzione.**

:::image type="content" source="media/solution-explorer-context-menu.png" alt-text="Screenshot del menu di scelta rapida in Esplora soluzioni.":::

Ciò che viene visualizzato nel menu di scelta rapida dal nodo **Soluzione** dipende anche dal tipo di progetto, dal linguaggio di programmazione o dalla piattaforma. Lo screenshot seguente evidenzia le opzioni aggiuntive seguenti per un'app C#: **Project Dependencies**, **Project Build Order**, Set Startup **Projects** e un menu a comparsa **Git.** Queste opzioni aggiuntive vengono in genere visualizzate quando si aggiunge un altro progetto a una soluzione e quindi lo si aggiunge a un repo.

:::image type="content" source="media/solution-explorer-context-menu-extra-items.png" alt-text="Screenshot del menu di scelta rapida in Esplora soluzioni con opzioni aggiuntive.":::

## <a name="the-add-menu"></a>Menu Aggiungi

Nel menu Esplora soluzioni di scelta rapida, una delle opzioni più utili è **il** menu a comparsa Aggiungi. Da questa soluzione è possibile [aggiungere un altro](../get-started/csharp/tutorial-console-part-2.md#add-another-project) progetto a una soluzione. È anche possibile [aggiungere un elemento](reference/add-new-item-command.md) a un progetto e altro ancora.

:::image type="content" source="media/solution-explorer-context-menu-add-flyout.png" alt-text="Screenshot del menu a comparsa Aggiungi dal menu di scelta rapida con il pulsante destro del mouse in Esplora soluzioni.":::

È possibile visualizzare **il** menu a comparsa Aggiungi  dal nodo **Soluzione,** dal nodo Project o dal **nodo** Dipendenze. Le opzioni variano a seconda del nodo in uso.

Per un'esercitazione che illustra come aggiungere elementi e progetti usando il menu di scelta rapida in Esplora soluzioni, vedere la pagina Introduzione a progetti [e](../get-started/tutorial-projects-solutions.md#add-an-item-to-the-project) soluzioni.

## <a name="see-also"></a>Vedi anche

- [Che cosa sono le soluzioni e i progetti Visual Studio?](solutions-and-projects-in-visual-studio.md)
- [Personalizzare il layout delle finestre in Visual Studio](customizing-window-layouts-in-visual-studio.md)

---
description: Usare questa finestra per visualizzare e modificare in fase di progettazione le proprietà e gli eventi degli oggetti selezionati presenti in editor e finestre di progettazione.
title: Finestra Proprietà
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ce71f30b6008de006ad2ab96c0388dc3e1ee507247d9c9a500304c94d5197846
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447428"
---
# <a name="properties-window"></a>Finestra Proprietà

Usare questa finestra per visualizzare e modificare in fase di progettazione le proprietà e gli eventi degli oggetti selezionati presenti in editor e finestre di progettazione. È anche possibile usare la finestra **Proprietà** per modificare e visualizzare le proprietà di file, progetto e soluzione. La finestra **Proprietà** può essere selezionata dal menu **Visualizza**. È anche possibile aprirla premendo **F4** o digitando **Proprietà** nella casella di ricerca.

La finestra **Proprietà** visualizza diversi tipi di campi di modifica, a seconda dei requisiti di una determinata proprietà. I campi di modifica comprendono caselle di modifica, elenchi a discesa e collegamenti a finestre di dialogo dell'editor personalizzato. Le proprietà visualizzate in grigio sono di sola lettura.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

Nome oggetto\
Elenca l'oggetto o gli oggetti attualmente selezionati. Saranno visibili solo gli oggetti dell'editor attivo o della finestra di progettazione attiva. Quando si selezionano più oggetti vengono visualizzate solo le proprietà comuni a tutti gli oggetti selezionati.

Per categoria\
Elenca, per categoria, tutte le proprietà e i relativi valori per l'oggetto selezionato. È possibile comprimere una categoria per ridurre il numero di proprietà visualizzate. Quando una categoria viene espansa o compressa, accanto al nome verrà visualizzato un segno più (+) o un segno meno (-). Le categorie sono elencate in ordine alfabetico.

Alfabetico\
Ordina alfabeticamente tutti gli eventi e le proprietà in fase di progettazione per gli oggetti selezionati. Per modificare una proprietà attiva, fare clic nella cella a destra della proprietà e immettere le modifiche.

Pagine delle proprietà\
Visualizza la finestra di dialogo **Pagine delle proprietà** o **Creazione progetti** per l'elemento selezionato. In Pagine delle proprietà viene visualizzato un subset, lo stesso o un superset delle proprietà disponibili nella finestra **Proprietà**. Usare questo pulsante per visualizzare e modificare le proprietà correlate alla configurazione attiva del progetto.

Proprietà\
Visualizza le proprietà di un oggetto. Molti oggetti contengono anche eventi che possono essere visualizzati usando la finestra **Proprietà**.

Ordina per origine proprietà\
Raggruppa le proprietà per origine, ad esempio ereditarietà, stili applicati e binding. È disponibile solo quando si modificano i file XAML nella finestra di progettazione.

Eventi\
Visualizza gli eventi per un oggetto.

> [!NOTE]
> Questo controllo della barra degli strumenti della finestra **Proprietà** è disponibile solo quando si attiva un modulo o una finestra di progettazione controlli nel contesto di un progetto [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Quando si modificano i file XAML, gli eventi vengono visualizzati in una scheda separata della finestra Proprietà.

Messaggi\
Elenca tutti i messaggi di Windows. Consente di aggiungere o eliminare funzioni specifiche del gestore per i messaggi visualizzati per la classe selezionata.

> [!NOTE]
> Questo controllo della barra degli strumenti della finestra **Proprietà** è disponibile solo quando **Visualizzazione classi** è la finestra attiva nel contesto di un progetto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

Override\
Indica tutte le funzioni virtuali per la classe selezionata e consente di aggiungere o eliminare funzioni per l'override.

> [!NOTE]
> Questo controllo della barra degli strumenti della finestra **Proprietà** è disponibile solo quando **Visualizzazione classi** è la finestra attiva nel contesto di un progetto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

Riquadro descrizione\
Visualizza il tipo di proprietà e una breve descrizione della proprietà. È possibile attivare e disattivare la descrizione della proprietà usando il comando Descrizione del menu di scelta rapida.

> [!NOTE]
> Questo controllo della barra degli strumenti della finestra **Proprietà** non è disponibile se si modificano i file XAML nella finestra di progettazione.

Visualizzazione anteprima\
Visualizza una rappresentazione visiva dell'elemento attualmente selezionato quando si modificano i file XAML nella finestra di progettazione.

Ricerca\
Specifica una funzione di ricerca per le proprietà e gli eventi quando si modificano i file XAML nella finestra di progettazione. La casella di ricerca risponde alle ricerche di parole parziali e aggiorna i risultati della ricerca durante la digitazione.

## <a name="see-also"></a>Vedi anche

- [Project Properties Reference](../../ide/reference/project-properties-reference.md) (Riferimenti alle proprietà di progetto)
- [Personalizzazione del layout della finestra](../../ide/customizing-window-layouts-in-visual-studio.md)

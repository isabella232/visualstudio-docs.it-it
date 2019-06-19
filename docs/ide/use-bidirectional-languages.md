---
title: Supporto per l'arabo e l'ebraico
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1271e5160920dc79decc9acc98aa1e5e3d936ca5
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/10/2019
ms.locfileid: "66824166"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Supporto per le lingue bidirezionali in Visual Studio

Visual Studio può visualizzare correttamente il testo in arabo ed ebraico e consente di immettere testo bidirezionale per i valori e i nomi degli oggetti.

> [!NOTE]
> Per l'immissione e la visualizzazione delle lingue bidirezionali è necessario usare una versione di Windows configurata per la lingua appropriata. Può essere una versione di Windows in inglese con il Language Pack appropriato o una versione di Windows localizzata nella lingua desiderata.

## <a name="fully-supported-features"></a>Funzionalità con supporto completo

In fase di progettazione in Visual Studio, è possibile usare le lingue bidirezionali durante l'immissione di testo e l'assegnazione di nomi agli oggetti e quando si salvano e aprono i file.

### <a name="text-entry"></a>Voce di testo

Visual Studio supporta Unicode, pertanto, se il sistema è configurato con le impostazioni locali e la lingua di input appropriate, è possibile immettere testo in arabo o ebraico. (Il supporto per l'arabo include le linee kashida e i segni diacritici.)

### <a name="arabic-or-hebrew-object-names"></a>Nomi di oggetto in arabo o ebraico

È possibile usare le lingue bidirezionali per assegnare nomi a soluzioni, progetti, file, cartelle e così via. Nel codice è possibile usare le lingue bidirezionali per i nomi di variabili, classi, oggetti, attributi, metadati e altri elementi. Quando si usa l'arabo è possibile usare qualsiasi carattere incluse le linee kashida e i segni diacritici.

Gli elementi seguenti possono avere nomi in arabo o ebraico e vengono gestiti correttamente in Visual Studio:

- Nomi di soluzioni, progetti e file, incluse le eventuali cartelle incluse nel percorso del progetto.

   **Esplora soluzioni** visualizza correttamente i nomi di elementi e soluzioni.

- Contenuto di file.

   È possibile aprire o salvare file con codifica Unicode o con una tabella codici selezionata.

- Elementi di dati.

   In **Esplora server** questi elementi vengono visualizzati correttamente e possono essere modificati.

- Elementi copiati negli Appunti di Windows.

- Attributi e metadati.

- Valori delle proprietà.

   Nella finestra **Proprietà** è possibile usare testo in arabo o ebraico. La finestra consente di passare dall'ordine di lettura da destra a sinistra a quello da sinistra a destra e viceversa usando combinazioni di tasti standard di Windows (**CTRL**+**MAIUSC destro** per l'ordine di lettura da destra a sinistra e **CTRL**+**MAIUSC sinistro** per quello da sinistra a destra).

- Codice e testo letterale.

   Nell'editor di codice è possibile usare l'arabo o l'ebraico per assegnare nomi a classi, funzioni, variabili, proprietà, valori letterali stringa, attributi e così via. Tuttavia l'editor non supporta l'ordine di lettura da destra a sinistra: il testo inizia sempre sul margine sinistro.

   > [!TIP]
   > È consigliabile inserire i valori letterali stringa nei file di risorse anziché impostarli come hardcoded nei programmi. Per altre informazioni, vedere [Risorse nelle applicazioni desktop (.NET Framework)](/dotnet/framework/resources/index).

   > [!NOTE]
   > È necessario mantenere la coerenza nei riferimenti a oggetti denominati in arabo ed ebraico. Se ad esempio si usano le linee kashida nel nome di una variabile in arabo, è necessario usare sempre la notazione kashida quando si fa riferimento alla variabile. In caso contrario, si verificheranno errori.

- Commenti del codice. È possibile creare commenti in arabo o in ebraico. È possibile usare queste lingue anche nello strumento per la generazione di commenti.

### <a name="file-encoding"></a>Codifica dei file

È possibile salvare e aprire file con codifica Unicode o specifica della lingua. Per altre informazioni, vedere [Procedura: Salvare e aprire file con codifica](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="right-to-left-reading-order"></a>Ordine di lettura da destra a sinistra

Visual Studio offre supporto limitato per l'ordine di lettura da destra a sinistra. Per impostazione predefinita i controlli per l'immissione di testo in Visual Studio adottano l'ordine di lettura da sinistra a destra. Nella maggior parte dei casi è possibile cambiare l'ordine di lettura con operazioni standard di Windows. È ad esempio possibile premere **CTRL**+**MAIUSC destro** per impostare il supporto dell'ordine di lettura da destra a sinistra per i valori delle proprietà nella finestra **Proprietà**.

L'ordine di lettura da destra a sinistra non è supportato nelle posizioni seguenti in Visual Studio:

- Le caselle di controllo, gli elenchi a discesa e gli altri controlli delle finestre di dialogo di Visual Studio usano sempre l'ordine di lettura da sinistra a destra.

- L'editor di codice (e l'editor di testo) non supportano l'ordine di lettura da destra a sinistra. È possibile immettere il testo in una lingua bidirezionale, ma l'ordine di lettura è sempre da sinistra a destra.

## <a name="see-also"></a>Vedere anche

- [Sviluppare app globalizzate e localizzate](globalizing-and-localizing-applications.md)

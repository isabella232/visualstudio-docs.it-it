---
title: Supporto per l'arabo e l'ebraico
description: Informazioni su come visualizzare il testo in arabo ed ebraico e immettere testo bidirezionale per i nomi e i valori degli oggetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ca94c650c88cb477e99812d87e2ff42146916bcf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116825"
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

- Valori delle proprietà

   È possibile usare testo arabo o ebraico nella **finestra** Proprietà. La finestra consente di passare dall'ordine di lettura da destra a sinistra a quello da sinistra a destra usando le sequenze di tasti Windows standard **(CTRL** MAIUSC da destra a sinistra e CTRL MAIUSC sinistro per l'ordine da sinistra a +   +  destra).

- Codice e testo letterale.

   Nell'editor di codice è possibile usare l'arabo o l'ebraico per assegnare nomi a classi, funzioni, variabili, proprietà, valori letterali stringa, attributi e così via. Tuttavia l'editor non supporta l'ordine di lettura da destra a sinistra: il testo inizia sempre sul margine sinistro.

   > [!TIP]
   > È consigliabile inserire i valori letterali stringa nei file di risorse anziché impostarli come hardcoded nei programmi. Per altre informazioni, vedere [Risorse nelle applicazioni desktop (.NET Framework)](/dotnet/framework/resources/index).

   > [!NOTE]
   > È necessario mantenere la coerenza nei riferimenti a oggetti denominati in arabo ed ebraico. Se ad esempio si usano le linee kashida nel nome di una variabile in arabo, è necessario usare sempre la notazione kashida quando si fa riferimento alla variabile. In caso contrario, si verificheranno errori.

- Commenti del codice. È possibile creare commenti in arabo o in ebraico. È possibile usare queste lingue anche nello strumento per la generazione di commenti.

### <a name="file-encoding"></a>Codifica file

È possibile salvare e aprire file con codifica Unicode o specifica della lingua. Per altre informazioni, vedere [Procedura: Salvare e aprire file con codifica](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="right-to-left-reading-order"></a>Ordine di lettura da destra a sinistra

Visual Studio offre supporto limitato per l'ordine di lettura da destra a sinistra. Per impostazione predefinita i controlli per l'immissione di testo in Visual Studio adottano l'ordine di lettura da sinistra a destra. Nella maggior parte dei casi è possibile cambiare l'ordine di lettura con operazioni standard di Windows. Ad esempio, è possibile premere **CTRL** MAIUSC DESTRO per cambiare la finestra Proprietà per supportare l'ordine di lettura da destra a sinistra per +  i valori delle proprietà. 

L'ordine di lettura da destra a sinistra non è supportato nelle posizioni seguenti in Visual Studio:

- Le caselle di controllo, gli elenchi a discesa e gli altri controlli delle finestre di dialogo di Visual Studio usano sempre l'ordine di lettura da sinistra a destra.

- L'editor di codice (e l'editor di testo) non supportano l'ordine di lettura da destra a sinistra. È possibile immettere il testo in una lingua bidirezionale, ma l'ordine di lettura è sempre da sinistra a destra.

## <a name="see-also"></a>Vedi anche

- [Sviluppare app globalizzate e localizzate](globalizing-and-localizing-applications.md)

---
title: Supporto per app in arabo ed ebraico
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4aa75ee12e09d4aa56a112a135a2e9e913b5cd39
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335233"
---
# <a name="create-applications-in-bi-directional-languages"></a>Creare applicazioni in lingue bidirezionali

È possibile usare Visual Studio per creare applicazioni che visualizzano correttamente il testo nelle lingue scritte da destra a sinistra, tra cui l'arabo e l'ebraico. Per alcune funzionalità basta impostare delle proprietà. In altri casi è necessario implementare le funzionalità nel codice.

> [!NOTE]
> Per l'immissione e la visualizzazione delle lingue bidirezionali è necessario usare una versione di Windows configurata per la lingua appropriata. Può essere una versione di Windows in inglese con il Language Pack appropriato o una versione di Windows localizzata nella lingua desiderata.

## <a name="types-of-applications-that-support-bi-directional-languages"></a>Tipi di applicazioni che supportano le lingue bidirezionali

-  App di Windows

   È possibile creare applicazioni completamente bidirezionali che includono il supporto per il testo bidirezionale, l'ordine di lettura da destra a sinistra e il mirroring (inversione del layout di finestre, menu, finestre di dialogo e così via). Fatta eccezione per il mirroring, queste funzionalità sono disponibili per impostazione predefinita o come impostazioni di proprietà. Il mirroring è supportato intrinsecamente per alcune funzionalità, ad esempio le finestre di messaggio. In altri casi è invece necessario implementare il mirroring nel codice. Per altre informazioni, vedere [Supporto bidirezionale per le applicazioni Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

-  App Web

   I servizi Web supportano l'invio e la ricezione di testo UTF-8 e Unicode, quindi sono adatti per le applicazioni che prevedono l'uso delle lingue bidirezionali. L'interfaccia utente delle applicazioni Web client è basata sui browser, pertanto il livello di supporto bidirezionale di un'applicazione Web dipende dal grado di supporto delle funzionalità bidirezionali nel browser dell'utente. In Visual Studio è possibile creare applicazioni con supporto per testo in arabo o ebraico, ordine di lettura da destra a sinistra, codifica di file e impostazioni cultura locali. Per altre informazioni, vedere [Supporto bidirezionale per applicazioni Web ASP.NET](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

Le app console non includono il supporto del testo per le lingue bidirezionali. Questo fatto dipende dall'interazione tra Windows e le applicazioni console.

## <a name="fully-supported-features"></a>Funzionalità con supporto completo

In fase di progettazione con Visual Studio è possibile usare le lingue bidirezionali nei modi seguenti:

- **Immissione di testo**

   Visual Studio supporta Unicode, pertanto, se il sistema è configurato con le impostazioni locali e la lingua di input appropriate, è possibile immettere testo in arabo o ebraico. (Il supporto per l'arabo include le linee kashida e i segni diacritici.)

- **Nomi di oggetto**

   È possibile usare le lingue bidirezionali per assegnare nomi a soluzioni, progetti, file, cartelle e così via. Nel codice è possibile usare le lingue bidirezionali per i nomi di variabili, classi, oggetti, attributi, metadati e altri elementi.

- **Codifica file**

   È possibile salvare e aprire file con codifica Unicode o specifica della lingua. Per altre informazioni, vedere [Procedura: Salvare e aprire file con codifica](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="features-with-limited-support"></a>Funzionalità con supporto limitato

### <a name="right-to-left-reading-order"></a>Ordine di lettura da destra a sinistra

Per impostazione predefinita i controlli per l'immissione di testo in Visual Studio adottano l'ordine di lettura da sinistra a destra. Nella maggior parte dei casi è possibile cambiare l'ordine di lettura con operazioni standard di Windows. È ad esempio possibile premere **CTRL**+**MAIUSC destro** per impostare il supporto dell'ordine di lettura da destra a sinistra per i valori delle proprietà nella finestra **Proprietà**. Tuttavia, l'ordine di lettura da destra a sinistra non è supportato ovunque in Visual Studio:

- Le caselle di controllo, gli elenchi a discesa e gli altri controlli delle finestre di dialogo di Visual Studio usano sempre l'ordine di lettura da sinistra a destra.

- L'editor di codice (e l'editor di testo) non supportano l'ordine di lettura da destra a sinistra. È possibile immettere il testo in una lingua bidirezionale, ma l'ordine di lettura è sempre da sinistra a destra.

## <a name="arabic-or-hebrew-object-names"></a>Nomi di oggetto in arabo o ebraico

È possibile usare testo in arabo o ebraico per assegnare nomi a cartelle, variabili o altri oggetti. Quando si usa l'arabo è possibile usare qualsiasi carattere incluse le linee kashida e i segni diacritici.

Gli elementi seguenti possono essere denominati in arabo o ebraico e vengono gestiti correttamente in Visual Studio:

- Nomi di soluzioni, progetti e file, incluse le eventuali cartelle incluse nel percorso del progetto. **Esplora soluzioni** visualizza correttamente i nomi di elementi e soluzioni.

- Contenuto di file. È possibile aprire o salvare file con codifica Unicode o con una tabella codici selezionata.

    > [!NOTE]
    > L'editor di codice non supporta l'ordine di lettura da destra a sinistra.

- Elementi di dati. In **Esplora server** questi elementi vengono visualizzati correttamente e possono essere modificati.

- Elementi copiati negli Appunti di Windows.

- Attributi e metadati.

- Valori delle proprietà. Nella finestra **Proprietà** è possibile usare testo in arabo o ebraico. La finestra consente di passare dall'ordine di lettura da destra a sinistra a quello da sinistra a destra e viceversa usando combinazioni di tasti standard di Windows (**CTRL**+**MAIUSC destro** per l'ordine di lettura da destra a sinistra e **CTRL**+**MAIUSC sinistro** per quello da sinistra a destra).

- Codice e testo letterale. Nell'editor di codice è possibile usare l'arabo o l'ebraico per assegnare nomi a classi, funzioni, variabili, proprietà, valori letterali stringa, attributi e così via. Tuttavia l'editor non supporta l'ordine di lettura da destra a sinistra: il testo inizia sempre sul margine sinistro.

    > [!TIP]
    > È consigliabile inserire i valori letterali stringa nei file di risorse anziché impostarli come hardcoded nei programmi. Per altre informazioni, vedere [Risorse nelle applicazioni desktop (.NET Framework)](/dotnet/framework/resources/index).

    > [!NOTE]
    > È necessario mantenere la coerenza nei riferimenti a oggetti denominati in arabo ed ebraico. Se ad esempio si usano le linee kashida nel nome di una variabile in arabo, è necessario usare sempre la notazione kashida quando si fa riferimento alla variabile. In caso contrario, si verificheranno errori.

- Commenti del codice. È possibile creare commenti in arabo o in ebraico. È possibile usare queste lingue anche nello strumento per la generazione di commenti.
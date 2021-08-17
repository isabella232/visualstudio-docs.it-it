---
title: Limitare la strumentazione a funzioni specifiche | Microsoft Docs
description: Informazioni su come limitare la strumentazione e la raccolta dati a una o più funzioni impostando le opzioni nella pagina Avanzate o nelle pagine delle proprietà binarie di destinazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 23924193840226117c6e63541f8288faf8962be2781d634b1040964f3202571f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396487"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Procedura: Limitare la strumentazione a funzioni specifiche
È possibile limitare la strumentazione e la raccolta dei dati a una o più funzioni impostando le opzioni nella pagina **Avanzate** di **Sessione prestazioni** o nelle pagine delle proprietà del file binario di destinazione:

- Se si specificano le funzioni nella pagina delle proprietà della sessione di prestazioni, solo tali funzioni vengono instrumentate in tutti i file binari instrumentati della sessione.

- Se si specificano le funzioni nella pagina delle proprietà del file binario di destinazione, solo le funzioni presenti in quel determinato file binario vengono instrumentate. Le funzioni negli altri file binari delle prestazioni vengono instrumentate con la modalità consueta.

  Questo tipo di limitazione della raccolta dei dati è supportato solo quando viene selezionato il metodo di profilatura della strumentazione.

> [!NOTE]
> È inoltre possibile usare la pagina **Avanzate** delle pagine delle proprietà di **Sessione prestazioni** per impostare le altre opzioni disponibili nello strumento di strumentazione da riga di comando [VSInstr](../profiling/vsinstr.md) disponibile negli strumenti di profilatura.

### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Per limitare la strumentazione a specifiche funzioni in una sessione di prestazioni

1. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul nome della sessione e quindi scegliere **Proprietà**.

    Viene visualizzata la finestra di dialogo **Pagine delle proprietà**.

2. Nella finestra di dialogo **Pagine delle proprietà** fare clic su **Avanzate**.

3. Nella casella di testo **Opzioni di strumentazione aggiuntive** usare la sintassi seguente per digitare il nome delle funzioni da instrumentare:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec` è il nome dello spazio dei nomi e della funzione Il formato è `Namespace` **::** `FunctionName` . Usare un punto e virgola per separare più funzioni. Usare un asterisco (\*) per specificare un carattere jolly per uno o più caratteri. Ad esempio, **/include: MyNS::\\*** specifica tutte le funzioni nello spazio dei nomi MyNS.

   > [!NOTE]
   > Per elencare le funzioni in un file binario, aprire una finestra del prompt dei comandi nella directory di installazione degli strumenti di profilatura (vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)) e quindi digitare **vsinstr /DumpFuncs**

### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Per limitare la strumentazione a specifiche funzioni in un file binario

1. In **Esplora prestazioni** individuare il nome del file binario nel nodo **Destinazioni** della sessione di prestazioni.

2. Fare clic con il pulsante destro del mouse sul nome del file binario e quindi scegliere **Proprietà**.

    Viene visualizzata la finestra di dialogo **Pagine delle proprietà**.

3. Nella finestra di dialogo **Pagine delle proprietà** fare clic su **Avanzate**.

4. Nella casella di testo **Opzioni di strumentazione aggiuntive** usare la sintassi seguente per digitare il nome delle funzioni da instrumentare:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec` è il nome dello spazio dei nomi e della funzione Il formato è `Namespace` **::** `FunctionName` . Usare un punto e virgola per separare più funzioni. Usare un asterisco (\*) per specificare un carattere jolly per uno o più caratteri. Ad esempio, **/include: MyNS::\\*** specifica tutte le funzioni nello spazio dei nomi MyNS.

   > [!NOTE]
   > Per elencare le funzioni in un file binario, aprire una finestra del prompt dei comandi nella directory di installazione degli strumenti di profilatura (vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)) e quindi digitare **vsinstr /DumpFuncs**

## <a name="see-also"></a>Vedi anche
- [Controllare la raccolta dati](../profiling/controlling-data-collection.md)
- [Procedura: Limitare la strumentazione a specifiche DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)
- [Procedura: Specificare opzioni di strumentazione aggiuntive](../profiling/how-to-specify-additional-instrumentation-options.md)

---
title: Eseguire il debug .NET Framework origine | Microsoft Docs
description: Informazioni su come eseguire il debug .NET Framework origine. È necessario configurarlo e scaricare i simboli di debug.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.topic: how-to
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 5340cacf63f2371134641cfa09f873528e11fd94
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161206"
---
# <a name="how-to-debug-net-framework-source"></a>Procedura: Eseguire il debug del codice sorgente di .NET Framework

Per eseguire il debug .NET Framework'origine, è necessario:

- Abilitare l'esecuzione di istruzioni .NET Framework origine.

- Avere accesso ai simboli di debug per il codice.

  È possibile scegliere di scaricare immediatamente i simboli di debug o impostare le opzioni per il download successivo. Se i simboli non vengono scaricati immediatamente, verranno scaricati al successivo avvio del debug dell'app. Durante il debug, è anche possibile usare le **finestre Moduli** o **Stack di** chiamate per scaricare e caricare i simboli.

### <a name="to-enable-stepping-into-net-framework-source"></a>Per abilitare l'esecuzione di istruzioni .NET Framework origine

1. In **Strumenti** (o **Debug**) > **Debug** generale selezionare Abilita istruzione  >    >   **.NET Framework'origine**.

   - Se Just My Code è attivato, viene visualizzata una finestra di dialogo con un avviso indicante che Just My Code è stato disabilitato. Selezionare **OK**.

   - Se non è stata impostata una cache dei simboli locale, viene visualizzata una finestra di dialogo di avviso che indica che è stata impostata una cache dei simboli predefinita. Selezionare **OK**.

1. Selezionare **OK** per chiudere la **finestra di dialogo** Opzioni.

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Per impostare o modificare i percorsi di origine dei simboli e il comportamento di caricamento

1. Selezionare la **categoria Simboli** in **Strumenti** (o **Debug)**> **opzioni**  >  **debug**.

1. Nella pagina **Simboli** in Percorsi file di **simboli (con estensione pdb)** selezionare Server di simboli **Microsoft** per accedere ai simboli dai server di simboli Microsoft pubblici. Selezionare i pulsanti della barra degli strumenti per aggiungere altre posizioni dei simboli e modificare l'ordine di caricamento.

1. Per modificare la cache dei simboli locali, modificare o passare a un percorso diverso in **Memorizzare i simboli nella directory**.

1. Per scaricare immediatamente i simboli, selezionare **Carica tutti i simboli**. Questo pulsante è disponibile solo durante il debug.

   Se non si scaricano i simboli ora, questi verranno scaricati al successivo avvio del debug.

1. Selezionare **OK** per chiudere la **finestra di dialogo** Opzioni.

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>Per caricare i simboli dalle finestre Moduli o Stack di chiamate

1. Durante il debug, aprire la finestra selezionando Debug Windows Moduli (oppure premere  >    >   **CTRL+ALT+U)** o Esegui debug Windows Stack di chiamate  >    >   **(CTRL+ALT+C).**

1. Fare clic con il pulsante destro del mouse su un modulo per il quale non sono stati caricati i simboli. Nella finestra **Moduli lo** stato di caricamento dei simboli si trova nella **colonna Stato** simboli. Nella finestra **Stack di** chiamate lo stato si trova nella **colonna Stato** frame e il frame è disattivato.

   - Selezionare **Carica simboli** dal menu per individuare e caricare i file di simboli da una cartella nel computer.

   - Selezionare **Informazioni sul caricamento dei** simboli per visualizzare le posizioni in cui il debugger ha cercato i simboli.

   - Selezionare **Simbolo Impostazioni** per aprire la **pagina** Simboli. Nella pagina **Simboli** in Percorsi file di **simboli (con estensione pdb)** selezionare Server di simboli **Microsoft** per accedere ai simboli dai server di simboli Microsoft pubblici. Selezionare i pulsanti della barra degli strumenti per aggiungere altre posizioni dei simboli e modificare l'ordine di caricamento. Selezionare **OK** per chiudere la finestra di dialogo.

### <a name="see-also"></a>Vedi anche
- [Debug di codice gestito](../debugger/debugging-managed-code.md)
- [Specificare il simbolo (con estensione pdb) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

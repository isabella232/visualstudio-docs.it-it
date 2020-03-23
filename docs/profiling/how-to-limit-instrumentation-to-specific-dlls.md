---
title: 'Procedura: Limitare la strumentazione a specifiche DLL | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 066262a3fae35e82904b011165813e9dd75d9987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778817"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Procedura: Limitare la strumentazione a DLL specifiche

Usando il metodo di profilatura della strumentazione, è possibile limitare la raccolta dei dati di profilatura a una o più DLL di un'applicazione. Per profilare una o più DLL in un'applicazione, creare una sessione di prestazioni che include l'oggetto . *dll* come destinazioni. È possibile specificare le DLL da profilare come progetti in una soluzione di Visual Studio o come file binari indipendenti.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Per limitare la strumentazione a specifiche DLL di una soluzione di Visual Studio

1. Aprire la soluzione contenente la DLL in Visual Studio.

2. Nel menu **Analizza** selezionare **Avvia Creazione guidata sessione di prestazioni**.

3. Scegliere **Strumentazione** come metodo di profilatura e quindi fare clic su **Avanti**.

4. Dalla **sezione Quale delle seguenti destinazioni disponibili si desidera profilare?**, selezionare il nome del file . *dll* , quindi fare clic su **Avanti**.

5. Fare clic su **Fine** per chiudere la procedura guidata e visualizzare la nuova sessione di prestazioni nella finestra **Esplora prestazioni**.

6. Fare clic con il pulsante destro del mouse su **Destinazioni** e quindi selezionare **Aggiungi progetto di destinazione**.

7. Dall'elenco **Aggiungi progetto di destinazione** selezionare il progetto eseguibile da usare per verificare la DLL.

     Facoltativa. È possibile aggiungere qualsiasi progetto DLL che si vuole profilare.

8. Per impedire la raccolta di dati per un progetto aggiunto, fare clic con il pulsante destro del mouse sul nome del progetto e quindi deselezionare la casella di controllo **Strumento**.

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Per specificare determinate DLL da profilare come file binari indipendenti

1. Aprire Visual Studio.

2. Nel menu **Analizza** selezionare **Avvia Creazione guidata sessione di prestazioni**.

3. In **Specificare le destinazioni da profilare** selezionare **Profilatura di una libreria a collegamento dinamico (.DLL)** e quindi fare clic su **Avanti**.

4. Nella seconda pagina della procedura guidata eseguire i passaggi seguenti:

    - Digitare il percorso e il nome file del file . *dll* che si desidera profilare nel **percorso dll**. È anche possibile fare clic sul pulsante con i puntini di sospensione (...) per individuare il file nella finestra di dialogo **Libreria a collegamento dinamico da profilare**. Si noti che è necessario specificare la copia del file . *dll* che verrà avviato dall'eseguibile (.* exe*) selezionato successivamente.

    - Digitare il percorso e il nome file dell'eseguibile (.* exe*) che eserciterà il file . *dll* nel **percorso eseguibile**. È anche possibile fare clic sul pulsante con i puntini di sospensione (...) per individuare il file nella finestra di dialogo **Eseguibile da avviare**.

    - Facoltativa. Digitare gli argomenti della riga di comando da passare al file eseguibile in **Argomenti della riga di comando**. Se necessario, specificare la directory di lavoro per l'applicazione in **Directory di lavoro**.

    - Fare clic su **Avanti**.

5. Scegliere **Strumentazione** come metodo di profilatura e quindi fare clic su **Avanti**.

6. Fare clic su **Fine** per chiudere la procedura guidata e visualizzare la nuova sessione di prestazioni nella finestra **Esplora prestazioni**.

7. Facoltativa. Per aggiungere altro . *dll,* fare clic con il pulsante destro del mouse su **Destinazioni,** quindi selezionare **Aggiungi binario**di destinazione . Selezionare i file dalla finestra di dialogo **Aggiungi binario di destinazione**.

    > [!NOTE]
    > Non specificare l'eseguibile (.* exe*) che esercita le DLL.

## <a name="see-also"></a>Vedere anche

[Controllo della raccolta dati](../profiling/controlling-data-collection.md)
[Procedura: limitare la strumentazione a funzioni specificheControl](../profiling/how-to-limit-instrumentation-to-specific-functions.md) data collection How to: Limit instrumentation to specific functions

---
title: 'Procedura: Eseguire il debug in modalità mista | Microsoft Docs'
ms.date: 11/05/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f58c51bf1b610375c6204e27d064870ce1f76d04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894378"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>Procedura: Eseguire il debug in modalità mista (C#, C++, Visual Basic)

Le procedure seguenti descrivono come abilitare il debug per codice gestito e nativo contemporaneamente, noto anche come in modalità mista di debug. Esistono due scenari di debug in modalità mista:

- L'app che chiama una DLL è scritta in codice nativo e gestita la DLL.

- L'app che chiama una DLL è scritta in codice gestito e la DLL è in codice nativo. Per un'esercitazione che illustra questo scenario in modo più dettagliato, vedere [eseguire il Debug di codice gestito e nativo](../debugger/how-to-debug-managed-and-native-code.md).

È possibile abilitare i debugger nativi e gestiti al progetto di app chiamante **proprietà** pagine. Le impostazioni variano tra le app native e gestite.

Se non si ha accesso al progetto dell'app chiamante, è possibile eseguire il debug di DLL dal progetto di DLL. Modalità mista per eseguire il debug solo il progetto DLL non è necessario. Per altre informazioni, vedere [Procedura: Eseguire il debug da un progetto DLL](../debugger/how-to-debug-from-a-dll-project.md).

> [!NOTE]
> Le finestre di dialogo e i comandi visualizzati potrebbero essere diversi da quelli di questo articolo, a seconda dell'edizione o delle impostazioni di Visual Studio. Per modificare le impostazioni, scegliere **degli strumenti** > **Importa / Esporta impostazioni**. Per altre informazioni, vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Abilitare il debug in modalità mista per un'app chiamante nativa

1. Selezionare il progetto C++ in **Esplora soluzioni** e fare clic sui **delle proprietà** icona, premere **Alt**+**invio**, o pulsante destro del mouse e scegliere **proprietà**.

1. Nel  **\<progetto > pagine delle proprietà** della finestra, espandere **le proprietà di configurazione**e quindi selezionare **debug**.

1. Impostare **Tipo debugger** su **Misto** o **Automatico**.

1. Scegliere **OK**.

   ![Abilitare il debug in modalità mista](../debugger/media/dbg-mixed-mode-from-native.png "abilitare il debug in modalità mista")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Abilitare il debug in modalità mista per un'app gestita da chiamata

1. Selezionare il progetto c# o Visual Basic **Esplora soluzioni** e selezionare il **delle proprietà** icona, premere **Alt**+**invio**, oppure fare doppio clic su e scegliere **delle proprietà**.

1. Selezionare il **Debug** scheda e quindi selezionare **Abilita debug codice nativo**.

1. Chiudere la pagina delle proprietà per salvare le modifiche.

   ![Abilita debug codice nativo](../debugger/media/dbg-mixed-mode-from-csharp.png "Abilita debug codice nativo")

> [!NOTE]
> Nella maggior parte delle versioni di Visual Studio a partire da Visual Studio 2017 è necessario usare il file *launchSettings.json*, anziché le proprietà del progetto, per abilitare il debug in modalità mista per il codice nativo in un'app .NET Core. Per informazioni dettagliate, vedere [eseguire il Debug di codice gestito e nativo](../debugger/how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Vedere anche

- [Procedura: Eseguire il debug da un progetto DLL](../debugger/how-to-debug-from-a-dll-project.md)
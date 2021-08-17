---
title: Eseguire il debug in modalità mista | Microsoft Docs
description: Informazioni su come abilitare il debug in modalità mista (codice gestito e nativo insieme) nelle pagine delle proprietà del progetto dell'app chiamante.
ms.custom: SEO-VS-2020
ms.date: 11/05/2018
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0e25cd55efbd7d686a8251b2fb6da399e4977e50
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105236"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>Procedura: Eseguire il debug in modalità mista (C#, C++, Visual Basic)

Le procedure seguenti descrivono come abilitare il debug per il codice gestito e nativo insieme, noto anche come debug in modalità mista. Esistono due scenari di debug in modalità mista:

- L'app che chiama una DLL viene scritta in codice nativo e la DLL viene gestita.

- L'app che chiama una DLL è scritta in codice gestito e la DLL è in codice nativo. Per un'esercitazione che illustra questo scenario in modo più dettagliato, vedere [Eseguire il debug di codice gestito e nativo.](../debugger/how-to-debug-managed-and-native-code.md)

È possibile abilitare debugger sia gestiti che nativi  nelle pagine delle proprietà del progetto dell'app chiamante. Le impostazioni differiscono tra app native e gestite.

Se non si ha accesso al progetto di un'app chiamante, è possibile eseguire il debug della DLL dal progetto DLL. Non è necessaria la modalità mista per eseguire il debug solo del progetto DLL. Per altre informazioni, vedere [Procedura: Eseguire il debug da un progetto DLL.](../debugger/how-to-debug-from-a-dll-project.md)

> [!NOTE]
> Le finestre di dialogo e i comandi visualizzati potrebbero essere diversi da quelli di questo articolo, a seconda delle impostazioni o dell'edizione Visual Studio impostazioni. Per modificare le impostazioni, **scegliere** Strumenti  >  **Importa ed esporta Impostazioni**. Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Abilitare il debug in modalità mista per un'app chiamante nativa

1. Selezionare il progetto C++ in **Esplora soluzioni**  fare clic sull'icona Proprietà, premere **ALT** INVIO oppure fare clic con il pulsante destro del mouse + e **scegliere Proprietà.**

1. Nella finestra **\<Project> di dialogo Pagine** delle proprietà espandere Proprietà di **configurazione** e quindi selezionare **Debug.**

1. Impostare **Tipo debugger** su **Misto** o **Automatico**.

1. Selezionare **OK**.

   ![Abilitare il debug in modalità mista](../debugger/media/dbg-mixed-mode-from-native.png "Abilitare il debug in modalità mista")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Abilitare il debug in modalità mista per un'app chiamante gestita

1. Selezionare il progetto C# o Visual Basic in **Esplora soluzioni** e  selezionare l'icona Proprietà, premere **ALT** INVIO oppure fare clic con il pulsante destro del mouse + e **scegliere Proprietà.**

1. Selezionare la **scheda Debug** e quindi selezionare Abilita debug **codice nativo.**

1. Chiudere la pagina delle proprietà per salvare le modifiche.

   ![Abilita debug del codice nativo](../debugger/media/dbg-mixed-mode-from-csharp.png "Abilita debug del codice nativo")

> [!NOTE]
> Nella maggior parte delle versioni di Visual Studio a partire da Visual Studio 2017 è necessario usare il file *launchSettings.json*, anziché le proprietà del progetto, per abilitare il debug in modalità mista per il codice nativo in un'app .NET Core. Per informazioni dettagliate, vedere [Eseguire il debug di codice gestito e nativo.](../debugger/how-to-debug-managed-and-native-code.md)

## <a name="see-also"></a>Vedi anche

- [Procedura: Eseguire il debug da un progetto DLL](../debugger/how-to-debug-from-a-dll-project.md)
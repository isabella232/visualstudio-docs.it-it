---
title: Eseguire il debug in modalità mista | Microsoft Docs
description: Vedere come abilitare il debug in modalità mista (codice gestito e nativo insieme) nelle pagine delle proprietà del progetto dell'app chiamante.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 123fb61cb223d8db3c447f5925639df33a2b3e11
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903987"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>Procedura: eseguire il debug in modalità mista (C#, C++, Visual Basic)

Nelle procedure seguenti viene descritto come abilitare il debug per il codice gestito e il codice nativo insieme, noto anche come debug in modalità mista. Esistono due scenari di debug in modalità mista:

- L'app che chiama una DLL viene scritta in codice nativo e la DLL è gestita.

- L'app che chiama una DLL viene scritta in codice gestito e la DLL si trova nel codice nativo. Per un'esercitazione che illustra in modo dettagliato questo scenario, vedere eseguire il [debug di codice nativo e gestito](../debugger/how-to-debug-managed-and-native-code.md).

È possibile abilitare sia i debugger gestiti sia quelli nativi nelle pagine delle **Proprietà** del progetto di applicazione chiamante. Le impostazioni sono diverse tra le app native e quelle gestite.

Se non si ha accesso a un progetto di app chiamante, è possibile eseguire il debug della DLL dal progetto DLL. Non è necessaria la modalità mista per eseguire il debug solo del progetto di DLL. Per altre informazioni, vedere [procedura: eseguire il debug da un progetto di dll](../debugger/how-to-debug-from-a-dll-project.md).

> [!NOTE]
> Le finestre di dialogo e i comandi visualizzati potrebbero non corrispondere a quelli di questo articolo, a seconda delle impostazioni o dell'edizione di Visual Studio. Per modificare le impostazioni, scegliere **strumenti**  >  **Importa/Esporta impostazioni**. Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Abilitare il debug in modalità mista per un'app chiamante nativa

1. Selezionare il progetto C++ in **Esplora soluzioni** e fare clic sull'icona delle **Proprietà** , premere **ALT** + **invio** oppure fare clic con il pulsante destro del mouse e scegliere **Proprietà**.

1. Nella finestra di dialogo **\<Project> pagine delle proprietà** espandere **proprietà di configurazione**, quindi selezionare **debug**.

1. Impostare **Tipo debugger** su **Misto** o **Automatico**.

1. Selezionare **OK**.

   ![Abilitare il debug in modalità mista](../debugger/media/dbg-mixed-mode-from-native.png "Abilitare il debug in modalità mista")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Abilitare il debug in modalità mista per un'app chiamante gestita

1. Selezionare il progetto C# o Visual Basic in **Esplora soluzioni** e selezionare l'icona delle **Proprietà** , premere **ALT** + **invio** oppure fare clic con il pulsante destro del mouse e scegliere **Proprietà**.

1. Selezionare la scheda **debug** e quindi selezionare **Abilita il debug del codice nativo**.

1. Chiudere la pagina delle proprietà per salvare le modifiche.

   ![Abilita debug del codice nativo](../debugger/media/dbg-mixed-mode-from-csharp.png "Abilita debug del codice nativo")

> [!NOTE]
> Nella maggior parte delle versioni di Visual Studio a partire da Visual Studio 2017 è necessario usare il file *launchSettings.json*, anziché le proprietà del progetto, per abilitare il debug in modalità mista per il codice nativo in un'app .NET Core. Per informazioni dettagliate, vedere [eseguire il debug di codice nativo e gestito](../debugger/how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Vedere anche

- [Procedura: Eseguire il debug da un progetto DLL](../debugger/how-to-debug-from-a-dll-project.md)
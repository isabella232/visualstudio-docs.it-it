---
title: Eseguire il debug da una dll Project | Microsoft Docs
description: È possibile avviare il debug di un progetto DLL dal progetto stesso, specificando l'app chiamante nelle proprietà del progetto. Vedi questo articolo per altri dettagli.
ms.custom: SEO-VS-2020
ms.date: 3/30/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 61599a878d73ab188ee8e05bf7f1cf5c314ac42f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120959"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>Procedura: Eseguire il debug da un progetto DLL in Visual Studio (C#, C++, Visual Basic, F#)

Un modo per eseguire il debug di un progetto DLL è specificare l'app chiamante nelle proprietà del progetto DLL. È quindi possibile avviare il debug dal progetto DLL stesso. Per il funzionamento di questo metodo, l'app deve chiamare la stessa DLL nello stesso percorso di quello configurato. Se l'app trova e carica una versione diversa della DLL, tale versione non conterrà i punti di interruzione. Per altri metodi di debug delle DLL, vedere [Debug di progetti DLL](../debugger/debugging-dll-projects.md).

Se l'app gestita chiama una DLL nativa o l'app nativa chiama una DLL gestita, è possibile eseguire il debug sia della DLL che dell'app chiamante. Per altre informazioni, vedere [Procedura: Eseguire il debug in modalità mista.](../debugger/how-to-debug-in-mixed-mode.md)

I progetti DLL nativi e gestiti hanno impostazioni diverse per specificare le app chiamanti.

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Specificare un'app chiamante in un progetto DLL nativo

1. Selezionare il progetto DLL C++ in **Esplora soluzioni**. Selezionare **l'icona** Proprietà, premere **ALT INVIO** oppure fare clic con il pulsante destro del + mouse e scegliere **Proprietà**.

1. Nella finestra **\<Project> di dialogo** Pagine delle proprietà verificare che il **campo Configurazione** nella parte superiore della finestra sia impostato su **Debug**.

1. Selezionare **Debug delle proprietà di**  >  **configurazione**.

1. **Nell'elenco Debugger da** avviare scegliere Local Windows **Debugger** o Remote **Windows Debugger**.

1. Nella casella **Comando** o **Comando remoto** aggiungere il percorso completo e il nome file dell'app chiamante, ad esempio un file *.exe* remoto.

   ![Eseguire il debug Finestra Proprietà](../debugger/media/dbg-debugging-properties-dll.png "Eseguire il debug Finestra Proprietà")

1. Aggiungere tutti gli argomenti del programma necessari nella casella **Argomenti del comando**.

1. Selezionare **OK**.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Specificare un'app chiamante in un progetto DLL gestito

1. Selezionare il progetto DLL C# o Visual Basic in **Esplora soluzioni**. Selezionare **l'icona** Proprietà, premere **ALT INVIO** oppure fare clic con il pulsante destro del + mouse e scegliere **Proprietà**.

1. Assicurarsi che il campo **Configurazione** nella parte superiore della finestra sia impostato su **Debug**.

1. In **Azione di avvio**:

   - Per .NET Framework DLL, selezionare **Avvia** programma esterno e aggiungere il percorso completo e il nome dell'app chiamante.

   - In caso contrario, selezionare **Avvia browser con URL** e compilare l'URL di un'app ASP.NET locale.

   - Per le DLL .NET Core, la **pagina Proprietà** debug è diversa. Selezionare **Eseguibile** **nell'elenco a** discesa Avvia e quindi aggiungere il percorso completo e il nome dell'app chiamante nel **campo Eseguibile.**

1. Aggiungere eventuali argomenti della riga di comando necessari nel campo **Argomenti della** riga di comando o **Argomenti applicazione.**

   ![Debug di C# Finestra Proprietà](../debugger/media/dbg-debugging-properties-dll-csharp.png "Debug di C# Finestra Proprietà")

1. Usare **File**  >  **Save Selected Items (Salva elementi selezionati)** o **CTRL** + **S** per salvare le modifiche.

## <a name="debug-from-the-dll-project"></a>Eseguire il debug dal progetto DLL

1. Impostare punti di interruzione nel progetto DLL.

1. Fare clic con il pulsante destro del mouse sul progetto DLL e scegliere **Imposta come avvio Project**.

1. Assicurarsi che il **campo Configurazione soluzioni** sia impostato su **Debug**. Premere **F5,** fare clic sulla freccia **Start** verde o selezionare **Debug**  >  **Avvia debug**.

Altri suggerimenti:

- Se il debug non ha raggiunto i punti di interruzione, assicurarsi che l'output della DLL (per impostazione predefinita, la cartella *\<project> \Debug)* sia il percorso chiamato dall'app chiamante.

- Se si vuole interrompere il codice in un'app chiamante gestita da una DLL nativa o viceversa, abilitare il debug [in modalità mista.](../debugger/how-to-debug-in-mixed-mode.md)

- In alcuni scenari potrebbe essere necessario indicare al debugger dove trovare il codice sorgente. Per altre informazioni, vedere Usare le pagine Nessun simbolo [caricato/Nessuna origine caricata](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#use-the-no-symbols-loadedno-source-loaded-pages).

## <a name="see-also"></a>Vedi anche
- [Debug di progetti DLL](../debugger/debugging-dll-projects.md)
- [Impostazioni di progetto per configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)

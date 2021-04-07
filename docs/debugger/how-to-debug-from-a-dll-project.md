---
title: Eseguire il debug da un progetto di DLL | Microsoft Docs
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
ms.workload:
- multiple
ms.openlocfilehash: 7846cc3fd17b46365da59f6fe1a744032cb8ba14
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/31/2021
ms.locfileid: "106083642"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>Procedura: eseguire il debug da un progetto di DLL in Visual Studio (C#, C++, Visual Basic, F #)

Un modo per eseguire il debug di un progetto di DLL consiste nel specificare l'app chiamante nelle proprietà del progetto DLL. È quindi possibile avviare il debug dal progetto di DLL. Per il corretto funzionamento di questo metodo, l'app deve chiamare la stessa DLL nella stessa posizione di quella configurata. Se l'app trova e carica una versione diversa della DLL, tale versione non conterrà i punti di interruzione. Per altri metodi di debug delle dll, vedere [debug di progetti DLL](../debugger/debugging-dll-projects.md).

Se l'app gestita chiama una DLL nativa o l'app nativa chiama una DLL gestita, è possibile eseguire il debug sia della DLL che dell'app chiamante. Per altre informazioni, vedere [procedura: eseguire il debug in modalità mista](../debugger/how-to-debug-in-mixed-mode.md).

I progetti DLL nativi e gestiti hanno impostazioni diverse per specificare le app di chiamata.

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Specificare un'app chiamante in un progetto DLL nativo

1. Selezionare il progetto DLL C++ in **Esplora soluzioni**. Selezionare l'icona delle **Proprietà** , premere **ALT** + **invio** oppure fare clic con il pulsante destro del mouse e scegliere **Proprietà**.

1. Nella finestra di dialogo **\<Project> pagine delle proprietà** assicurarsi che il campo **configurazione** nella parte superiore della finestra sia impostato su **debug**.

1. Selezionare **proprietà di configurazione**  >  **debug**.

1. Nell'elenco **debugger da avviare** scegliere **debugger Windows locale** o **debugger Windows remoto**.

1. Nella casella **comando** o **comando remoto** aggiungere il percorso completo e il nome file dell'app chiamante, ad esempio un file con estensione *exe* .

   ![Finestra Proprietà di debug](../debugger/media/dbg-debugging-properties-dll.png "Finestra Proprietà di debug")

1. Aggiungere tutti gli argomenti del programma necessari nella casella **Argomenti del comando**.

1. Selezionare **OK**.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Specificare un'app chiamante in un progetto DLL gestito

1. Selezionare il progetto di DLL C# o Visual Basic in **Esplora soluzioni**. Selezionare l'icona delle **Proprietà** , premere **ALT** + **invio** oppure fare clic con il pulsante destro del mouse e scegliere **Proprietà**.

1. Assicurarsi che il campo **Configurazione** nella parte superiore della finestra sia impostato su **Debug**.

1. In **azione di avvio**:

   - Per .NET Framework dll, selezionare **Avvia programma esterno** e aggiungere il percorso completo e il nome dell'app chiamante.

   - In alternativa, selezionare **Avvia browser con URL** e compilare l'URL di un'app ASP.NET locale.

   - Per le DLL di .NET Core, la pagina delle proprietà di **debug** è diversa. Selezionare **eseguibile** dall'elenco a discesa **Avvia** e quindi aggiungere il percorso completo e il nome dell'app chiamante nel campo **eseguibile** .

1. Aggiungere gli argomenti della riga di comando necessari nel campo argomenti della **riga di comando** o **argomenti dell'applicazione** .

   ![Finestra Proprietà di debug C#](../debugger/media/dbg-debugging-properties-dll-csharp.png "Finestra Proprietà di debug C#")

1. Usare **file**  >  **Salva elementi selezionati** o **CTRL** + **S** per salvare le modifiche.

## <a name="debug-from-the-dll-project"></a>Eseguire il debug dal progetto di DLL

1. Impostare i punti di interruzione nel progetto di DLL.

1. Fare clic con il pulsante destro del mouse sul progetto DLL e scegliere **Imposta come progetto di avvio**.

1. Verificare che il campo **configurazione soluzioni** sia impostato su **debug**. Premere **F5**, fare clic sulla freccia di **inizio** verde oppure selezionare **debug**  >  **Avvia debug**.

Altri suggerimenti:

- Se il debug non raggiunge i punti di interruzione, assicurarsi che l'output della DLL (per impostazione predefinita, la cartella *\<project> \Debug* ) sia il percorso chiamato dall'app chiamante.

- Se si desidera suddividere il codice in un'app chiamante gestita da una DLL nativa o viceversa, abilitare il debug in [modalità mista](../debugger/how-to-debug-in-mixed-mode.md).

- In alcuni scenari potrebbe essere necessario indicare al debugger dove trovare il codice sorgente. Per altre informazioni, vedere [usare le pagine nessun simbolo caricato/nessuna origine caricata](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#use-the-no-symbols-loadedno-source-loaded-pages).

## <a name="see-also"></a>Vedi anche
- [Debug di progetti DLL](../debugger/debugging-dll-projects.md)
- [Impostazioni di progetto per configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)

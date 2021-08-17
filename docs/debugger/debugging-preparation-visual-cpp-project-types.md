---
title: Preparare il debug di progetti C++ | Microsoft Docs
description: Ottenere informazioni sulla preparazione per il debug dei tipi di progetto di base creati Visual C++ modelli di progetto in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- project templates, debugging
- C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 461fbf9ca8518326c800baabbb4d67585895c7e9c23445d115dc6eb3c4f971c9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420327"
---
# <a name="debugging-preparation-c-project-types"></a>Preparazione del debug: tipi di Project C++
In questa sezione viene descritto come eseguire il debug dei tipi di progetto di base creati mediante i modelli di progetto [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].

 Si noti che i tipi di progetto che creano DLL come output sono stati raggruppati in Debug di progetti [DLL](../debugger/debugging-dll-projects.md) a causa delle funzionalità comuni che condividono.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> In questo argomento
 [Impostazioni consigliate per le proprietà](#BKMK_Recommended_Property_Settings)

 [Progetti Win32](#BKMK_Win32_Projects)

- [Per eseguire il debug di un'applicazione Win32 in C o C++](#BKMK_To_debug_a_C_or_C___Win32_application)

- [Per impostare manualmente una configurazione di debug](#BKMK_To_manually_set_a_Debug_configuration)

## <a name="recommended-property-settings"></a><a name="BKMK_Recommended_Property_Settings"></a> Impostazioni consigliate per le proprietà
 Determinate proprietà devono essere impostate nello stesso modo per tutti gli scenari di debug non gestito. Nelle tabelle riportate di seguito sono indicate le impostazioni consigliate delle proprietà. Le impostazioni non specificate in queste tabelle possono variare in base al tipo di progetto non gestito. Per altre informazioni, vedere [Project Impostazioni per una configurazione di debug C++.](../debugger/project-settings-for-a-cpp-debug-configuration.md)

### <a name="configuration-properties-124-cc-124-optimization-node"></a>Proprietà di configurazione &#124; nodo Ottimizzazione &#124; C/C++

|Nome della proprietà|Impostazione|
|-------------------|-------------|
|**Ottimizzazione**|Impostare su **Disabilitato (/0d).** L'esecuzione del debug di codice ottimizzato è più complessa perché le istruzioni generate non corrispondono direttamente al codice sorgente. Se si nota un bug presente solo nel codice ottimizzato del programma, è possibile attivare questa impostazione, tenendo però presente che il codice riportato nella finestra **Disassembly** è generato da codice sorgente ottimizzato che potrebbe non corrispondere a quanto visualizzato nelle finestre del codice sorgente. È possibile che altre funzionalità, ad esempio il debug passo a passo, non funzionino come previsto.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>Proprietà di configurazione &#124; nodo Debug &#124; linker

|Nome della proprietà|Impostazione|
|-------------------|-------------|
|**Genera informazioni di debug**|Si consiglia di impostare questa opzione sempre su **Sì (/DEBUG)** per creare i simboli di debug e i file necessari per il debug. Quando l'applicazione passa alla fase di produzione, è possibile disattivare questa opzione.|

 [Contenuto dell'argomento](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="win32-projects"></a><a name="BKMK_Win32_Projects"></a> Progetti Win32
 Le applicazioni Win32 sono programmi Windows tradizionali scritti in C o C++. Il debug di questo tipo di applicazione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è una procedura molto semplice.

 Le applicazioni Win32 includono applicazioni MFC e progetti ATL. Utilizzano API Windows e possono utilizzare MFC o ATL, ma non Common Language Runtime (CLR). Possono, tuttavia, chiamare codice gestito che utilizza CLR.

 Nella procedura riportata di seguito viene descritto come eseguire il debug di un progetto Win32 dall'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per eseguire il debug di un'applicazione Win32 è anche possibile avviare l'applicazione all'esterno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e stabilire una connessione. Per altre informazioni, vedere [Connettersi a processi in esecuzione.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

### <a name="to-debug-a-c-or-c-win32-application"></a><a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Per eseguire il debug di un'applicazione Win32 C o C++

1. Aprire il progetto in Visual Studio.

2. Scegliere **Avvia** dal menu **Debug**.

3. Eseguire il debug usando le tecniche descritte in [Esaminare prima di tutto il debugger.](../debugger/debugger-feature-tour.md)

### <a name="to-manually-set-a-debug-configuration"></a><a name="BKMK_To_manually_set_a_Debug_configuration"></a> Per impostare manualmente una configurazione di debug

1. Nel menu **Visualizza** fare clic su **Pagine delle proprietà**.

2. Se non è ancora aperto, fare clic sul nodo **Proprietà di configurazione** per espanderlo

3. Selezionare **Generale** e impostare il valore della riga **Output** su **Debug**.

4. Espandere il nodo **C/C++** e selezionare **Generale**.

    Nella riga **Debug** specificare il tipo di informazioni di debug che dovrà essere generato dal compilatore. I valori tra cui è possibile scegliere includono **Database di programma (/Zi)** o **Database di programma per Modifica e continuazione (/ZI)**.

5. Selezionare **Ottimizzazione** e nella riga **Ottimizzazione** scegliere **Disabilitato (/0d)** dall'elenco a discesa.

    L'esecuzione del debug di codice ottimizzato è più complessa perché le istruzioni generate non corrispondono direttamente al codice sorgente. Se si nota un bug presente solo nel codice ottimizzato del programma, è possibile attivare questa impostazione, tenendo però presente che il codice riportato nella finestra Disassembly è generato da codice sorgente ottimizzato che potrebbe non corrispondere a quanto visualizzato nelle finestre del codice sorgente. È probabile che alcune funzionalità, ad esempio il debug passo a passo, non visualizzino i punti di interruzione e i punti di esecuzione in modo corretto.

6. Espandere il nodo **Linker** e selezionare **Debug**. Nella prima riga di **Genera informazioni di debug** selezionare **Sì (/DEBUG)** dall'elenco a discesa. Utilizzare sempre questa impostazione durante il debug.

   Per altre informazioni, vedere Project Impostazioni[per una configurazione di debug C++.](../debugger/project-settings-for-a-cpp-debug-configuration.md)

   [Contenuto dell'argomento](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>Vedi anche
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Project Impostazioni per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Connessione a uno o più programmi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Configurazioni versioni di debug e di rilascio](../debugger/how-to-set-debug-and-release-configurations.md)
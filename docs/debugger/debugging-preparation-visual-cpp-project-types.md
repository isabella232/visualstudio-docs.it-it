---
title: Preparare il debug C++ di progetti | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9c7d223b9ea542177176045c9abd103958e5ae33
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738104"
---
# <a name="debugging-preparation-c-project-types"></a>Preparazione al debug C++ : tipi di progetto
In questa sezione viene descritto come eseguire il debug dei tipi di progetto di base creati mediante i modelli di progetto [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].

 Si noti che i tipi di progetto che creano dll come output sono stati raggruppati in [progetti di dll di debug](../debugger/debugging-dll-projects.md) a causa delle funzionalità comuni condivise.

## <a name="BKMK_In_this_topic"></a> In questo argomento
 [Impostazioni consigliate delle proprietà](#BKMK_Recommended_Property_Settings)

 [Progetti Win32](#BKMK_Win32_Projects)

- [Per eseguire il debug di un'applicazione Win32 in C o C++](#BKMK_To_debug_a_C_or_C___Win32_application)

- [Per impostare manualmente una configurazione di debug](#BKMK_To_manually_set_a_Debug_configuration)

  [Applicazioni Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)

## <a name="BKMK_Recommended_Property_Settings"></a> Impostazioni consigliate delle proprietà
 Determinate proprietà devono essere impostate nello stesso modo per tutti gli scenari di debug non gestito. Nelle tabelle riportate di seguito sono indicate le impostazioni consigliate delle proprietà. Le impostazioni non specificate in queste tabelle possono variare in base al tipo di progetto non gestito. Per altre informazioni, vedere [impostazioni di progetto per C++ una configurazione di debug](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="configuration-properties-124-cc-124-optimization-node"></a>Proprietà &#124; di configurazione CC++ &#124; /nodo di ottimizzazione

|Nome proprietà|Impostazioni|
|-------------------|-------------|
|**Optimization**|Impostare su **Disabilitato (/0d).** L'esecuzione del debug di codice ottimizzato è più complessa perché le istruzioni generate non corrispondono direttamente al codice sorgente. Se si nota un bug presente solo nel codice ottimizzato del programma, è possibile attivare questa impostazione, tenendo però presente che il codice riportato nella finestra **Disassembly** è generato da codice sorgente ottimizzato che potrebbe non corrispondere a quanto visualizzato nelle finestre del codice sorgente. È possibile che altre funzionalità, ad esempio il debug passo a passo, non funzionino come previsto.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>Nodo di &#124; &#124; debug del linker delle proprietà di configurazione

|Nome proprietà|Impostazioni|
|-------------------|-------------|
|**Genera informazioni di debug**|Si consiglia di impostare questa opzione sempre su **Sì (/DEBUG)** per creare i simboli di debug e i file necessari per il debug. Quando l'applicazione passa alla fase di produzione, è possibile disattivare questa opzione.|

 [In questo argomento](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="BKMK_Win32_Projects"></a> Progetti Win32
 Le applicazioni Win32 sono programmi Windows tradizionali scritti in C o C++. Il debug di questo tipo di applicazione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è una procedura molto semplice.

 Le applicazioni Win32 includono applicazioni MFC e progetti ATL. Utilizzano API Windows e possono utilizzare MFC o ATL, ma non Common Language Runtime (CLR). Possono, tuttavia, chiamare codice gestito che utilizza CLR.

 Nella procedura riportata di seguito viene descritto come eseguire il debug di un progetto Win32 dall'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per eseguire il debug di un'applicazione Win32 è anche possibile avviare l'applicazione all'esterno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e stabilire una connessione. Per ulteriori informazioni, vedere [Connetti a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Per eseguire il debug di un'applicazione Win32 in C o C++

1. Aprire il progetto in Visual Studio.

2. Scegliere **Avvia** dal menu **Debug**.

3. Eseguire il debug usando le tecniche descritte in [prima occhiata al debugger](../debugger/debugger-feature-tour.md).

### <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Per impostare manualmente una configurazione di debug

1. Scegliere **Pagine delle proprietà** dal menu **Visualizza**.

2. Se non è ancora aperto, fare clic sul nodo **Proprietà di configurazione** per espanderlo

3. Selezionare **Generale** e impostare il valore della riga **Output** su **Debug**.

4. Espandere il nodo **C/C++** e selezionare **Generale**.

    Nella riga **Debug** specificare il tipo di informazioni di debug che dovrà essere generato dal compilatore. I valori tra cui è possibile scegliere includono **Database di programma (/Zi)** o **Database di programma per Modifica e continuazione (/ZI)** .

5. Selezionare **Ottimizzazione** e nella riga **Ottimizzazione** scegliere **Disabilitato (/0d)** dall'elenco a discesa.

    L'esecuzione del debug di codice ottimizzato è più complessa perché le istruzioni generate non corrispondono direttamente al codice sorgente. Se si nota un bug presente solo nel codice ottimizzato del programma, è possibile attivare questa impostazione, tenendo però presente che il codice riportato nella finestra Disassembly è generato da codice sorgente ottimizzato che potrebbe non corrispondere a quanto visualizzato nelle finestre del codice sorgente. È probabile che alcune funzionalità, ad esempio il debug passo a passo, non visualizzino i punti di interruzione e i punti di esecuzione in modo corretto.

6. Espandere il nodo **Linker** e selezionare **Debug**. Nella prima riga di **Genera informazioni di debug** selezionare **Sì (/DEBUG)** dall'elenco a discesa. Utilizzare sempre questa impostazione durante il debug.

   Per altre informazioni, vedere[impostazioni di progetto per C++ una configurazione di debug](../debugger/project-settings-for-a-cpp-debug-configuration.md).

   [In questo argomento](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="BKMK_Windows_Forms_Applications___NET_"></a> Applicazioni Windows Forms (.NET)
 Il modello **Windows Forms Application (.NET)** consente di creare un'applicazione Windows Forms in [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. Per altre informazioni, vedere [How to: Create a Windows Application Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 Il debug di questo tipo di applicazione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è simile a quello delle applicazioni Windows Form gestite.

 Quando si crea un progetto di Windows Form mediante il modello di progetto, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono definite automaticamente le impostazioni necessarie per le configurazioni di debug e di rilascio. Se necessario, è possibile modificare queste impostazioni nella finestra di dialogo **Pagine delle proprietà di \<nomeprogetto>** . Per altre informazioni, vedere [Configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md).

 Per altre informazioni, vedere [impostazioni di progetto per C++ una configurazione di debug](../debugger/project-settings-for-a-cpp-debug-configuration.md).

 Per eseguire il debug di un'applicazione Windows Form è anche possibile avviare l'applicazione all'esterno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e stabilire una connessione. Per ulteriori informazioni, vedere [Connessione a uno o più programmi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

 [In questo argomento](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>Vedere anche
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Connessione a uno o più programmi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Configurazioni versioni di debug e di rilascio](../debugger/how-to-set-debug-and-release-configurations.md)
- [Procedura: Creare un progetto Applicazione Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))
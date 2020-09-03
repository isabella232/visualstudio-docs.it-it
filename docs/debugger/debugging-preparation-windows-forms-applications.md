---
title: Preparare il debug di app Windows Forms | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9e98411a009ea4345b567cbc38e6cf94c037323
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916400"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Preparazione al debug: applicazioni Windows Form
Il modello di progetto Windows Forms consente di creare un'applicazione Windows Forms. Il debug di questo tipo di applicazione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è una procedura molto semplice. Per ulteriori informazioni, vedere [creazione di un progetto di applicazione Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 Quando si crea un progetto di Windows Form mediante il modello di progetto, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono definite automaticamente le impostazioni necessarie per le configurazioni di debug e di rilascio. Se necessario, è possibile modificare tali impostazioni. Queste impostazioni possono essere modificate nella finestra di dialogo ** \<project name> pagine delle proprietà** (**progetto** in Visual Basic).

 Per ulteriori informazioni, vedere [impostazioni delle proprietà consigliate](../debugger/managed-debugging-recommended-property-settings.md).

 Nella tabella riportata di seguito è indicata un'impostazione consigliata aggiuntiva per le proprietà.

### <a name="configuration-properties-in-debug-tab"></a>Proprietà di configurazione disponibili nella scheda Debug

|**Nome proprietà**|**Impostazione**|
|-----------------------|-----------------|
|**Azione di avvio**|Nella maggior parte dei casi, impostare questa proprietà su **Avvia progetto**. Impostare questa proprietà su **Avvia programma esterno** se si vuole avviare un altro eseguibile quando si inizia il debug (in genere per il debug di DLL).|

 È possibile eseguire il debug di applicazioni Windows Forms dall'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oppure stabilendo una connessione a un'applicazione già in esecuzione. Per ulteriori informazioni sul fissaggio, vedere [Connetti a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Per eseguire il debug di Windows Forms Application in C#, F# o Visual Basic

1. Aprire il progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

2. Creare i punti di interruzione necessari.

    Poiché le applicazioni Windows Forms sono guidate da eventi, i punti di interruzione dovranno essere inseriti nel codice del gestore eventi o nei metodi chiamati dal codice del gestore eventi. Alcuni eventi tipici in cui impostare i punti di interruzione sono:

   1. Eventi associati a un controllo, ad esempio Click, Enter e così via

   2. Eventi associati all'avvio e alla chiusura dell'applicazione, ad esempio Load, Activated e così via

   3. Eventi di convalida e relativi allo stato attivo.

      Per altre informazioni, vedere [Creazione di gestori eventi in Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).

3. Scegliere **Avvia** dal menu **Debug**.

4. Eseguire il debug usando le tecniche descritte in [prima occhiata al debugger](../debugger/debugger-feature-tour.md).

## <a name="see-also"></a>Vedere anche
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
- [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Procedura: impostare le configurazioni di debug e di rilascio](../debugger/how-to-set-debug-and-release-configurations.md)
- [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)
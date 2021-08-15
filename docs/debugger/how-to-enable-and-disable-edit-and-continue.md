---
title: Abilitare e disabilitare Modifica e continuazione | Microsoft Docs
description: Informazioni su come disabilitare e abilitare Modifica e continuazione nelle opzioni Visual Studio in fase di progettazione. La funzionalità Modifica e continuazione può essere utilizzata solo nelle build di debug.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 8e01926f5ec245fe611e72f9f15b8da780d9423e38e568e2992869ebd9a55db1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379282"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Procedura: Abilitare e disabilitare Modifica e continuazione (C#, VB, C++)

È possibile disabilitare o abilitare **Modifica e continuazione** nella finestra Visual Studio **opzioni** in fase di progettazione. La funzionalità **Modifica e continuazione** può essere usata solo nelle build di debug. Per altre informazioni, vedere [Modifica e continuazione](../debugger/edit-and-continue.md).

Per C++ nativo, **Modifica e continuazione** richiede l'uso dell'opzione `/INCREMENTAL` . Per altre informazioni sui requisiti delle funzionalità in C++, vedere questo post di [blog](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) e Modifica e continuazione [(C++).](../debugger/edit-and-continue-visual-cpp.md)

**Per abilitare o disabilitare Modifica e continuazione:**

1. Se si è in una sessione di debug, arrestare il debug (**Debug**  >  **Arresta debug** o **MAIUSC** + **F5**).

1. In **Strumenti** Opzioni > (o Opzioni di debug ) > Debug generale , selezionare Modifica e  >   continuazione nel   >     >  riquadro destro. 

    > [!NOTE]
    > Se IntelliTrace è abilitato e si raccolgono sia eventi IntelliTrace sia informazioni sulle chiamate, la funzionalità Modifica e continuazione viene disabilitata. Per altre informazioni, vedere [IntelliTrace.](../debugger/intellitrace.md)

1. Per il codice C++, assicurarsi che **l'opzione Abilita** Modifica e continuazione nativa sia selezionata e impostare le opzioni aggiuntive:
    - **Applica modifiche alla continuazione (solo nativo)**

      Se selezionata, Visual Studio compila e applica automaticamente le modifiche al codice quando si continua il debug da uno stato di interruzione. In caso contrario, è possibile scegliere di applicare le modifiche usando **Debug**  >  **Applica modifiche al codice**.

    - **Avvisa del codice non obsoleto (solo nativo)**

      Se l'opzione è selezionata, genera avvisi sul codice non obsoleto.

1. Fare clic su **OK**.

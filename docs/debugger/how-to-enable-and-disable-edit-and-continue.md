---
title: Abilitare e disabilitare modifica e continuazione | Microsoft Docs
description: Informazioni su come disabilitare e abilitare modifica e continuazione nelle opzioni di Visual Studio in fase di progettazione. La funzionalità Modifica e continuazione può essere utilizzata solo nelle build di debug.
ms.custom: SEO-VS-2020, seodec18
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
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 02356a407acc97b60f05641359c32305323f162e
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903532"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Procedura: abilitare e disabilitare modifica e continuazione (C#, VB, C++)

È possibile disabilitare o abilitare **modifica e continuazione** nella finestra di dialogo **Opzioni** di Visual Studio in fase di progettazione. La funzionalità **Modifica e continuazione** può essere usata solo nelle build di debug. Per altre informazioni, vedere [Modifica e continuazione](../debugger/edit-and-continue.md).

Per il linguaggio C++ nativo, per **modifica e continuazione** è necessario usare l' `/INCREMENTAL` opzione. Per ulteriori informazioni sui requisiti di funzionalità in C++, vedere questo [post di Blog](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) e [modificare e continuare (C++)](../debugger/edit-and-continue-visual-cpp.md).

**Per abilitare o disabilitare modifica e continuazione:**

1. Se ci si trova in una sessione di debug, arrestare il debug (**debug**  >  **Interrompi debug** o **MAIUSC** + **F5**).

1. In **strumenti**  >  **Opzioni** > (o   >  **Opzioni** di debug) > **debug**  >  **generale**, selezionare **modifica e continua** nel riquadro destro.

    > [!NOTE]
    > Se IntelliTrace è abilitato e si raccolgono sia eventi IntelliTrace sia informazioni sulle chiamate, la funzionalità Modifica e continuazione viene disabilitata. Per ulteriori informazioni, vedere [IntelliTrace](../debugger/intellitrace.md).

1. Per il codice C++, assicurarsi che sia selezionata l'opzione **Abilita modifica e continuazione nativa** e impostare le opzioni aggiuntive:
    - **Applica le modifiche durante la continuazione (solo nativo)**

      Se questa opzione è selezionata, Visual Studio compila e applica automaticamente le modifiche del codice quando si continua il debug da uno stato di interruzioni. In caso contrario, è possibile scegliere di applicare le modifiche utilizzando **debug**  >  **Applica modifiche del codice**.

    - **Avvisa in caso di codice non aggiornato (solo nativo)**

      Se questa opzione è selezionata, fornisce avvisi sul codice non aggiornato.

1. Fare clic su **OK**.

---
title: 'Procedura: Abilitare e disabilitare Modifica e continuazione | Microsoft Docs'
ms.custom: seodec18
ms.date: 10/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 0b5fbc7ee0f2d85c72ccda75bc2e8531419d52e3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051387"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Procedura: Abilitare e disabilitare Modifica e continuazione (C#, VB, C++)

È possibile disabilitare o abilitare **modifica e continuazione** in Visual Studio **opzioni** finestra di dialogo in fase di progettazione. La funzionalità **Modifica e continuazione** può essere usata solo nelle build di debug. Per altre informazioni, vedere [Modifica e continuazione](../debugger/edit-and-continue.md). 
  
C++ nativo **modifica e continuazione** richiede l'uso di `/INCREMENTAL` opzione. Per altre informazioni sui requisiti di funzionalità in C++, vedere questo [post di blog](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/) e [modifica e continuazione (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).
  
**Per abilitare o disabilitare Modifica e continuazione:**  
  
1.  Se lavora in una sessione di debug, arrestare il debug (**Debug** > **Termina debug** oppure **MAIUSC**+**F5**) .

1.  Nella **degli strumenti** > **opzioni** > (o **Debug** > **opzioni**) > **debug**  >  **Generali**, selezionare **modifica e continuazione** nel riquadro di destra.  
  
    > [!NOTE]
    >  Se IntelliTrace è abilitato e si raccolgono sia eventi IntelliTrace sia informazioni sulle chiamate, la funzionalità Modifica e continuazione viene disabilitata. Per altre informazioni, vedere [IntelliTrace](../debugger/intellitrace.md).
    
1.  Per codice C++, assicurarsi che **abilitare Modifica e continuazione nativo** sia selezionato e impostare le opzioni aggiuntive:
    - **Applica le modifiche durante la continuazione (solo nativo)**  
      
      Se selezionata, Visual Studio viene compilato automaticamente e applica le modifiche al codice quando si continua il debug da uno stato di interruzione. In caso contrario, è possibile scegliere di applicare modifiche mediante **Debug** > **Applica modifiche del codice**.  
      
    - **Avvisa in caso di codice non aggiornato (solo nativo)**  
      
      Se selezionata, consente di avvisi relativi a codice non aggiornato. 
  
1.  Fare clic su **OK**.    

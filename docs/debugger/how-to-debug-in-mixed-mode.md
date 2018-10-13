---
title: 'Procedura: eseguire il Debug in modalità mista | Microsoft Docs'
ms.custom: ''
ms.date: 06/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a08cf3cf95073d06c1dfa350f2de86bf72837c5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182676"
---
# <a name="how-to-debug-in-mixed-mode"></a>Procedura: eseguire il Debug in modalità mista
Le procedure seguenti descrivono come abilitare il debug per codice gestito e nativo contemporaneamente, noto anche come in modalità mista di debug. Esistono due scenari di debug in modalità mista:  
  
- L'app che chiama una DLL è scritta in codice nativo e gestita la DLL. 
  
- L'app che chiama una DLL è scritta in codice gestito e la DLL è in codice nativo. Per un'esercitazione che illustra questo scenario in modo più dettagliato, vedere [eseguire il Debug di codice gestito e nativo](../debugger/how-to-debug-managed-and-native-code.md).
   
È possibile abilitare i debugger nativi e gestiti al progetto di app chiamante **proprietà** pagine. Le impostazioni variano tra le app native e gestite. 

Se non si ha accesso al progetto dell'app chiamante, è possibile eseguire il debug di DLL dal progetto di DLL. Modalità mista per eseguire il debug solo il progetto DLL non è necessario. Per altre informazioni, vedere [procedura: eseguire il Debug da un progetto di DLL](../debugger/how-to-debug-from-a-dll-project.md). 

> [!NOTE]
> Le finestre di dialogo e i comandi visualizzati potrebbero essere diversi da quelli di questo articolo, a seconda dell'edizione o delle impostazioni di Visual Studio. Per modificare le impostazioni, scegliere **degli strumenti** > **Importa / Esporta impostazioni**. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Abilitare il debug in modalità mista per un'app chiamante nativa  
  
1. Selezionare il progetto C++ in **Esplora soluzioni** e fare clic sui **delle proprietà** icona, premere **Alt**+**invio**, o pulsante destro del mouse e scegliere **proprietà**.
   
1. Nel  **\<progetto > pagine delle proprietà** della finestra, espandere **le proprietà di configurazione**e quindi selezionare **debug**.  
   
1. Impostare **tipo di Debugger** a **misto** oppure **automatico**.
   
1. Scegliere **OK**.
   
   ![Abilitare il debug in modalità mista](../debugger/media/dbg-mixed-mode-from-native.png "abilitare il debug in modalità mista")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Abilitare il debug in modalità mista per un'app gestita da chiamata  
  
1. Selezionare il progetto c# o Visual Basic **Esplora soluzioni** e selezionare il **delle proprietà** icona, premere **Alt**+**invio**, oppure fare doppio clic su e scegliere **delle proprietà**.
   
1. Selezionare il **Debug** scheda e quindi selezionare **Abilita debug codice nativo**.
   
1. Uso **File** > **Salva elementi selezionati** oppure **Ctrl + S** per salvare le modifiche.

   ![Abilita debug codice nativo](../debugger/media/dbg-mixed-mode-from-csharp.png "Abilita debug codice nativo")
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Eseguire il debug da un progetto DLL](../debugger/how-to-debug-from-a-dll-project.md)
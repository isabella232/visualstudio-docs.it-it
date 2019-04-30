---
title: 'Procedura: Ripristinare comandi nascosti del Debugger | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7766f83eef6205ce445ed892ffaf5861a0dcabbb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387547"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Procedura: Ripristinare i comandi nascosti del debugger
Quando si installa Visual Studio, viene chiesto di scegliere una serie di impostazioni IDE predefinite per il linguaggio di programmazione principale. Le impostazioni IDE predefinite per alcuni linguaggi possono nascondere determinati comandi del debugger.

 Se si desidera utilizzare una funzionalità del debugger nascosta dalle impostazioni IDE predefinite, è possibile aggiungere di nuovo il comando al menu come descritto nella procedura riportata di seguito.

### <a name="to-restore-hidden-debugger-commands"></a>Per ripristinare comandi nascosti del debugger

1. Dopo avere aperto un progetto, scegliere **Personalizza** dal menu **Strumenti**.

2. Nella finestra di dialogo **Personalizza** fare clic sulla scheda **Comandi**.

3. Nell'elenco a discesa **Barra dei menu** selezionare il menu **Debug** in cui si vuole includere il comando ripristinato.

4. Fare clic sul pulsante **Aggiungi comando**.

5. Nella casella **Aggiungi comando** selezionare il comando che si vuole aggiungere e fare clic su **OK**.

6. Ripetere il passaggio precedente per aggiungere un altro comando.

7. Dopo avere aggiunto tutti i comandi desiderati al menu, fare clic su **Chiudi**.

    > [!WARNING]
    > Alcune voci di menu vengono visualizzate solo quando nel debugger è attivata una particolare modalità, ad esempio la modalità di esecuzione o la modalità di interruzione. Le voci aggiunte potrebbero quindi non essere immediatamente visualizzate al termine di questa procedura.

## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Ripristino di comandi non disponibili nella finestra di dialogo Personalizza
 Alcuni comandi, in particolare quelli facenti parte di menu gerarchici, non possono essere ripristinati dalla finestra di dialogo **Personalizza**. Per ripristinare tali comandi, è necessario importare una nuova raccolta di impostazioni IDE.

#### <a name="to-import-new-ide-settings"></a>Per importare nuove impostazioni IDE

1. Scegliere **Importa/Esporta impostazioni** dal menu **Strumenti**.

2. Nella pagina **Importazione/Esportazione guidata delle impostazioni** fare clic su **Importa le impostazioni di ambiente selezionate** e quindi fare clic su **Avanti**.

3. Nella pagina **Salvare le impostazioni correnti** specificare se si desidera salvare le impostazioni personali correnti e quindi fare clic su **Avanti**.

4. Nella pagina **Scegliere una raccolta di impostazioni da importare** scegliere una raccolta di impostazioni di sviluppo contenente i comandi da usare nella cartella **Impostazioni predefinite**. In caso di dubbi sulla raccolta da scegliere, provare a selezionare **Impostazioni generali per lo sviluppo** o **Impostazioni di sviluppo di Visual C++**, che contengono la maggior parte dei comandi del debugger.

5. Scegliere **Avanti**.

6. Nella pagina **Scegliere le impostazioni da importare** assicurarsi che sia selezionata l'opzione **Debug** in **Opzioni**. Deselezionare le altre caselle di controllo, a meno che non si desideri importare anche tali impostazioni.

7. Scegliere **Fine**.

8. Nella pagina **Importazione completa** esaminare gli eventuali errori associati alla riconfigurazione delle impostazioni in **Dettagli**.

9. Fare clic su **Chiudi**.

## <a name="see-also"></a>Vedere anche
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
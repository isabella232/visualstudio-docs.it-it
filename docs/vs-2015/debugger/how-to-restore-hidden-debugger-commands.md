---
title: 'Procedura: ripristinare comandi nascosti del Debugger | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5edc195397b9652d790620b8281100cc7651a02d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802304"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Procedura: ripristinare comandi nascosti del debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si installa Visual Studio, viene chiesto di scegliere una serie di impostazioni IDE predefinite per il linguaggio di programmazione principale. Le impostazioni IDE predefinite per alcuni linguaggi possono nascondere determinati comandi del debugger.  
  
 Se si desidera utilizzare una funzionalità del debugger nascosta dalle impostazioni IDE predefinite, è possibile aggiungere di nuovo il comando al menu come descritto nella procedura riportata di seguito.  
  
### <a name="to-restore-hidden-debugger-commands"></a>Per ripristinare comandi nascosti del debugger  
  
1.  Con un progetto aperto, scegliere il **degli strumenti** menu, fare clic su **Personalizza**.  
  
2.  Nel **Personalizza** finestra di dialogo, fare clic sul **comandi** scheda.  
  
3.  Nel **barra dei Menu:** elenco a discesa, selezionare la **Debug** menu che si desidera includere il comando ripristinato.  
  
4.  Fare clic su di **comando Aggiungi...** immagini (...).  
  
5.  Nel **Aggiungi comando** , selezionare il comando che si desidera aggiungere, quindi scegliere **OK**.  
  
6.  Ripetere il passaggio precedente per aggiungere un altro comando.  
  
7.  Fare clic su **Chiudi** quando hanno completato l'aggiunta di comandi al menu di scelta.  
  
    > [!WARNING]
    >  Alcune voci di menu vengono visualizzate solo quando nel debugger è attivata una particolare modalità, ad esempio la modalità di esecuzione o la modalità di interruzione. Le voci aggiunte potrebbero quindi non essere immediatamente visualizzate al termine di questa procedura.  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Ripristino di comandi non disponibili nella finestra di dialogo Personalizza  
 Alcuni comandi, in particolare quelli facenti parte di menu gerarchici, non possono essere ripristinati dal **Personalizza** nella finestra di dialogo. Per ripristinare tali comandi, è necessario importare una nuova raccolta di impostazioni IDE.  
  
#### <a name="to-import-new-ide-settings"></a>Per importare nuove impostazioni IDE  
  
1.  Nel **degli strumenti** menu, fare clic su **Importa / Esporta impostazioni**.  
  
2.  Nel **l'importazione / esportazione guidata delle impostazioni** pagina, fare clic su **Importa le impostazioni di ambiente selezionate**e quindi fare clic su **Next**.  
  
3.  Nel **salvare le impostazioni correnti** pagina, decidere se salvare le impostazioni esistenti e quindi fare clic su **successivo**.  
  
4.  Nel **scegliere una raccolta di impostazioni da importare** nella pagina il **impostazioni predefinite** cartella, scegliere una raccolta di impostazioni di sviluppo che include i comandi da usare. Se non si conosce quale raccolta di scegliere, provare **impostazioni generali per lo sviluppo** oppure **delle impostazioni di sviluppo di Visual C++**, che forniscono più i comandi del debugger.  
  
5.  Scegliere **Avanti**.  
  
6.  Nel **scegliere le impostazioni da importare** nella pagina **opzioni**, verificare che **debug** sia selezionata. Deselezionare le altre caselle di controllo, a meno che non si desideri importare anche tali impostazioni.  
  
7.  Scegliere **Fine**.  
  
8.  Nel **importazione completa** pagina, esaminare gli eventuali errori associati alla riconfigurazione delle impostazioni in **dettagli**.  
  
9. Fare clic su **Chiudi**.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debugger Basics](../debugger/debugger-basics.md) (Nozioni di base sul debugger)




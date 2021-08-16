---
title: Eseguire il debug di ActiveX controllo | Microsoft Docs
description: Informazioni su come eseguire il debug di ActiveX controllo . È necessario specificare un eseguibile contenitore, che è possibile eseguire nelle pagine Project proprietà o quando si avvia il debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 12eec4742fb4c420e10637b212a1fa6bbc578b0d07d058296b931f4ce60a7015
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362328"
---
# <a name="how-to-debug-an-activex-control"></a>Procedura: eseguire il debug di un controllo ActiveX

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

Per effettuare il debug di un controllo ActiveX, è necessario specificare un contenitore (eseguibile) in cui elaborare il controllo stesso.

## <a name="to-specify-a-container-for-the-debug-session"></a>Per specificare un contenitore per la sessione di debug

1. In Esplora soluzioni selezionare il progetto.

2. Scegliere **Pagine** delle proprietà dal menu **Visualizza**.

3. Nella finestra di dialogo **Pagine delle proprietà del progetto** aprire la cartella **Proprietà di configurazione** e selezionare **Debug**.

4. Nella categoria **Debug** individuare la proprietà **Command**.

5. Specificare il percorso del contenitore. Ad esempio, C:\Programmi\Internet Explorer\IEXPLORE.EXE.

6. Se si specifica Internet Explorer come contenitore ed è attivata la modalità Active Desktop, digitare `/new` nella casella **Argomenti del comando**.

7. Fare clic su **OK**.

     Se non si specifica alcun contenitore nella finestra di dialogo **Project Property Pages** (Pagine delle proprietà del progetto), sarà possibile specificarlo all'avvio del debug. Quando si seleziona un comando per avviare il debug, viene visualizzata la finestra di dialogo [Eseguibile per la sessione di debug](../debugger/executable-for-debugging-session-dialog-box.md). Nella finestra di dialogo specificare il nome percorso del contenitore.

## <a name="see-also"></a>Vedi anche

- [ActiveX Controlli](/cpp/mfc/activex-controls)
- [Test di proprietà ed eventi con Test Container](/cpp/mfc/testing-properties-and-events-with-test-container)
- [Debug com e ActiveX](../debugger/com-and-activex-debugging.md)
- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
